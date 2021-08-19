## ACL Implementation

Exam Topics

- Configure and verify access control lists

#### Configuring Standard Numbered IPv4 ACLS

Standard IPv4 ACLs, which are numbered ACLs 1-99 and 1300-1999 or are named ACLs, filter packets based on source address and mask. They permit or deny the entire TCP/IP protocol suite. Configuring an ACL requires two steps:

1. Create the ACL
2. Apply the ACL 

#### Standard Numbered IPv4 ACL: Permit Specific Network

Create an ACL to prevent traffic that is not part of the internal networks (172.16.0.0/16) from traveling out of the Gigabit Ethernet interfaces:

1. Create the ACL. Use the ```access-list``` global configuration command to create an entry in a standard IPv4 ACL 
```
R1(config)# access-list 1 permit 172.16.0.0 0.0.255.255
```

This statement matches any addresses that start with 172.16. The ```remark``` command allows to add a description of the ACL

2. Apply the ACL. Use the interface configuration command to select an interface to which to apply the ACL. Then use the ```ip access-group```interface configuration command to activate the existing ACL on an interface for a specific direction
```
R1(config)# interface gigabitethernet 0/0 
R1(config-if)# ip access-group 1 out
R1(config-if)# interface gigabitethernet 0/1
R1(config-if)# ip access-group 1 out
```

This step activates the standard IPv4 ACL 1 on both the interfaces as an outbound filter.

This ACL allows only traffic from source network 172.16.0.0 to be forwarded out on G0/0 and G0/1. Traffic from networks other than 172.16.0.0 is blocked with the implied deny any

#### Standard Numbered IPv4 ACL: Deny a Specific Host

Create an ACL to prevent traffic that originates from host 172.16.4.13 from traveling out G0/0. Create and apply the ACL.
```
R1(config)# access-list 1 deny 172.16.4.13 0.0.0.0
R1(config)# access-list 1 permit 0.0.0.0 255.255.255.255
R1(config)# interface gigabitethernet 0/0
R1(config-if)# ip access-group 1 out 
```
This ACL is designed to block traffic from a specific address, 172.16.4.13, and to allow all other traffic to be forwarded on G0/0.
The second statement can be rewritten as ```access-list 1 permit any```

#### Standard Numbered IPv4 ACL: Deny a Specific Subnet

Create an ACL to prevent traffic that originates from the 172.16.4.0/24 from traveling out the G0/0 interface:
```
R1(config)# access-list 1 deny 172.16.4.0 0.0.0.255
R1(config)# access-list 1 permit any
R1(config)# interface g0/0
R1(config-if)# ip access-group 1 out 
```

This ACL is designed to block traffic from a specific subnet and allow all other traffic to be forwarded out.

#### Standard Numbered IPv4 ACL: Deny Telnet or SSH Access to the Router

For traffic into and out of the router, filter Telnet or SSH access to the router by applying an ACL to the vty ports. Restricting vty access is primarily a technique for increasing network security and defining which addresses are allowed Telnet access to the router EXEC process. 
```
R1(config)# access-list 12 permit host 172.16.4.13
R1(config)# line vty 0 15
R1(config-line)# access-list 12 in 
```

#### Configuring Extended Numbered IPv4 ACLs 

For more precise traffic filtering control, use extended IPv4 ACLs. Extended IPv4 ACLs can be numbered 100-199 and 2000-2699. Extended ACLs check for source and destination IP addresses. In addition, at the end of the extended ACL statement, you can specify the protocol and optional TCP or UDP application to filter more precisely. To configure numbered extended IPv4 ACLs on a Cisco router, create an extended IP ACL and activate that ACL on an interface.

#### Command parameters for a numbered extended IPv4 ACL

