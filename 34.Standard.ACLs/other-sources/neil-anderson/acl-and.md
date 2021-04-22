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



