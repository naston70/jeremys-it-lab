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

With a named ACL, you can identify standard and extended ACLs with an alpha

