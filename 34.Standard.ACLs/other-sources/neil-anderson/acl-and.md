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















