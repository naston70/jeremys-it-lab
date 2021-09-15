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

#### The Routing Table 


