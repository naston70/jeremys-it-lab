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


