## QoS

###### Exam Topic

- Explain the PHB for QoS such as classification, marking, queuing congestion, policing shaping

#### QoS

Normal default operation for switches and routers is to process frames and packets in the order in which they are received. FIFO does not discriminate between traffic types

QoS tools are used to classify traffic types based on the four following characteristics

- Latency: Latency, or delay, is the amount of time it takes for data to be sent to the receiver. QoS tools can reduce the delay for time-sensitive packets, such as voice and video
- Jitter: Jitter is the variance in the delay of packets. QoS tools can even out the delay of packets to improve end user experience
- Loss: Loss refers to the number of lost messages, usually as a percentage of the packets sent. QoS tools reduce packet loss, especially for time sensitive traffic
- Bandwidth: Bandwidth is a measure of the amount of data an interface can send every second. QoS tools can manage which traffic type gets to use the bandwidth next and how much of the bandwidth each type of traffic gets over time. 

#### Characteristics of Major Traffic Types

###### VOICE:
* Smooth
* Benign
* Drop sensitive
* Delay sensitive
* UDP priority

- One-Way Requirements
    * Latency < 150 ms 
    * Jitter  < 30 ms 
    * Loss    < 1% 
    * Bandwidth (30-128 kbps)

###### VIDEO:
* Bursty
* Greedy
* Drop sensitive
* Delay sensitive
* UDP priority

- One-Way Requirements
    * Latency < 200 - 400 ms 
    * Jitter  < 30 - 50 ms 
    * Loss    < 0.1 - 1%
    * Bandwidth (384 kbps - 20+ Mbps)

#### Overview of QoS tools

* classification and marking: QoS tools monitor traffic flows and classify packets based on the header contents. Messages are then marked by changing bits in the header

* congestion avoidance: when traffic exceeds available network resources, some traffic might be selectively dropped, delayed or remarked to avoid congestion 

* congestion management: QoS tools manage the scheduling and shaping of traffic while packets wait their turn in a queue to exit the interface  

#### Classification and Marking

Classification refers to the process of matching fields in the headers to take some type of QoS action on the packet. These fields can include all the normal fields filtered by ACLs as well as the Type of Service (ToS) field in an IPv4 packet or the Traffic Class field in an IPv6 header.

Marking refers to  the process of changing bit values in the ToS or Traffic Class field

The Differentiated Service Code Point (DSCP) bits are the core of the Differentiated Services (DiffServ) model for QoS. QoS tools can use the two bits allotted for IP explicit congestion notification (ECN) to inform downstream routers of congestion in the traffic flow 

#### DSCP and IPP

As standardized in RFC 2474, the 8 DSCP bits provide 64 different classifications that QoS can use. This is a vast improvement over the eight classifications allotted for the 3 bits in the previous IPP field. For backward compatibility, the DSCP bits include the Class Selector (CS) values that are designated to match the IPP bits.

For Layer 2 trunk links, the third byte of the 4-byte 802.1Q header is reserved for the Class of Service (CoS) and QoS tools can use it to mark frames. However, this field exists only as long as the frame is traversing trunk links. To continue the same level of service as traffic is routed on Layer 3, the ToS field must be marked. 

#### EF and AF 


