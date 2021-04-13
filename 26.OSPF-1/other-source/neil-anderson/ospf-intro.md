## OSPF Characteristics

* OSPF is a Link State routing protocol
* Supports large networks
* Has fast convergence
* Messages are sent sing multicast
* OSPF is an open standard
* Uses Dijkstra's Shortest Path First algorithm

#### Link State Routing Protocols
* In Link State routing protocols, each router describes itself and its interfaces to its directly connected neighbors
* This information is passed unchanged from one router to another
* Every router learns the full picture of the network, its interfaces and what they connect to
* OSPF routers use LSA link State Advertisements to pass on routing updates

#### OSPF Operations
1. Discover neighbors
2. Form adjacencies
3. Flood Link State Database
4. Compute Shortest Path
5. Install best routes in routing table
6. Respond to network changes

#### OSPF Packet Types

- Hello: A router will send out and listen for Hello packets when OSPF is enabled on an interface, and form adjacencies with other OSPF routers on the link 
- DBD Database Description: Adjacent routers will tell each other the networks they know about with the DBD packet
- LSR Link State Request: If a router is missing information about any of the networks in the received DBD, it will send the neighbor an LSR
- LSA Link State Advertisement: A routing update
- LSU Link State Update: Contains a list of LSA's which should updated, used during flooding
- LSack: Receiving routers acknowledge LSAs







interface
