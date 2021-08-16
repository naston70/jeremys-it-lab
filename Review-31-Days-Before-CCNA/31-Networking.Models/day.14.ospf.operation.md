## OSPF Operation

Exam Topics
- Determine how a router makes a forwarding decision by default
- Configure and verify single-area OSPFv2

#### Single-Area OSPF Operation 

The IETF chose OSPF over IS-IS as its recommended IGP. In 1998 OSPFv2 was updated. IOS chooses OSPF routes over RIP routes as OSPF AD is 110 and RIPs is 120

#### OSPF Message Format

The data portion of an OSPF message is encapsulated in a packet. This data field can include one of five OSPF packet types. 
The OSPF packet header is included with every OSPF packet, regardless of its type. The OSPF packet header and packet type-specific data are then encapsulated in an IP packet. In the IP packet header, the protocol field is set to 89 to indicate OSPF and the destination address is typically set to one of two multicast addresses. 224.0.05 or 224.0.0.6. 

If the OSPF packet is encapsulated in an Ethernet frame, the destination MAC address is also a multicast address

#### OSPF Packet Types

Each of the five OSPF packet types serves a specific purpose in the routing process:

* Hello: Hello packets establish and maintain adjacency with other OSPF routers
* DBD: The db description packet contains an abbreviated list of the sending routers link-state database. Receiving routers use it to check against the local link-state database
* LSR: Receiving routers can request more information about any entry in the DBD by sending a link-state request (LSR)
* LSU: Link-state update packets reply to LSRs and announce new information. LSUs contain 11 types of LSAs
* LSack: When an LSu is received, the router send a link-state acknowledgment to confirm receipt of the LSU 

#### Neighbor Establishment

OSPF neighbors exchange hello packets to establish adjacency
(important fields in the hello packet)

* **Type:** OSPF packet type - Hello (1), DBD (2), LS Request (3), LS Update (4), LS ACK (5)
* **Router ID:** ID of the originating router 
* **Area ID:** Area from which the packet originated
* **Network Mask:** Subnet mask associated with the sending interface
* **Hello Interval:** Number of seconds between the sending routers hellos
* **Router Priority:** Used in DR/BDR election
* **Designated Router:** Router iD of the DR, if any 
* **DBR:** Router ID of the BDR, if any 
* **List of Neighbors:** The OSPF router ID of the neighboring router 

Hello packets are used to do the following:

- Discover OSPF neighbors and establish neighbor adjacencies
- Advertise parameters on which two routers must agree to become neighbors 
- Elect the DR and BDR on multiaccess networks such as Ethernet and Frame Relay

Receiving an OSPF hello packet in an interface confirms for a router that another OSPF router exists on this link. OSPF then establishes adjacency with the neighbor. To establish adjacency, two OSPF routers must have the following matching interface values:

* Hello Interval
* Dead Interval
* Network Type 
* Area ID 

Before two routers can establish adjacency, both interfaces must be part of the same network, including the same subnet mask. Full adjacency happens after the two routers have exchanged any necessary LSUs and have identical link-state databases. By default, OSPF hello packets are sent to the multicast address 224.0.0.5 every 10 seconds on multiaccess and point-to-point segments and ever 30 seconds on no broadcast multiaccess segments

#### Link-state Advertisements

LSUs are the packets used for OSPF routing updates. An LSU packet can contain 11 types of LSAs

#### OSPF DR and BDR 

Multiaccess networks create two challenges for OSPF regarding the flooding of LSAs:
- Creation of multiple adjacencies, with one adjacency for every pair of routers
- Extensive flooding of LSAs

The solution to managing the number of adjacencies and the flooding of LSAs on a multiaccess network is the designated router (DR). To reduce the amount of OSPF traffic on multiaccess networks, OSPF elects a DR and a backup DR (BDR). The DR is responsible for updating all other OSPF routers when a change occurs in the multiaccess network. The BDR monitors the DR and takes over from the DR and takes over as DR if the current DR fails. All other routers become DROTHERS. A DROther is a router that is neither the DR nor the BDR.

## OSPF Algorithm

Each OSPF router maintains a link-state database containing the LSAs received from all other routers. When a router has received all the LSAs and built its local link-state database, OSPF uses Dijkstra's shortest path first (SPF) algorithm to create an SPF tree. This algorithm accumulates cost along each path, from source to destination. The SPF tree is then used to populate the IP routing table with the best paths to each network. 

