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

Once an OSPF router ID is selected, it is not changed even if the interface that is used to select it changed its operational state or its IP address. To change the OSPF process command or reload the router. 

```
#####
Verifying the Router IDs on R2 and R3
#####

R2# show ip protocols
*** IP Routing is NSF aware ***

Routing Protocol is "ospf 2"
  Outgoing update filter list for all interfaces is not set
  Incoming update filter list for all interfaces is not set
  
Router ID 2.2.2.2
  Number of areas in this router is 1. 1 normal 0 stub 0 nssa
  Maximum path: 4
  Routing for Networks:
    172.16.12.0 0.0.0.3 area 1
    192.168.2.0 0.0.0.255 area 1
  Routing Information Sources:
    Gateway         Distance      Last Update
    1.1.1.1              110      00:02:55
  Distance: (default is 110)

R3# show ip protocols | include ID
  Router ID 3.3.3.3
```

The OSPF neighborship on R2 and R· can be verified using ```show ip ospf neighbor``` command

```
R2# show ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface
1.1.1.1           1   FULL/DR         00:01:57    172.16.12.1     Serial0/0

R3# show ip ospf neighbor

Neighbor ID     Pri   State           Dead Time   Address         Interface
1.1.1.1           1   FULL/DR         00:00:39    172.16.13.1     Ethernet0/0
```

The command ```show ip ospf neighbor``` displays OSPF neighbor information on a per-interface basis. The significant fields of the outputs are as follows:

* Neighbor ID: represents neighbor router ID
* Priority: Priority on the neighbor interface used for the DR/BDR election
* State: A Full state represents the final stage of OSPF neighbor establishment process and denotes that the local router has established full neighbor adjacency with the remote OSPF neighbor. DR means that the DR/BDR has been completed and the router 1.1.1.1 has been elected as the DR 
* Dead Time: Represents the value of the dead timer. When this timer expires, the router terminates the neighbor relationship. Each time a router receives an OSPF Hello packet from a specific neighbor, it resets the dead timer back to its full value
* Address: Primary IPv4 address of the neighbor router 
* Interface: Local interface over which an OSPF neighbor relationship is established

Output of the show ```ip ospf interface``` command shows you all interfaces enabled in the OSPF process. For each enabled interface, you can see detailed information such as OSPF area ID, OSPF process ID and how the interface was included into the OSPF process. 

OSPF routes are verified in the routing table using ```show ip ospf route```
OSPF clearly distinguishes two types of routers: intra-area routes and interarea routes. 
Intra-area routes in the routing tables is O. The second type is interarea routes, which originate in other areas and are inserted into the local area to which the router belongs. 

###### Using OSPF Priority in the DR/BDR Election

One of the fields in the OSPF Hello packet used in the DR/BDR election process is the Router Priority field. Every broadcast and NBMA OSPF enabled interface is assigned a priority value between 0 and 255. By default the OSPF interface priority is 1 and can be manually changed by using the ```ip ospf priority``` interface command. When electing a DR and BDR, the routers view the OSPF priority value of other routers during the Hello packet exchange process and then use the following conditions to determine which router to select:

* The router with the highest priority value is elected the DR 
* The router with the second highest value is the BDR 
* In case of a tie where two routers have the same priority value, router ID is used as the tiebreaker
* A router with a priority of 0 cannot become the BR or BDR. A router that is not the DR or BDR is called a DROTHER

###### Manipulating OSPF Timers

OSPF uses two timers to check neighbor reachability, the hello and dead intervals.The values of hello and dead intervals are carried in OSPF Hello packets and serve as a keepalive message, with the purpose of acknowledging the presence of the router on the segment. The hello interval specifies the frequency of sending OSPF Hello packets in seconds. The OSPF dead timer specifies how long a router waits to receive a Hello packet before it declares a neighbor down. 

OSPF requires that both hello and dead timers be identical for all routers on the segment to become ospf neighbors. The default value of the OSPF Hello timer on multiaccess broadcast and point-to-point links is 10 seconds and is 30 seconds on all other network types, including NBAA. When you configure the hello interval, the default value of the dead interval is automatically adjusted to four times the hello.

To detect faster topological changes, you can lower the value of OSPF hello interval with the downside of having more routing traffic

###### Modifying the Hello and Dead Intervals
```
R1(config)# interface serial 2/0
R1(config-if)# ip ospf hello-interval 8
R1(config-if)# ip ospf dead-interval 30
*Jan 20 13:17:34.441: %OSPF-5-ADJCHG: Process 1, Nbr 2.2.2.2 on Serial2/0 from
FULL to DOWN, Neighbor Down: Dead timer expired
```

Once the default OSPF hello and dead interval values on the Frame Relay link are changed, both routers will detect hello timer mismatch. The dead timer will not be refreshed and the OSPF relationship is down. 

#### OSPF DR Election Process

OSPF works by the DR and BDR listening for routing updates from the DROTHERS through multicast communication. When these updates are received, they are responsible for the flooding of the updates to all of the other DROTHERS. There are two things that can be used to influence and control the OSPF DR election process:

* OSPF Device Priority
* OSPF Device Router-ID 

###### OSPF Device Priority

Through the use of device interface priority within OSPF, you can influence which device becomes the OSPF DR or BDR. The priority values range from 0-255 with 0 meaning the device would not participate in the election process. Default priority values are 1. Within the network, changing the interface OSPF priority values facing the OSPF area is what would need to be done.

```
interface f0/0
ip ospf priority 255
```

This would set the interface to the maximum value of 255, which would make it the DR as long as no other device had 255 as its priority. Common practice is to set 255 for the router desired to be DR and 254 for the BDR with all other devices left at 1.

###### OSPF Device Router-ID
