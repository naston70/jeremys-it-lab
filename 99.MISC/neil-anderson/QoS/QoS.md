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
* Congestion cause delay to packets as they wait in the queue
* As the size of the queue changes it causes jitter 
* There is a limit to the size of the queue. If a packet arrives when the queue is full the router will drop it 
* Voice and Video calls (and apps) will be unacceptable quality if they do not meet their delay, jitter and loss requirements

#### How to mitigate congestion:

- Add more bandwidth, which costs more money
- Use Quality of Service techniques to give better service to the traffic which needs it 

**using QoS example:**
- Packets begin to arrive faster than 2 Mbps
- Packets wait in the queue to go out
- The router recognises the voice packets and moves them to the front of the queue to minimise their delay

#### Effects of QoS Queuing

* QoS queuing can reduce latency, jitter and loss for particular traffic 
* The original driver for QoS was VOIP but it can also be used to give better service to data applications
* If one type of service is getting better service then the other types must be getting worse service
* The point is to give each type of traffic the service it requires 
* QoS queuing is not a magic bullet and is designed to mitigate temporary periods of congestion. If a link is permanently congested the bandwidth should be increased 

#### Classification and Marking 

- For a router or switch to give a particular level of service to a type of traffic, it has to recognise that traffic first 
- Common ways to recognise traffic are by COS (class of service) marking, DSCP (differentiated services code point) marking, an Access Control List or NBAR (Network based application recognition)

#### Layer 2 Marking - CoS Class of Service 
* There is a 3 bit field in the Layer 2 802.1q frame header which is used to carry the CoS QoS marking 
* A value of 0-7 can be set. The default value is 0 which is designated as Best Effort Traffic
* CoS 6 and 7 are reserved for network use 
* IP phones mark their call signaling traffic as CoS 3 and their voice payload as CoS 5

#### Layer 3 Marking - DSCP 
- The ToS Type of Service byte in the Layer 3 IP header is used to carry the DSCP QoS marking
- 6 bits are used which gives 64 possible values. The default value is 0 which is designated as Best Effort traffic 
- IP phones mark their call signalling traffic as 24 (CS23) an their voice payload as 46 (EF)
- These are standard markings for other traffic types, such as 26 (AF31) for mission critical data, and 34 (AF41) for SD video 

#### The Trust Boundary 
- The switch should be configured to trust markings from the IP phone and pass them on unchanged, but mark traffic from the PC down to CoS 0 and DSCP 0

#### Quality Requirements for Video and Voice 
- Voice and video endpoints mark their own traffic with a DSCP value 
- If you want to give a particular quality of service to another application running between a workstation and a server, the endpoints will typically be unable to mark their own traffic 
