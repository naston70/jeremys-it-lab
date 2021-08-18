## ACL Concepts

Exam Topics

- Configure and verify ACLs

#### ACL Operation

A routers default operation is to forward all packets, as long as a route for the packet exists and the link is up. ACLs can help implement a basic level of security. However, they are not the only security solution a large organization should implement. In fact ACLs increase latency of router. If the organization is very large, with routers managing traffic of hundreds or thousands of users, the administrator will likely use a combination of other security implementations, beyond CCNA.


#### Defining an ACL

An ACL is a router configuration script that controls whether a router permits or denies packets to pass, based on criteria in the packet header. To determine whether a packet is permitted or denied, it is tested against the ACL statement in sequential order. When a statement matches, no more statements are evaluated, the packet is either permitted or denied. There is an implicit deny statement at the end of an ACL. If a packet does not match any of the statements in the ACL, it is dropped.

#### Processing Interface ACLs

ACLs can be applied to an Interface for inbound and outbound traffic. However a seperate ACL for each direction is needed. 

For inbound traffic, the router checks for an inbound ACL applied to the interface before doing a route table lookup. Then, for outbound traffic, the router makes sure that a route to the destination exists before checking for ACLs. Finally, if an ACL statement results in a dropped packet, the router sends an ICMP destination unreachable message.

The choice of using an inbound or outbound ACL is easy to make if, first, place yourself in the router. From there you can visualize processing a packet coming into a router interface deciding what to do with the packet. 

#### List Logic with IP ACLs

An ACL is a list of commands that are processed in order, from the first statement in the list to the last statement. Each command has different matching logic that the router must apply when filtering is enabled. ACLs use first-match logic. If a packet matches one line in the ACL the router takes the action listed in that line of the ACL and ignores the rest of the statements. 

## Planning to Use ACLs
