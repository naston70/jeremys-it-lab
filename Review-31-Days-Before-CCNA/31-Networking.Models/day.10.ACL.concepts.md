## ACL Concepts

Exam Topics

- Configure and verify ACLs

#### ACL Operation

A routers default operation is to forward all packets, as long as a route for the packet exists and the link is up. ACLs can help implement a basic level of security. However, they are not the only security solution a large organization should implement. In fact ACLs increase latency of router. If the organization is very large, with routers managing traffic of hundreds or thousands of users, the administrator will likely use a combination of other security implementations, beyond CCNA.


#### Defining an ACL

An ACL is a router configuration script that controls whether a router permits or denies packets to pass, based on criteria in the packet header. To determine whether a packet is permitted or denied, it is tested against the ACL statement in sequential order. When a statement matches, no more statements are evaluated, the packet is either permitted or denied. There is an implicit deny statement at the end of an ACL. If a packet does not match any of the statements in the ACL, it is dropped.

#### Processing Interface ACLs

ACLs can be applied to an Interface for inbound and outbound traffic. However a seperate ACL for each direction is needed. 
