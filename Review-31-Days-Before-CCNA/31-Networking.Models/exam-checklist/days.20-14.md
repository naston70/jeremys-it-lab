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

A. - Route Source - Identifies how the route was learned 
B. - Dst Network - Identifies the IPv4 address of the remote network
C. - Admin Distance - Identifies the trustworthiness of the route source, lower is preferred
D. - Metric - Identifies the value assigned to reach the remote network. Lower values indicate preferred routes
E. - Next Hop - IP address of the next router to forward the packet to 
F. - Route Timestamp - Identifies how much time has passed since the route was learned 
G. - Outgoing Interface - Identifies the exit interface to use to forward a packet toward the final destination 

## Types of OSPF packets

* Types of OSPF packet types

Type  |  Packet Name        | Protocol function          |
---------------------------------------------------------|
1     | Hello               | Discover/maintain neighbors|
2     | Db description      | Summarize database contents|
3     | Link State Request  | Database download          |
4     | Link State Update   | Database update            |
5     | Link State ACK      | Flooding Acknowledgement   |
---------------------------------------------------------|


#### Hello Packet 

Type 1 - Hello packets are used to discover, build and maintain OSPF neighbor adjacencies. To establish adjacency, OSPF peers at both sides of the link must agree on some parameters contained in the Hello packet to become OSPF neighbors.

Type 2 - Database Description packet (DBD). When the OSPF neighbor adjacency is already established, a DBD packet is used to describe LSDB so that routers can compare whether databases are in sync.

Type 3 - Link-State Request (LSR) packet. When the database synchronization process is over, the router might still have a list of LSAs that are missing in its database. The router will send a LSR packet to inform OSPF neighbors to send the most recent version of the missing LSAs

Type 4 - Link-State Update (LSU) packet. There are several types of LSUs, known as LSAs. LSU packets are used for the flooding of LSAs and sending LSA responses to LSR packets. It is sent only to the directly connected neighbors who have previously requested LSAs in the form of LSR packet. In case of flooding, neighbor routers are responsible for re-encapsulation of received LSA information in new LSU packets. 

Type 5 - Link State Acknowledgement (LSack) packet: LSAcks are used to make flooding of LSAs reliable. Each LSA received must be explicitly acknowledged. Multiple LSAs can be acknowledged in a single LSAck packet.


#### Basic OSPF Configuration

Example Topology 
5 routers R1-R5. R4 and R5 are pre-configured. R2 and R3 will be configured
R1, R4 and R5 are connected to common multiaccess Ethernet segment. R1 and R2 are connected over serial Frame Relay interface and R1 and R3 are also connected over Ethernet link. 

###### OSPF Configuration on R2 and R3
```
#####
config of OSPF on WAN and LAN interfaces on R2 and R3
#####

R2# conf t
R2(config)# router ospf 2
R2(config-router)# network 172.16.12.0 0.0.0.3 area 1
R2(config-router)# network 192.168.2.0 0.0.0.255 area 1

####
R3# conf t
R3(config)# router ospf 3
R3(config-router)# network 172.16.13.0 0.0.0.3 area 2
R3(config-router)# network 192.168.3.0 0.0.0.255 area 2
```

To enable the OSPF process on the router, use the ```router ospf router-id``` command. Process ID numbers between neighbors do not need to match for routers to establish an OSPF adjacency. The ID is an internally used ID parameter for an OSPF routing process and only has local significance. It is good practice to make the process ID the same on all routers. 

Cisco IOS software sequentially evaluates the ```ip-address wildcard-mask pair specified in the network command for each interface as follows:
- it performs a logical OR operation between a wildcard-mask argument and the interfaces primary IP
- it performs a logical OR operation between a wildcard-mask argument and the ip-address argument in the network command
- the software compares the two resulting values. If they match, OSPF is enabled on the associated interface and this interface is attached to the OSPF area specified

###### OSPF Router IDs
```
#####
OSPF Router IDs on R2 and R3 are configured 
#####
R2(config-router)# router-id 2.2.2.2
R3(config-router)# router-id 3.3.3.3
```

The OSPF router-id is a fundamental parameter for the OSPF process. For the OSPF process the start Cisco ISO must be able to identify a unique OSPF router ID. At least one primary IPv4 address on an interface in the up/up state must be configured for a router to be able to choose Router-ID, otherwise an error message is logged and the OSPF process does not start.

To choose the OSPF router ID at the time of OSPF process initialization, the router uses the following criteria:

1. Use the router ID specified in the ```router-id x.x.x.x``` command. You can configure an arbitrary value in the format but this value must be unique
2. Use the highest IPv4 address of all active loopback interfaces on the router 
3. Use the height IPv4 address among all active nonloopback interfaces 



