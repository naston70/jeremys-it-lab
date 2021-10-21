## QOS

The purpose of QoS is to give certain kinds of network traffic priority over others during congestion

**Classification** organizes network traffic (packets) into traffic classed (categories)

- Classification is a fundamental to QoS. To give priority to certain types of traffic, you have to identify which types of traffic to give priority to 
- There are many methods of classifying traffic:
	* An ACL: Traffic permitted by the ACL will be given certain treatment, other traffic will not.
	* NBAR: performs a DPI, looking beyond layer 3 and 4 up to layer 4
	* In the Layer 2 and Layer 3 headers there are specific fields used for classification:
		- The PCP
		- The DSCP

**PCP**

PCP is also known as CoS (Class of Service). Defined by IEEE 802.1p
3 bits in length = 8 possible values (2 to the power of 3 = 8)

PCP values 0: 'best effort' delivery means there is no guarantee that data is delivered or that it meets any QoS standard. This is regular traffic

PCP values 3 and 5: IP phones **mark** call signalling traffic as PCP3, they **mark** the actual voice traffic as PCP5


PCP/CoS  because PCP is found in the dot1q header, it can only be used over the following connections:
* trunk links
* access links with a voice vlan

**DSCP**

IPP updated to DSCP, new standard markings had to be decided. By having generally agreed upon standard markings for different kinds of traffic, QoS design and implementation is simplified, QoS works better between ISPs and enterprises, among other benefits.

The markings are DF - best effort traffic and EF - low loss/latency/jitter traffic, AF assured forwarding and CS, class selector (IPP backward compatibility)


#### Trust Boundaries

The trust boundary of a network defines where devices trust or dont trust the QoS markings of received messages
- If the markings are trusted, the device will forward the messages without changing the markings
- If the markings aren't trusted, the device will change the markings according to the configured policy

* If an IP phone is connected to the switch port, it is recommended to move the trust boundary to the IP phones
* This is done via configuration on the port switch connected to the IP phone
* If a user marks their PC's traffic with a high priority, the marking will be changed

#### Queuing / Congestion Management

- When a network receives traffic at a faster rate than it can forward the traffic out of the appropriate interface, packets are placed in that interfaces queue as they wait to be forwarded
- When the queue becomes full, packets that don't fit in the queue are dropped
- RED and WRED drop packets early to avoid tail drop

* An essential part of QoS is the use of multiple queues - this is where classification plays a role. The device can match traffic based on various factors (ie the DSCP marking in the IP header) and then place it in the appropriate queue
* However, the device is only able to forward one frame out of an interface at once, so a scheduler is used to decide, which queue traffic is forwarded from next - prioritization allows the scheduler to give certain queues more priority than others.

 * A common scheduling method is weighted round robin
 - **round-robin:** packets are taken from each queue in order
 - **weighted:** more data is taken from high priority queues each time the scheduler reaches that queue  
 
* CBFWQ (Class based Weighted Fair Queuing) is a popular method of scheduling, using a weighted round-robin scheduler while guaranteeing each queue a certain percentage of the interfaces bandwidth during congestion 


CLASSIFY --> QUEUE --> SCHEDULE --> TRANSMIT 

#### Shaping and Policing

Traffic shaping and policing are both used to control the rate of traffic

* Shaping buffers traffic in a queue if the traffic rate goes over the configured rate 
* Policing drops traffic if the traffic rate goes over the configured rate
- Burst traffic over the configured rate is allowed for a short period of time
- This accommodates data applications which typically are bursty in nature - the amount of burst traffic is configurable.

In both cases, classification can be used to allow for different rates for different kinds of traffic
