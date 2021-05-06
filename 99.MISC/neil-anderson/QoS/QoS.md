## Quality of Service

#### Dedicated Voice, Video and Data Networks 

QoS is queuing - Old network setup was to have 3 seperate networks for voice, video and data. 
Modern networks run Converged Networks where all three run over the same IP network 

- This enables cost savings and advanced features for voice and video 
- Data, voice and video are now all fighting for the same shared bandwidth

#### Quality Requirement for Voice and Video

* Voice and traditional standard definition video packets must meet these recommend requirements to be an acceptable quality call
    * Latency < 150 ms 
    * Jitter  < 30 ms 
    * Loss    < 1% 
* These are one-way requirements, meaning a packet sent from a phone in HQ has 150ms to reach the phone in the branch and vice versa
* HD video has stricter requirements 

#### FIFO 
- Whenever congestion is experienced on a router or switch, packets are sent out in a FIFO manner by default
- COngestion can be experienced whenever it is possible for packets to come in quicker than they can be sent out 

#### Congestion example:

100 Mbps LAN ----------- [router] ----------- 2 Mbps WAN

- Traffic is going left to right from the HQ to the branch 
- The WAN edge router has a FastEthernet interface on the inside LAN interface and an E1 interface on the outside of the WAN interface 

- When traffic arrives at a rate of 2 Mbps or slower the router has no problem sending out the traffic immediately
- However, when the rate of traffic exceeds 2 Mbps, the router will buffer the packet.
- Packets are arriving faster than they can be sent out 
- Packets wait in the queue to go out 
- Packets are sent out FIFO in the order they were received 

#### Effects of Congestion 


