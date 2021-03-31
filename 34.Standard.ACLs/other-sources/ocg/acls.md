## IPv4 Access Control Basics

IP ACLs give engineers a way to identify different types of packets. To do so the ACL configuration lists values that the router can see in the IP, TCP, UDP and other headers. ie an ACL can match packets with source 1.1.1.1 or packets whose destination IP address is some address in a subnet or packets with a destination port of 23 (telnet)

Engineers can enable ACLs on a router so that the ACL sits in the forwarding path of packets as they pass through the router. Once enabled the router considers whether to forward or drop the packet depending on the rules in the ACL.

ACLs can also be used for many other features such as QoS. 

#### ACL Location and Direction
Cisco routers can apply ACL logic at the point in which in enters the router or the point in which it leaves - ACLs become associated with an interface and for a direction of packet flow (in or out)

To filter a packet you must enable an ACL on an interface that processes the packet, in the same direction the packet flows through the interface. 

When enabled, the router then processes every inbound or outbound IP packet using that ACL.

#### Matching Packets

When thinking about the location and direction for an ACL,  what packets are to be filtered and which ones to allow through must be known.
To tell a router those same ideas, the router must be configured with an IP ACL that matches packets. *Matching packets* refers to how to configure the ACL commands to look at each packet, listing how to identify which packets should either be dropped or allowed through.













