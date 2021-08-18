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