Each path is labeled with an arbitrary value for cost. Each router determines its own cost to each destination in the topology

#### Link-state Routing Process

All OSPF routers complete the following generic link-state routing process to reach a state of convergence

1. Each router learns about its own links and its own directly connected networks by detecting that an interface has a Layer 3 address configured and is in the up state 

2. Each router is responsible for establishing adjacency with its neighbors on directly connected networks by exchanging hello packets

3. Each router builds a link-state packet (LSP) containing the state of each directly connected link. This is done by recording all the pertinent information about each neighbor, including neighbor ID, link type and bandwidth

4. Each router floods the LSP to all neighbors, which then store all LSPs received in a database. Neighbors then flood the LSPs to their neighbors until all routers in the area have received the LSPs. Each router stores a copy of each LSP received from its neighbors in a local database

5. Each router uses the database to construct a complete map of the topology and computes the best path to each destination network. The SPF algorithm is used to construct the map of the topology and determine the best path to each network. All routers have a common map or tree of the topology, but each router independently determines the best path to each network within that topology

## OSPFV2 vs OSPFV3

OSPFv3 has the same functionality as OSPFv2 but uses IPv6 as the network layer transport, communicating with OSPFv3 peers and advertising IPv6 routes. OSPFv3 also uses the SPF algorithms the computation engine to determine the best paths throughout the routing domain. 

As with all other IPv6 routing protocols, OSPFv3 has seperate processes from its IPv4 counterpart. OSPFv2 and OSPFv3 each have seperate adjacency tables, OSPF topology tables and IP routing tables 

#### Similarities between OSPFv2 and OSPFv3

| Feature              | OSPFv2 and OSPFv3                                      |
|----------------------|--------------------------------------------------------|
|                      |                                                        |
| Link State           | Yes                                                    |
| Routing algo         | SPF                                                    |
| Metric               | Cost                                                   |
| Areas                | Support the same two-level hierarchy                   |
| Packet types         | Use the same hello,dbd,lsr,lsu,lsack                   |
| Neighbor discovery   | Transition through the same states using hello packets |
| LSDB Synchronization | Exchange contents of their LSDB between two neighbors  |
| DR and BDR           | Use the same function and election process             |
| Router ID            | 32-bit router ID, same process in determining the ID   |

#### v2 and v3 differences tables

| Feature              | OSPFv2                                  | OSPFv3                  |
|----------------------|-----------------------------------------|-------------------------|
|                      |                                         |                         |
| advertising          | IPv4                                    | IPv6                    |
| source address       | IPv4 source address                     | IPv6 link-local address |
| dst addresses        | 224.0.0.5 / 224.0.0.6                   | FF02::5, FF02::6        |
| Areas                | Support the same two-level hierarchy    |                         |
| Advertising Networks | using **network** command               | **ipv6 ospf area** cmd  |
| IP Unicast           | IPv4 unicast routing enabled by default | ipv6 unicast-routing    |
| Authentication       | Plain text and MD5                      | IPsec                   |

#### Multiarea OSPF Operation

Single-ares OSPF works fine in smaller networks in which the number of links is manageable. However, a single area with 900 routers and 2000 subnets would cause problems.
###### Single area design causes the following problems:

* **Large routing tables**: by default, OSPF does not summarize routing updates
* **Large LSDB**: In a single area, each router must maintain a database of all active links in the routing domain, regardless of whether that router is currently using a particular link.
* **Frequent SPF calculations**: In a large network, changes to the LSDB can cause routers to spend many CPU cycles recalculating the SPF algorithm and updating the routing table 

To address these issues, OSPF supports hierarchical design through the uses of multiple OSPF areas. Multiarea OSPF is useful in larger network deployments to reduce processing and memory overhead. This involves breaking the one LSDB into several smaller LSDBs by using multiple OSPF areas


## MultiArea OSPF Design

Multiarea OSPF design follows a couple of basic rules:

- Put all interfaces connected to the same subnet inside the same area
- An area should contiguous 
- Some routers might be internal to an area, with all interface assigned to that single area 
- Some routers might be area border (ABRs) because some interfaces connect to the backbone area and some connect to nonbackbone areas.
- All nonbackbone areas must connect to the connect to the backbone area (area 0) by having at least one ABR connected to both the backbone area and the nonbackbone area