- access-list-number: identifies the list using a number in range 100-199 or 2000-2699
- permit|deny: indicated whether to block or deny specified address 
- protocol: if **ip** is specified, the entire TCP/IP protocol suite is filtered. includes TCP, UDP, ICMP etc 
- source and destination: source and destination of the IP addresses
- src and dst wildcard: wildcard mask 
- operator: can be lt (less than), gt (greater than), or neq. 
- established: for inbound TCP only, Allows TCP traffic to pass if the packet is a response to an outbound initiated session. This type of traffic has the ACK bits set. 
- log: sends a logging message to the console

#### Extended Numbered IPv4 ACL: Deny FTP from Subnets

create an ACL to prevent FTP traffic originating from the subnet 172.16.4.0/24 and going to 172.16.3.0/24 subnet from traveling out G0/0. Create and apply.

###### Access List Preventing FTP Traffic from Specific Subnets 
```
R1(config)# access-list 101 deny tcp 172.16.4.0 0.0.0.255 172.16.3.0 0.0.0.255 eq 21
R1(config)# access-list 101 deny tcp 172.16.4.0 0.0.0.255 172.16.3.0 0.0.0.255 eq 20
R1(config)# access-list 101 permit ip any any 
R1(config)# interface g0/0
R1(config-if)# ip access-group 101 out 
```

The deny statements block FTP traffic originating from subnet 172.16.4.0 to subnet 172.16.3.0. The permit statement allows all other IP traffic out interface G0/0. Two statements must be entered for the FTP application because port 21 is used to establish, maintain and terminate an FTP session, while port 20 is used for the actual file transfer task.

#### Extended Numbered IPv4 ACL: Deny Only Telnet from Subnet 

Create an ACL to prevent Telnet traffic that originates from the subnet 172.16.4.0/24 from traveling out interface G0/0
```
R1(config)# access-list deny 172.16.4.0 0.0.0.255 any eq 23
R1(config)# access-list 101 permit ip any any 
R1(config)# interface g0/0
R1(config)# ip access-group 101 out 
```

#### Configuring Named IPv4 ACLs 

With a named ACL, you can identify standard and extended ACLs with an alphanumeric string instead of the numeric. Because you can modify an ACL without having to delete and then reconfigure the entire ACl. With IOS 12.3 you can insert individual entries using an appropriate sequence number.

#### Standard Named IPv4 ACL Steps and Syntax

The following steps and syntax are used to create a standard named ACL:
1. Name the ACL. ```ip access-list standard [name]```
2. Create the ACL. From standard named ACL configuration mode, use ```permit``` or ```deny``` statements to specify one or more conditions for determining whether a packet is forwarded or dropped.
```
R1(config-std-nacl)# [sequence-number]{permit|deny} source source-wildcard
```

If a sequence number is not specified, Cisco IOS increments by 10 for every statement

3. Apply the ACL. Activate the named ACL on an interface with the ```ip access-group name``` command
```
R1(config-if)# ip access-group [name] [in|out]
```

#### Standard Named IPv4 ACL: Deny a Single Host from a Given Subnet 
Create a standard ACL named TROUBLEMAKER to prevent traffic that originates from host 172.16.4.13 from traveling out interface G0/0.
```
R1(config)# ip access-list standard TROUBLEMAKER
R1(config-std-nacl)# deny host 172.16.4.13
R1(config-std-nacl)# permit 172.16.4.0 0.0.0.255

R1(config-std-nacl)# interface G0/0
R1(config-if# ip access-group TROUBLEMAKER out
```

#### Extended Named IPv4 ACL Steps and Syntax
1. Name the ACL, ```ip access-list extended [name]```
2. Create the ACL. From extended named ACL configuration mode, use ```permit``` or ```deny``` statements to specify one or more conditions for determining whether a packet is forwarded or dropped.
```
R1(config-ext-nacl)# [sequence-number] {deny|permit} protocol source source-wildcard [operator-port] destination destination-wildcard [operator-port] [established|log]
```

3. Apply the ACL. Activate the named ACL on the interface: ```ip access-group name [in | out]``` 

#### Adding Comments to Named or Numbered IPv4 ACLs

