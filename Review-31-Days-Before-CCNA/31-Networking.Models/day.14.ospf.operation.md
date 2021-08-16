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
