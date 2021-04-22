## ACL Overview

* An ACL identifies traffic based on characteristics of the packet such as source IP address, destination IP address and port number
* The router or switch can take an action based on the result of the ACL 
* ACL's are supported on both switches and routers

- The original use of ACLs was a security feature to decide if traffic should be allowed to pass through the router
- By default a router will allow all traffic to pass between its interfaces
- When ACLs are applied the router identifies traffic and then decides if it will be allowed or not 

* ACLs are now also used in other software policies when traffic has to be identified, for example:
    - Identify traffic to give better service to in a QoS policy
    - Identify traffic to translate to a different IP address in a NAT

#### ACE - Access Control Entries
- ACLs are made up of ACE, access control entries, which are a series of deny/permit rules
- Each ACE is written on a seperate line

## Standard, Extended and Named ACLs
ace example:
```
access-list 100 deny tcp 10.10.30.0 0.0.0.255 gt 49151 10.10.20.1 0.0.0.0 eq 23
```
#### Standard vs Extended ACLs:
```
#access-list ?
<1-99>      ip standard access-list
<100-199>   ip extended access-list
<1300-1999> ip standard access-list (expanded range)
<2000-2699> ip extended access-list (expanded range)
```

- Standard ACLs reference the source address only
- Extended ACLs check based on the protocol, source address and port number

**STANDARD ACL RANGE = 1 - 99**
**EXTENDED ACL RANGE = 100 - 199**
**EXPANDED 100-199, 1999-2699**

STANDARD ACL EXAMPLE: ```#access-list 1 deny 10.10.10.10 0.0.0.0```
 
* The default wildcard mask is 0.0.0.0, meaning it matches an individual host address
* The wildcard mask should not be forgotten when specifying an IP subnet

EXTENDED ACL EXAMPLE:
```
#access-list 100 deny tcp 10.10.10.10 0.0.0.0 gt 49151 10.10.50.10 0.0.0.0 eq 23
```

Extended ACLs allow for much more information to be entered, there is no standard wildcard mask for extended ACLs

#### ACL Improvements
- It is now possible to reference ACLs by number or by name 
- Named ACLs begin with the command: ```ip access-list``` instead of just ```access-list``
 
```
#ip access-list ?

    extended
    standard
```

```
#ip access-list [standard | extended] list_name
```
This creates the list and moves into the ACL config menu:
```
R1(config-std-nacl)#deny 10.01.10.01 0.0.0.0
R1(config-std-nacl)#permit 10.10.10.0 0.0.0.255
```

## ACL SYNTAX

```R1(config)#access-list 100 ?
    deny        reject
    permit      forward
    remark      comment
```

It is recommended to add comments to entries so if the ACL grows rule meanings can be found more easily. 
After this command ```access-list [permit | deny]``` comes the protocol. There are many that can be put into the command

- Use TCP or UDP if you want the ACE to apply to traffic for a particular application between a source and destination address 

- Use IP if you want the ACE to apply to all traffic between a source and destination address

The next keyword is the ACL source:
```
#access-list 100 permit tcp ?
    A.B.C.D - source address
    any     - any source host
    host    - a single source host
```

Followed by the Port Source number, specifying the source port is optional, it defaults to any port. 
The destination IP is next and followed by some final options.
 
#### Verifying ACLs
```
#show access-lists 100
```

The log keyword is used to log to the console or external monitoring server

## ACL OPERATIONS

#### Access Groups
* ACLs are applied at the interface level with the Access-Group command
* ACLs can be applied on the inbound or outbound direction
* You can have a maximum of one ACL per interface per direction
* You can have both an inbound and an outbound ACL on the same interface, but not 2 inbound or outbound ACLs
* An interface can have no ACL applied, an inbound only, an outbound only or ACLs in both directions

#### Access Group Configuration
```
#interface g0/1
#ip access-group 100 out 
#ip access-group 101 in 
```

####  Verification
```
#show ip interface f1/0 | include access list 
```

'not set' error if ACL is not applied, pipe the command for less information 

#### Access Control Entry Order
- The ACL is read by the router from top to bottom
- As soon as a rule matches the packet, the permit or deny action is applied and the ACL is not processed any further
- The order of rules is important

**ACL examples:**
This will deny 10.10.10.10 but permit the rest of the 10.10.10.0/24 subnet
```
#access-list 1 deny host 10.10.10.10
#access-list 1 permit 10.10.10.0 0.0.0.255
```
Below will permit all of the 10.10.10.0/24 subnet including 10.10.10.10
```
#access-list 1 permit 10.10.10.0 0.0.0.255
#access-list 1 deny host 10.10.10.10
```

#### Injecting ACEs in an Existing ACL

- ACEs are automatically numbered in increments of 10, the reason for this is that it allows space later on if new entries need to be added
- Support for injecting ACEs in an existing ACL started in Named ACLs but is also supported in Numbered ACLs now

#### Implicit Deny All 

* There is an implicit 'deny any any' rule at the bottom of ACLs 
* If an ACL is not applied to an interface, all traffic is allowed
* If an ACL is applied, all traffic is denied except what is explicitly allowed


* Traffic from 10.10.10.0/24 will be permitted, everything else is denied
* ```#access-list 1 permit 10.10.10.0 0.0.0.255``

Implicit deny is always there. 

- Many organisations include an explicit deny all at the end of ACLs to log illegal traffic- Also explicit is better than implicit.
```
#access-list 1 permit 10.10.10.0 0.0.0.255
#access-list 1 deny any log
```

Makes it possible to send information out to a server for example

#### Explicit Permit All

* If an ACL is applied, all traffic is denied except what is explicitly allowed
* If you want to reverse that, add a permit statement at the end of the ACL

* Traffic from 10.10.10.0/24 is denied, everything else is permitted
```
#access-list 1 deny 10.10.10.0 0.0.0.255
#access-list 1 permit any 
```
  
#### Traffic Sourced from Router 

- ACLs applied to an interface do not apply to traffic which originates from the router itself

















