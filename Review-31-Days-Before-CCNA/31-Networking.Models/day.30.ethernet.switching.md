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
