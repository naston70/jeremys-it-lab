# OSPF

Link State routing protocol.

* When using a link state routing protocol, every router creates a connectivity map of the network
* To allow this each router advertises information about its interfaces (connected networks) to it neighbours. These advertisements are passed along to other routers, until all routers in the network develop the same map 
* Then each router independently uses this map to calculate the best routes to each destination
* Link state protocols use more resources (CPU) on the router as more information is shared
* However, link state protocols tend to be faster in reacting to changes in the network than distance vector protocols

#### Open Shortest Path First

- Uses the Shortest Path First algorithm
- Three Versions:
	+ OSPFv1 (not used anymore)
	+ OSPFv2 (used for IPv4)
	+ OSPFv3 (used for IPv6, but can be used for IPv4)

- Routers store information about the network in LSAs (link state advertisements), which are organized in a structure called the LSDB (link state database)
- Router will flood LSAs until all routers in the OSPF area develop the same map of the network. (same LSDB)

LSA Flooding:- 
	+ OSPF is enabled on an interface
	+ The router creates an LSA to tell its neighbors about the network on the interface
	+ The LSA is flooded throughout the network until all routers have received it.
	+ This results in all routers sharing the same LSDB
	+ Each router then uses the SPF algorithm to calculate its best route to the new network

