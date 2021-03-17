# OSPF (ictshore notes)

OSPF is a Link State protocol. It doesn't exchange routes, instead routers talk about links by advertising which other routers are their neighbors. 

This process aims to give all routers the same understanding of the networks topology. Once the routers are converged all routers should have a map of the entire network.

This 'map' is the **OSPF Database**. However, once all routers have an updated database they still don't have routes. 
The router will take the db and look in it for the shortest path to any destination. It calculates the shortest distance by using Dijkstra's algorithm over the database and once found it will add a route to the routing table.

#### OSPF ADJACENCIES

OSPF implements its own transport layer. A router will put OSPF messages into IP packets and set the protocol number to 89. OSPF will have to handle acknowledgment and retransmissions itself. OSPF uses unicast and multicast to send packets.

* 224.0.0.5 is the multicast address for all OSPF routers in the same network
* 224.0.0.6 is the multicast address for all Designated OSPF Routers on the same network 

#### THE HELLO PACKET

Before two routers being sharing information, they must form an adjacency. OSPF periodically sends out Hello packets using the multicast address 224.0.0.5.

Routers include just basic information in a Hello with the purpose of discovery new neighbors. Once two routers see that they are neighbors they can start to create an adjacency. Once that is established they can start to exchange details about links. In fact routers need to go through several states to reach the goal of exchanging information.

#### OSPF STATES

Two routers will need to go through 7 or 8 states in order to converge. Understanding these states can help with troubleshooting. The 7 states are:

Down + Init + 2-Way + Exstart + Exchange + Loading + Full (Attempt is the 8th)

States from Down to 2-Way are concerned with forming an adjacency, once that is formed states from Exstart to Loading allow routers to talk about links. Once the topology is agreed upon they move into the Full state that represents convergence.

#### OSPF STATES - DESCRIPTIONS

- *Down*: is the initial stage, routers don't know each other
- *Init*: the router has received a hello packet and both routers must move to this state before continuing. This means each router has seen the hello packet of the other
- *2-Way*: in this state they have established a bidirectional communication tat can be used to talk about links
- *ExStart*: indicates that routers are beginning to exchange link information
- *Exchange*: routers send each other a summary of their OSPF database. This allows the other routers to have an idea about the links their neighbor knows about
- *Loading*: each router asks the neighbor for details about the new links. The router can tell what are the links it doesnt know - but the neighbor does. With this step, the two routers will end up with the same OSPF db
- *Full*: indicates that the routers have the same OSPF db. They can be called **fully adjacent**

Under normal conditions all routers should be fully adjacent, the exception is when Designated routers are needed.

#### THE ROUTER ID

To identify each link, the routers need to be identifiable. OSPF uses the concept of **Router ID**

The Router ID is a 32-bit numeric identifier of the router (X.X.X.X). This is not an IP address.

When OSPF is first configured on a router it will attempt to create a Router ID itself, to do so it will look for the following items:
	1. The highest IP among loopback interfaces (if none, the next item)
	2. The highest IP among Ethernet interfaces
	3. Although, the best practice is to configure the Router ID manually

#### THE OSPF DATABASE

The OSPF database is actually known as the Link State Database (LSDB).

The LSDB can be thought of as a set of tables, one of them stores all the Link States. Each Link State is a row containing the Router IDs of the two routers forming the links and a cost. The cost indicates how much cost it takes to go this path/ link. 

In the Exchange State, routers see a summary of the LSDB of the neighbor. The summary is known as the **Database Description (DBD)** and it is a specific OSPF packet to be unicasted. Based on that summary, the router decides which of the Link States they need more information on.

After this the Loading state is used to retrieve the information. In this state, the router that doesn't have a certain link uses a **Link State Request** LSR message. The other router will reply with a **Link State Advertisement (LSA)** (all using unicast)

OSPF is a 'sender', 'receiver' protocol. When exchanging data a router asks and the other responds. Things aren't done at the same time, they exchange roles once one has finished.

#### CALCULATING OSPF COST

Cost relies exclusively on the bandwidth of the link, the higher the bandwidth, the lower the cost. OSPF has the concept of **reference bandwidth** Default is 100 Mbps but Cisco allows this to be changed to fit particular needs.

cost = reference_bandwidth / interface_bandwidth

The cost of a path of multiple links is simply the sum of the cost of all the links in the path. If/when OSPF produces two paths to the same destination, the one with the lower cost will be the route used.


#### DESIGNATED ROUTER, BACKUP DESIGNATED ROUTER

OSPF adjacencies are *peer-to-peer*. It means an adjacency **involves two routers** and only two. If multiple routers are connected to a switch the number of adjacencies could grow as to not be scalable. To overcome that, OSPF uses the **Designated Router** and **Backup Designated Router**. On a broadcast network, OSPF routers will elect a designated router and a backup. Then they will establish adjacencies only toward them. The DR will make updates from a neighbor and sync the others. The BDR maintains the adjacencies already up to replace the DR in case it fails.

#### OSPF AREAS

Routers can be grouped into areas, groups of contiguous routers. Then routers will use their LSDB to map the topology for routers only in the same area. For routers in a different area, they don't care about the status of links. Instead they care about routes. ABRs will have one interface in one area and another in a different area. ABRs will take the LSDB from an area and create inter area routes to inject in the other area. For both directions.

#### THE BACKBONE AREA

OSPF identifies each area with a numeric ID. On top of that, it defines the concept of the backbone area, an area with the role of connecting other areas. The backbone area must have the ID set to 0. As a requirement, all areas must have at least an ABR shared with area 0, making them directly connected to area 0