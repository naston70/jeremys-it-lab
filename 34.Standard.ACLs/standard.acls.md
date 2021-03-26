## Standard ACLs -  Access Control Lists

#### ACLs from a security viewpoint

- ACLs function as a packet filter, instructing the router to permit or discard specific traffic
- ACLs can filter traffic based on source / destination IP addresses, source / destination Layer 4 ports, etc

There must be a requirement -  such as 'Hosts in 192.168.2.0/24 cannot access 10.0.2.0/24 network'
* ACLs are configured globally on the router (global config mode)
* They are an ordered sequence of ACEs (Access Control Entries)

- Configuring an ACL in global config mode will not make the ACL take effect
- The ACL must be applied to an interface
- ACLs are applied either inbound or outbound
- ACLs are made up of one or more ACEs
- When the router checks a packet against the ACL, it processes the ACEs in order from top to bottom
- If the packet matches one of the ACEs in the ACL, the router takes the action and stops processing the ACL. All entries below the matching entry will be ignored
- Maximum if one inbound and one outbound ACL per interface

#### Implicit Deny

What happens if a packet doesn't match any entries in an ACL? 

By default the router will drop the packet, be aware when configuring an ACL

## ACL Types:

**Standard ACLs:** Match based on Source IP address only
    * -> Standard Numbered ACLs
    * -> Standard Named ACLs

**Extended ACLs:** Match Source/Destination IP, Source/Destination port, etc
    * -> Extended Numbered ACLs
    * -> Extended Named ACLs

###### Standard Numbered ACLs

- Standard ACLs match traffic based only on the source IP address of the packet
- Numbered ACLs are identified with a number (ie ACL 1, ACL 2, ACL 3, etc)
- Different types of ACLs have a different range of numbers that can be used
    * Standard ACLs can use 1-99 and 1300 - 1999

- Basic command to configure a standard numbered ACL is:
- R1(config)# access-list number {deny|permit} ip wildcard-mask 

- To apply the access list to an interface:
```
R1(config-if)#ip access-group number {in|out}
```

Config example:

Requirements
    - 192.168.1.1 can access 192.168.2.0/24
    - other IPs in 192.168.1.0/24 cant access 192.168.2.0/24

Creation of the ACL and ACEs
```
R1(config)#access-list 1 permit 192.168.1.1
R1(config)#access-list 1 deny 192.168.1.0 0.0.0.255
R1(config)#access-list 1 permit any
```
Applying the ACL to an interface
```
R1(config)#int g0/1
R1(config-if)#ip access-group 1 out
```

**Standard ACLs should be applied as close as possible to the destination**


#### Standard Named ACLs

* Standard ACLs match traffic based only on the source IP address of the packet
* Named ACLs are identified with a name 
* Standard named ACLs are configured by entering 'standard named ACL config mode' and then configuring each entry within that config mode
* ```R1(config)#ip access-list acl-name```
* ```R1(config-std-nacl)#[entry-number] {deny|permit} ip wildcard-mask``

Verify a configuration using:
```
#show access-lists
```
```
#show running-config | section access-list
```




