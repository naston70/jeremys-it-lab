## Quality of Service

##### Quality of Service Models

**Best Effort:** No QoS policies are implemented
**Integrated Services (IntServ):** Resource Reservation Protocol (RSVP) is used to reserve bandwidth per-flow across all nodes in a path
**Differentiated Services (DiffServ):** Packets are individually classified and marked; policy decisions are made independently by each node in a path

##### Terminology

*Per-Hop Behavior:* The individual QoS action performed at each independent DiffServ node 

*Trust Boundary:* Beyond this, inbound QoS markings are not trusted 

*Tail Drops:* Occurs when a packet is dropped because a queue is full 

*Policing:* Imposes an artificial ceiling on the amount of bandwidth that may be consumed; traffic exceeding the policer rate is reclassified or dropped

*Shaping:* Similar to policing but buffers excess traffic for delayed transmission; makes more efficient use of bandwidth but introduces a delay

*TCP Synchronization:* Flows adjust TCP windows sizes in sync, making inefficient use of a link


##### Congestion Avoidance

**(RED) Random Early Detection**
Packets are randomly dropped before a queue is full to prevent tail drop; mitigates TCP synchronization

**(WRED) Weighted RED**
RED with the added capability of recognizing prioritized traffic based on its marking 

**(CBWRED) Class-Based WRED**
WRED employed inside a class-based WFQ queue

##### DSCP Per-Hop Behaviour

**Class Selector (CS)** - Backward-compatible with IP precedence values
**Assured Forwarding (AF)** - Four classes with variable drop preferences
**Expedited Forwarding (EF)** - Priority queuing for delay-sensitive traffic

##### Types of queuing:

*First in First out (FIFO):* 
* Packets are transmitted in the order they are processed
* No prioritization is provided
* Default queuing method on high speed interfaces 
* Configurable with the tx-ring-limit interface config command 

*Priority queuing (PQ):*
* Provides four static queues which cannot be reconfigured
* Higher priority queues are always emptied before lower priority queues
* Lower-priority queues are at risk of bandwidth starvation 

*Custom Queuing (CQ):*
* Rotates through queues using Weighted Round Robin (WRR)
* Processes a configurable number of bytes from each queue per turn 
* Prevents queue starvation but does not provide for delay-sensitive traffic 

*Weighted Fair Queuing (WFQ):*
* Queues are dynamically created per flow to ensure fair processing
* Statistically drops packets from aggressive flows more often
* No support for delay-sensitive traffic

*Class-Based WFQ (CBWFQ):*
* WFQ with administratively configured queues 
* Each queue is allocated an amount/percentage of bandwidth
* No support for delay-sensitive traffic 

*Low Latency Queuing (LLQ):*
* CBWFQ with the addition of a policed strict-priority queue
* Highly configurable while still supporting delay-sensitive traffic 

