## Ethernet Switching

#### TOPICS:
* Explain the role and function of network components
* Describe switching concepts

###### Evolution to Switching 

Todays LANs almost exclusively use switches to interconnect end devices, however this was not always the case. Initially devices were connected to a physical bus (long run of cable). With the introduction of 10BASE-T and UTP cabling, the hub gained popularity as a cheaper, easier way to connect devices. But, even Hubs had limitations:

- A frame sent from one device can collide with a frame sent by another device attached to that LAN segment. Devices were in the same collision domain sharing the bandwidth.

- Broadcasts sent by one device were heard and processed by all other devices on the LAN. Devices were in the same broadcast domain. 

Ethernet bridges were developed to solve some of the inherent problems in a shared LAN. A bridge basically segmented a LAN into two collision domains, which reduced the number of collisions in a LAN segment. This increased the performance of collisions in a LAN segment. This increased the performance of the network by decreasing unnecessary traffic from another segment. 

When switches arrives, these devices provided the same benefits of bridges as well as the following:

- Larger number of interfaces to break up the collision domain into more segments
- Hardware-based switching instead of using software to make the decision

In a LAN where all nodes are directly connected to the switch, the throughput of the network increases dramatically. With each computer connected to a seperate port on the switch, each is in a seperate collision domain and has its own dedicated segment. There are three primary reasons for this increase:

- Dedicated bandwidth to each port
- Collision free environment 
- Full-duplex operation 

#### Switching Logic

Ethernet switches selectively forward individual frames from a receiving port to the port where the destination node is connected. During this instant, the switch creates a full bandwidth. logical point to point connection between the two nodes. 

Switches create this logical connection based on the source and destination MAC addresses in the Ethernet header. Specifically, the primary job of a LAN switch is to receive frames and then make a decision to either forward the frame or ignore the frame. To accomplish this, the switch performs three actions:

Step 1. Decides when to forward a frame or when to filter a frame, based on the destination MAC

Step 2. Learns MAC addresses by examining the source MAC address of each frame the switch receives. 

Step 3. Creates a loop-free environment with other switches using STP


To make the decision to forward or filter the switch uses a dynamically built MAC address table stored in RAM. By comparing the frames destination MAC address with the fields in the table, the switch decides how to forward and/or filter the frame.

#### Collision and Broadcast Domains 

A collision domain is the set of LAN interfaces whose frames could collide with each other. All shared media environments, such as those created by using hubs, are collision domains. When one host is attached to a switch or port, the switch creates a dedicated connection, thereby eliminating the potential for a collision. Switches reduce collisions and improve bandwidth use on network segments because they provide full-duplex, dedicated bandwidth to each network segment. 

Out of the box, a switch cannot provide relief from broadcast traffic. A collection of connected switches forms one large broadcast domain. If a frame with FFFF.FFFF.FFFF crosses a switch port, that switch must flood the frame out all other active ports. Each attached device must then process the broadcast frame at least up to the network layer. 


#### Frame Forwarding

Switches operate in several ways to forward frames;

###### Switch Forwarding Methods

- Store-and-forward switching: The switch stores received frames in its buffers, analyzes each frame for information about the destination and evaluates the data integrity using the CRC check in the frame trailer. The entire frame is stored and the CRC is calculated before any of the frame is forwarded. If the CRC passes, the frame is forwarded to the destination 

- Cut-through switching: The switch buffers just enough of the frame to read the destination MAC address so that it can determine which port to forward the data to. When the switch determines a match between the destination MAC and an entry in the MAC address table, the frame is forwarded out the appropriate port. This happens as the rest of the initial frame is still being received. The switch does not perform any error checking. 

- Fragment-free mode: The switch waits for the collision window to pass before forwarding the frame. This means that each frame is checked into the data field to make sure that no fragmentation has occurred. Fragment free mode provides better error checking than cut-through, with practically no increase in latency.

#### Symmetric and Asymmetric Switching 

Symmetric switching provides switched connections between ports with the same bandwidth, such as all 100 mbps ports or all 1000 mbps ports. An asymmetric LAN switch provides switched connections between ports of unlike bandwidth.

#### Memory Buffering

Switches store frames for a brief time in a memory buffer. Two methods of memory buffering exist:

- Port based memory: frames stored in queues that are linked to specific incoming ports 
- Shared memory: frames are deposited into a common memory buffer that all ports on the switch share

###### Layer 2 and Layer 3 Switching

A Layer 2 LAN switch performs switching and filtering based only on MAC addresses. A Layer 2 switch is completely transparent to network protocols and user applications. A Layer 3 switch functions similarly to a Layer 2 switch but instead of using only the Layer 2 MAC address information for forwarding decisions, a Layer 3 switch can also use IP address information. Layer 3 switches are also capable of performing Layer 3 routing functions, reducing the need for dedicated routers on a LAN. Because Layer 3 switches have specialized switching hardware, they can typically route data as quickly as they can switch data.

#### Ethernet Overview


