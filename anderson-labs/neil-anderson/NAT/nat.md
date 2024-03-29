## NAT - Network Address Translation

- An organisation can use private IP addresses on their inside network but still grant their hosts Internet access by translating them to their outside public IP addresses
- Many hosts on the inside can share a few or a single public IP address on the outside

#### Static NAT

- **Static NAT** - permanent one to one mapping usually between a public and private IP address. Used for servers which must accept incoming connections

- **Dynamic NAT** - uses a pool of public addresses which are given out on an as needed first come first served basis. Usually used for internal hosts which need to connect to the Internet but do not accept incoming connections

- **PAT (Port Address Translation)** - allows the same public IP to be reused

#### Static Nat Scenario

- Bought range 203.0.113.0/28 from service provider
- 203.0.113.2 is used on the outside interface on the Internet edge router R1
- 203.0.113.1 is used as the default gateway address. 
- 203.0.113.3 - 203.0.113.14 remain available

- Int-S1 at 10.0.1.10 is an internal web server which needs to accept incoming connections from the Internet
- A fixed public IP address is needed to accept incoming connections, we use 203.0.113.3
- A static NAT translation is required to translate the public IP address 203.0.113.3 on f0/0 to 10.0.1.10 on f1/0 for incoming connections
- The translation is bidirectional so will also translate 10.0.1.10 to 203.0.113.3 for outbound traffic from the server 

#### Static NAT Configuration
```
#int f0/0
#ip nat outside

#int f0/1
#ip nat inside

#ip nat inside source static 10.0.1.10 203.0.113.3
```

To verify the NAT is working, send some traffic from the device using NAT and use the command:
```
#show ip nat translation
```

#### NAT Translations Inside Local, Inside Global, Outside Local Outside Global

* Inside Local: The IP address actually configured on the inside hosts Operating System
* Inside Global Address: The NAT'd address of the inside host as it will be reached by the outside network 
* Outside Local: The IP address of the outside host as it appears to the inside network 
* Outside Global Address: The IP address assigned to the host on the outside network by the hosts owner

#### Outside Local vs Outside Global
- R1 in the lab scenario knows one address to reach the outside host 203.0.113.20 and does not translate that address
- For one way NAT, the Outside Local and Outside Global addresses will be reported as being the same 

## Static NAT lab demo
configuring an internal server with private ip using static nat 
```
[on router ]
#int f0/0
#ip nat inside 
#int f0/1 
#ip nat outside 
#exit
#ip nat inside source static 10.0.1.0 203.0.113.3
```

#### Dynamic NAT

- Hosts in th 10.0.2.0/24 network do not accept incoming connections so they dont need a fixed public IP address with a static NAT translation
- They do not need outbound connectivity to the Internet so need to be translated to a public IP address
- 203.0.113.4 - .14 will be used as the pool
- The inside hosts will be translated to the public IP addresses on a first come first served basis when they send traffic out
- The first host to send traffic out will be translated to 203.0.113.4, the second to .5, up to 14 at the end of the pool

* With standard dynamic NAT you need a public IP address for every host which needs to communicate with the outside
* If you have 30 hosts, you need 30 public IP addresses
* When all the addresses in the pool have been used, new outbound connections from other inside hosts will fail because there will be no addresses left to translate them to
* The hosts would have to wait for an existing connection to be torn down and the translations to be released back into the pool when they time out
[not typically used in real world due to this limitation]

#### Dynamic NAT Configuration 
```
#int f0/0
#ip nat outside
#int f2/0
#ip nat inside 
```
Configure the pool of global addresses:
```
#ip nat pool Dobby 203.0.113.4 203.0.113.14 netmask 255.255.255.240
```
Create an access list which references the internal IP addresses we want to translate:
```
#access-list 1 permit 10.0.2.0 0.0.0.255
```
Associate the access list with the NAT pool to complete the configuration:
```
#ip nat inside source list 1 pool Dobby
```

#### clear ip nat translation 

- ```clear ip nat translation``` can be used to remove translations from the translation table
- This can be useful for troubleshooting
- It is also often required if you want to edit your NAT configuration - the router will not allow changes when there are active connections
- ```clear ip nat translation *``` will remove all dynamic translations 

## Dynamic NAT lab demo
Allow the PCs out to the internet, using a dynamic nat

First add the interface being used as the inside nat:
```
#int f2/0
#ip nat inside
#exit
#ip nat pool Dobby 203.0.113.4 203.0.113.14 netmask 255.255.255.240
#ip access-list 1 permit 10.0.2.0 0.0.0.255
#ip nat inside source list 1 pool Dobby
#
```

#### Port Address Translation 
Solves the issue with dynamic NAT using IP addresses up.

- PAT is an extension to NAT that permits multiple devices to be mapped to a single public IP address
- With PAT you do not need a public IP address for every inside host 
- The router tracks translations by IP address and Layer 4 port number
- Because different inside hosts are assigned different port numbers, the router knows which host to send return traffic to, even when the public address is the same

#### Dynamic NAT with Overload

* Dynamic NAT with Overload uses PAT to allow more clients to be translated than IP addresses are available in the NAT pool
* If the NAT pool is 203.0.113.4 - .6 for example, the first 2 hosts which initiate outbound connections will be translated to .4 and .5
* The 3rd host will be translated to .6 and the router will track which source port number was used in the translation table
* The 4th and 5th etc hosts will also be translated to .6 but with different source port numbers
* When the return traffic is sent back the router checks the destination port number to see which host to forward it to

To add overload functionality the ```overload``` keyword needs to be added to the end of command associating the access-list with the NAT pool from the Dynamic NAT configuration
```
#ip nat inside source list 1 pool Dobby overload
```

#### PAT with a single IP address
- The last NAT scenario to cover is a small office which has not purchased a range of public IP addresses
- In this case the outside interface will most likely get its IP address via DHCP from the service provider
- PAT can be used to allow multiple inside hosts to share the single outside public IP address 
* The configuration is similar to Dynamic NAT with overload but translates to the outside interface address rather than a pool of addresses
* You must translate to the outside interface rather than a specific IP address because a DHCP address can change 

```
#int f0/0
#ip address dhcp 
#ip nat outside 

#int f1/0
#ip nat inside 

#access-list 1 permit 10.0.2.0 0.0.0.255
#ip nat inside source list 1 interface f0/0 overload
```

Mapping to the interface rather than a pool as before, verify using ```show ip nat translation```

## PAT Lab demo
small office scenario, public ip on outside interface from dhcp which can change:

```
#int f0/0
#ip nat outside
#int f2/0
#ip nat inside 
#exit

#access-list 1 permit 10.0.2.0 0.0.0.255
#ip nat inside source list 1 interface f0/0 overload
```

Use debug on router to confirm addresses using NAT 






