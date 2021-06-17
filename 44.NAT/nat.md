## NAT - Network Address Translation

#### Private IPv4 Addresses (RFC 1918)

* IPv4 doesn't provide enough addresses for all devices that need an IP address in the modern world
* The long term solution is to switch to IPv6
* There are 3 main short term solutions:
    - 1. CIDR
    - 2. Private IPv4 Addresses
    - 3. NAT
* RFC 1918 specifies the following IPv4 ranges as private:
    * 10.0.0.0/8 (10.0.0.0 - 10.255.255.255)
    * 172.16.0.0/12 (172.16.0.0 - 172.31.255.255)
    * 192.168.0.0/16 (192.168.0.0 - 192.168.255.255)

* Private IP's cannot be used over the Internet 

#### NAT 

* Network Address Translation is used to modify the source and/or destination IP addresses of packets
* There are various reasons to use NAT, but the most common reason is to allow hosts with private IP addresses to communicate with other hosts over the Internet

###### Static NAT

- Static NAT involves statically configuring one-to-one mappings of private addresses to public addresses 
- An inside local IP address is mapped to an inside global IP address 
    - **Inside Local** = The IP address of the inside host, from the perspective of the local network - the IP actually configured on the inside host, usually a private address.
    - **Inside Global** = The IP of the inside host, from the perspective of the outside hosts - the IP address of the inside host after NAT, usually a public address

- **Static NAT** allows devices with private IP addresses to communicate over the Internet. However, because it requires a one-to-one IP address mapping, it does not help preserve addresses

###### Static NAT Configuration
```
R1(config)#int g0/1
R1(config-if)#ip nat inside

R1(config)#int g0/0
R1(config-if)#ip nat outside
R1(config)#exit 

R1(config)#ip nat inside source static 192.168.0.167 100.0.0.1
R1(config)#ip nat inside source static 192.168.0.168 100.0.0.2
R1(config)#exit

[confirm configuration using:]
R1#show ip nat translations
```

When using the show command two new terms appear:

- **Outside Local** = The IP address of the outside host, from the perspective of the local network 
- **Outside Global** = The IP address of the outside host, from the perspective of the outside network 

Unless *destination NAT* is used, these two addresses will be the same. (beyond scope of ccna)

**Inside/Outside** = Location of the **HOST**
**Local/Global**   = **Perspective**
