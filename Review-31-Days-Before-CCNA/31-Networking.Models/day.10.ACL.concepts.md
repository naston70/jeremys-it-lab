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

Because an ACL can be used to filter traffic it is important that the implementation of an ACL is thoroughly planned before actual configuration.

#### Types of ACL 

ACLs can be configured to filter any type of protocol traffic, including other network layer protocols such as Apple Talk and IPX. CCNA focuses on IPv4 and IPv6.

- Standard IPv4 ACLs: Filter traffic based on source address only security
- Extended IPv4 and IPv6 ACLs: filter based on source and destination, specific protocols and source and destination TCP and UDP ports.

Two methods can be used to identify both standard and extended ACLs:

* Numbered IPv4 ACLs: use a number for identification
* Named IPv4 and IPv6 ACLs: use a descriptive name or number for identification

Named ACLs must be used with some types of Cisco configurations, including IPv6 ACLs. However they provide two basic benefits for standard and extended IPv4 ACLs:

- By using a descriptive name, (BLOCK-FTP) a network administrator can more quickly determine the purpose of an ACL. This is particularly helpful in large networks, where a router can have many ACLs with 100's of statements
- They reduce the amount of typing you must do to configure each statement in a name ACL

Both numbered and named ACLs can be configured for standard as well as extended ACL implementations

#### ACL Identification

**Ranges:**
Protocol: IP          | Range 1 - 99
Protocol: Extended IP | Range 100 - 199
Protocol: Standard IP | Range 1300 - 1999
Protocol: Extended IP | Range 2000 - 2699

Named IP ACLs give more flexibility in working with the ACL entries. In addition to using more memorable names, using named instead of numbered ACLs enables you to delete individual statements in a name IP access list 

IOS 12.3 introduced IP access list entry sequence numbering for both numbered and named ACLs. IP access list entry sequence numbering provides the following benefits:

* You can edit the order of ACL statements
* You can remove individual statements from an ACL 
* You can use the sequence number to insert new statements into the middle of the ACL 

Sequence numbers are automatically added to the ACL if they are not entered explicitly at the time of creation

#### ACL Design Guidelines
