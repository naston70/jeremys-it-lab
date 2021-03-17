# OSPF NETWORK TYPES

* The OSPF 'network type' refers to the type of connection between OSPF neighbors (Ethernet, etc)
* There are 3 main OSPF network types:
	- **Broadcast:** enabled by default on Ethernet and FDDI (Fiber Distributed Data Interfaces) interfaces
	- **Point-to-Point:** enabled by default on PPP and HDLC interfaces
	- **Non-broadcast:** enabled by default on Frame Relays and X.25 interfaces

#### Broadcast Network Type

* Enabled on Ethernet and FDDI by default
* Routers dynamically discover neighbors by sending/listening for OSPF hello messages using multicast address 224.0.0.5
* A DR (designated router) and BDR (backup designated router) must be elected on each subnet (only DR if there are no ospf neighbors)
* Routers which aren't the DR or BDR become a DROther
* The DR/BDR election order of priority is:
	1. The highest OSPF interface priority
	2. The highest OSPF Router ID

* First place becomes the DR for the subnet, second place becomes the BDR
* The default OSPF interface priority is 1 on all interfaces
* In the broadcast network type, routers will only form a full OSPF adjacency with the DR and BDR of the segment
* Therefore routers only exchange LSAs with the DR and BDR. DROthers willnot exchanges LSAs with each other