You can add comments to ACLs by using the ```remark``` argument in place of the permit or deny. Remarks are descriptive statement that you can use to better understand and troubleshoot either named or numbered ACLs. Extended

## Verifying IPv4 ACLs 

When you finish configuring an ACL, use the ```show``` commands to verify the configuration. Use the ```show access-lists``` command to display the contents of all ACLs. By entering the ACL name or number as an option for this command you can specify a specific ACL on

An access list can also be verified on a specific interface: ```show ip interface g0/0``` will show what access list is set.

## Comparing IPv4 and IPv6 ACLs 

| Feature                                | IPv4 only | IPv6 only | Both |
|----------------------------------------|-----------|-----------|------|
|                                        |           |           |      |
| match src and/or dst                   |           |           | X    |
| Applied directionally on an interface  |           |           | X    |
| Match TCP or UDP src and/or dst ports  |           |           | X    |
| Match ICMP codes                       |           |           | X    |
| Includes implicit deny                 |           |           | X    |
| Match IPv4 only                        | X         |           |      |
| Match IPv6 only                        |           | X         |      |
| Use numbers to identify ACL            | X         |           |      |
| Use names to identify the ACL          |           |           | X    |
| Include some implicit permit statement |           | X         |      |
|                                        |           |           |      |


The basic steps to configure an IPv6 ACL are:

1. Name the ACL
2. Create the ACL 
3. Apply the ACL 

###### Step 1: Name the IPv6 ACLs

To name an IPv6 ACL, enter the ```ipv6 access-list```command in global configuration mode.
```ipv6 access-list name
```

The command syntax to name an IPv6 ACL is the same whether configuring standard or extended IPv6 ACLs. 

###### Step 2: Create the IPv6 ACL 

A standard IPv6 ACL includes both source and destination address information, but it does not include TCP, UDP or ICMPv6 information. The syntax for a standard IPv6 ACL follows:
```
R1(config-ipv6-acl)# [permit|deny] ipv6 {source-ipv6-prefix/prefix-length | any | host source-ipv6-address} {destination-ipv6-prefix/prefix-length | any | host destination-ipv6-address} [log]
```

Extended IPv6 ACLs match on many more IPv6 packet header fields, as well as TCP, UDP and ICMPv6 messages and IPv6 extension headers. 

###### Step 3: Apply the IPv6 ACL 
The syntax to apply an IPv6 ACL to an interface follows:
```
R1(config-if)# ipv6 traffic-filter name {in|out}
```

#### Standard IPv6 ACL: Allow SSH remote access
```
R1(config)# ipv6 access-list SSH-HOST
R1(config-ipv6-acl)# permit ipv6 host 2001:db8:1:4::13 any 
R1(config-ipv6-acl)# deny ipv6 any any 
R1(config-ipv6-acl)# exit
R1(config)# line vty 0 4
R1(config-line)# ipv6 access-class SSH-HOST in 
```

The ```permit``` statement allows only one host. ALl other ipv6 traffic is denied. The ACL is then applied to the first 5 vty lines with the ipv6 access-class command.

## Verifying IPv6 ACLs 

As with IPv4 ACLs, the configuration and application of IPv6 ACLs can be viewed with ```show run```. However, production routers configuration is usually long and complex, therefore it can be quicker to use verification commands to be more precise and efficient.

For example, ```show access-lists``` reveals all IPv4 and IPv6 ACLs configured on the device.
Cisco IOS added sequence numbers to the end of the IPv6 ACLs instead of at the beginning, as it does for IPv4 ACLs. 

To verify the placement of an IPv6 ACL on an interface, ```show ipv6 interface``` command is used. If an ACL is applied , the output will have a line entry such as ```Inbound access list WEB-ONLY``` 


#### Troubleshooting ACLs 

A network can be configured correctly, with all hosts receiving DHCP addressing fully populated routing tables, and a fully operating physical layer but an ACL somewhere in the data path can still cause a problem. Troubleshooting a problem caused by an ACL can make the job more difficult