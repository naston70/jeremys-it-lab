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
