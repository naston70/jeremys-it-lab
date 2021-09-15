## How Routers Learn About Routes 

To be able to route a packet, a router must know at least the following:

* Destination address to where the packet is destined.
* Neighboring routers from which remote networks can be learned and packets can be moved to on way to its destination 
* Routes to remote networks and a way to determine the best route to each of them 
* Ways to learn, verify and manage routing information. Incomplete, incorrect or unstable routing information is worse than not having any routing information. If a router does not have routing information it will drop packets and inform the source. If the router has incorrect information loops can form and possibly bring networks down.

Routing information is stored in the table. This table consists of routes to destination networks. Each route is a combination of the destination network address, subnet mask and the next hop towards the destination. 

###### There are 3 ways for a router to learn routes:

1. Static Routing - This is the method by which an administrator manually adds routes to the routing table of a router. Usually used on small networks as it is not very scalable

2. Default Routing - This is the method where all routers are configured to send all packets towards a single router. This is a useful method for small networks or networks with a single entry and exit point. 

3. Dynamic Routing - This is the method where protocols and algorithms are used to automatically propagate routing information. This is the most common method and most complex. 

#### The Routing Table (ciscopress)

The routing table of a router store information about the following:
- *Directly connected routes* - these routes come from the active router interfaces. Routers add a directly connected route when an interface is configured with an IP address and is activated

- *Remote Routes* - these are remote networks connected to other routers. ROutes to these networks can be statically configured or learned through Dynamic Routing Protocols.

Specifically, a routing table is a data file in RAM that stores route information about directly connected and remote networks. The routing table contains network or next-hop associations. These associations tell a router that a particular destination can be optimally reached by sending the packet to a specific router that represents the next hop on the way to the final destination. The next-hop association can also be the outgoing or exit interface to the next destination.

#### Routing Table Sources

On a Cisco router the ```show ip route``` command is used to display the IPv4 routing table of a router. A router provides additional information, including how the route was learned, how long the route has been in the table, and which specific interface to use to get to a predefined destination. 

Entries in the routing table can be added as follows:

* Local route interfaces - Added when a interface is configured and active. 
* Directly connected interfaces - added to the routing table when an interface is configured and active 
* Static routes - added when a route is manually configured and the exit interface is active 
* Dynamic routing protocol - added when routing protocols are implemented and other networks are identified

The sources of the routing table entries are identified by a code. The code identifies how the route was learned.

* L = identifies the address assigned to a routers interface. This allows the router to efficiently determine when it receives a packet for the interface instead of being forwarded 
* C = a directly connected network
* S = a static route created to reach a specific network 
* D = a dynamically learned network from another router using EIGRP 
* O = dynamically learned network from another router using OSPF 

#### Remote Network Routing Entries
```
D        10.1.1.0/24 [90/2170112] via 209.165.200.226, 00:01:30, Serial0/0/0

A         B           C     D               E              F         G 
```

######Parts of a Remote Network Entry