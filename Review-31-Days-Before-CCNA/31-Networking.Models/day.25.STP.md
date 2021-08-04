## STP

#### Exam Topics

- Configure, verify and troubleshoot STP
- Configure, verify and troubleshoot STP-related features
- Describe the benefits of switch stacking and chassis aggregation 

Original STP (802.1D) only allowed for one instance of STP to run for an entire network. Today, PVST - Per VLAN Spanning Tree and RSTP improve the standard.

#### STP Concepts and Operation

A key characteristic of a well-built communications network is resiliency. A resilient network is capable of handling a device or link failure through redundancy. A redundant topology can eliminate a single point of failure by using multiple links, multiple devices or both. STP helps prevent loops in a redundant switched network.

Without STP, redundancy in a network can introduce the following issues:

- Broadcast storms: Each switch floods broadcasts endlessly
- Multiple frame-transmission: Multiple copies of unicast frames are delivered to the destination, causing unrecoverable errors
- MAC data base instability: Instability in the content of the MAC table results from different ports of the switch receiving copies of the same frame

## STP Algorithm 

STP is an IEEE standard defined as 802.1D. STP places certain ports in the blocking state so they do not listen to, forward, or flood data frames. STP creates a tree that ensures that only one path exists for each network segment at any one time. If any segment experiences a disruption in connectivity, STP rebuilds a new tree by activating the previously inactive but redundant path.

The algorithm STP uses chooses the interfaces that should be placed into a forwarding state. For any interface not chosen to be in a forwarding state, STP places the interfaces in a blocking state.

Switches exchange STP configuration messages every 2 seconds, by default, using a multicast frame called the BPDU - Bridge Protocol Data Unit.Blocked ports listen for these BPDUs to detect whether the other side of the link is down, thus requiring an STP recalculation. One piece of information included in the BPDU is the Bridge ID or BID.

The BID is unique to each switch. It consists of a priority value (2 bytes) and the bridge MAC address (6 bytes). 
The default priority is 32,768. 
The root bridge is the bridge with the lowest BID. Therefore if the default priority is not changed, the switch with the lowest MAC address becomes root. 

#### STP Convergence

STP convergence is the process by which switches collectively realize that something has changed in the LAN topology. The switches determine whether they need to change which ports block and which port forward. The following steps summarize the STP algorithm used to achieve convergence

1. Elect a root bridge (Lowest BID). Only one root bridge can exist per network. All ports on the root bridge are forwarding

2. Elect a root port for each nonroot switch, based on the lowest root path cost. Each nonroot switch has one root port. The root port is the port through which the nonroot bridge has its best path to the root bridge

3. Elect a designated port for each segment, based on the lowest root port path cost. Each link has one designated port. 

4. The root ports and designated ports transition to the forwarding state, and the other ports stays in the blocking state. 

###### Reasons for Forwarding or Blocking 

**All the root switches ports:** Forwarding
* The root switch is always the designated switch on all connected segments

**Each nonroot switch's root port:** Forwarding
* This is the port through which the switch has the least cost to reach the root switch

**Each LANs designated port:** Forwarding
* The switch forwarding the lowest-cost BPDU onto the segment is the designated switch for that segment

**All other working ports:** Blocking
* The port is not used for forwarding frames, nor are any frames received on the interfaces considered for forwarding. BPDUs are still received.


Port bandwidth is used to determine the cost to reach the root bridge. 

###### Default IEEE Ports Costs

10 Mbps  = 100
100 Mbps = 10
1 Gbps   = 1
10 Gbps  = 1

###### Revised Port Costs

10 Mbps  = 100
100 Mbps = 19
1 Gbps   = 4
10 Gbps  = 2

STP uses four states as port transitions from blocking to forwarding.

###### STP port states

**Blocking:** Loss of BPDU detection - (Max Age = 20 sec)
**Listening:** (Forward delay = 15 sec) Moves to listening after it decides if it is a root port or designated port.
**Learning:** (forward delay = 15 sec)
**Forwarding**

A fifth state, disabled, occurs either when a network administrator disables the port or when a security violation occurs

## STP Varieties