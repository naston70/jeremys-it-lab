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

Several varieties of STP emerged after the original IEEE 802.1D;

- **STP**: the original specification of STP, defined in 802.1D, provides a loop-free topology in a network with redundant links. STP is sometimes referred to as Common Spanning Tree (CST) because it assumes one spanning tree instance for the entire bridged network, regardless of the number of VLANs.

- **PVST+**: Per VLAN Spanning Tree Plus (PVST+) is a Cisco enhancement of STP that provides a seperate 802.1D spanning tree for each VLAN configured in the network

- **RSTP**: Rapid STP or IEEE 802.1w, is an evolution of STP that provides faster convergence than STP. However, RSTP still provides for only a single instance of STP 

- **Rapid PVST+**: Rapid PVST+ is a Cisco enhancement of RSTP that uses PVST+. Rapid PVST+ provides a seperate instance of 802.1w per VLAN

- **MSTP and MST**: Multiple Spanning Tree Protocol is an IEEE standard inspired by the earlier Cisco MISTP (Multiple Instance). MSTP maps multiple VLANs into the same spanning tree instance. The Cisco implementation of MSTP is Multiple Spanning Tree, which provides up to 16 instances of RSTP and combines many VLANs with the same physical and logical topology into a common RSTP instance. 

###### Features of STP Varieties

| Protocol | Standard      | Resources      | Convergence | Tree         |
|----------|---------------|----------------|-------------|--------------|
|          |               |                |             |              |
| STP      | 802.1D        | Low            | Slow        | All VLANs    |
| PVST+    | Cisco         | High           | Slow        | Per VLAN     |
| RSTP     | 802.1w        | Medium         | Fast        | All          |
| R PVST+  | Cisco         | Very High      | Fast        | Per VLAN     |
| MSTP     | 802.1w/ Cisco | Medium or High | Fast        | Per Instance |

## PVST Operation 

PVST Plus (PVST+) is the default setting on all Cisco Catalyst switches. In a PVST+ environment, you can tune the spanning-tree parameters so that half the VLANs forward on each uplink trunk. You do this by configuring one switch to be elected the root bridge for half of the VLANs in the network and a second switch to be elected the root bridge for the other half of the VLANs.

Switched networks running PVST+ have the following characteristics:
* Configured PVST per VLAN allows redundant links to be fully utilized
* Each additional spanning tree instance for a VLAN adds more CPU cycles to all switches in the network 

#### Port States

The SPanning Tree is determined immediately after a switch is finished booting. If a switch port transitions directly from the blocking state to the forwarding state without information about the full topology during the transition, the port can temporarily create a data loop. 

#### Extended System ID

PVST+ requires a seperate instance of spanning tree for each VLAN. The BID field in the BPDU must carry VLAN ID information. The BID includes the following fields:

- **Bridge Priority:** A 4-bit field is still used to carry bridge priority: However the priority is conveyed in discrete values in increments of 4096 instead of discrete values in increments of 1 because only the first 4 most significant bits are available from the 16-bit field.
- **Extended System ID:** A 12-it field carrying the VID for PVST+
- **MAC Address:** A 6-byte field with the MAC address of a single switch.

## Rapid PVST+ Operation

In Rapid PVST+, a single instance of RSTP runs for each VLAN. This is why Rapid PVST+ has a very high demand for switch resources.

With RSTP, the IEEE improved the convergence performance of STP from 50 seconds to less than 10 with RSTP 802.1w 
RSTP is identical to STP in the following ways:

- It elects the root switch by using the same parameters and tiebreakers
- It elects the root port on nonroot switches by using the same rules.
- It elects designated ports on each LAN segment by using the same rules
- It places each port in either forwarding or discarding state, although RSTP calls the blocking state 

#### RSTP Interface Behaviour

The main changes with RTSP can be seen when changed occur in the network. RSTP acts differently on some interfaces based on what is connected to the interface. 

* Edge-type behaviour and PortFast: RSTP improves convergence for edge type connections by immediately placing the port in forwarding state hen the link is physically active 
* Link-type shared: RSTP does not do anything differently from STP on link-type shared links. However, because most links between switches today are full duplex, point-to-point and not shared this does not matter. 
* Link-type point-to-point: RSTP improves convergence over full duplex links between switches. RSTP recognizes the loss of the path to the root bridge through the root port in 6 seconds (based on three times the hello value of 2 seconds). RSTP thus recognizes a lost path to the root much more quickly.

#### RSTP and STP Port States Table

| State    | 802.1D State | 802.1w State | Forwards? |
|----------|--------------|--------------|-----------|
|          |              |              |           |
| Enabled  | Blocking     | Discarding   | No        |
| Enabled  | Listening    | Discarding   | No        |
| Enabled  | Learning     | Learning     | No        |
| Enabled  | Forwarding   | Forwarding   | Yes       |
| Disabled | Discarding   | Discarding   | No        |


RSTP removes the need for the listening state and reduces the time required for learning state by actively discovering the networks new state. STP passively waits on new BPDUs and reacts to them during the listening and learning states. With RSTP, the switches negotiates with neighboring switches by sending RSTP messages. The messages enable the switches to quickly determine whether an interface can be immediately transitioned to  forwarding state.

#### RSTP Port Roles

**Root Port:** A single port on each nonroot switch in which the switch hears the best BPDU out of all the received BPDUs

**Designated Port:** Of all switch ports on all switches attached to the same segment, the port that advertises the 'best' BPDU

**Alternate Port:** A port on a switch that receives a suboptimal BPDU

**Backup Port:** A non-designated port on a switch that is attached to the same segment as another port on the same switch.

**Disabled:** A port that is administratively disabled or that is not capable of working for other reasons

#### Edge Ports
In addition to the previous port roles, RSTP uses an edge port concept that corresponds to the PVST+ Portfast feature. An edge port connects directly to an end device. Therefore, the switch assumes that no other switch is connected to it. RSTP ports should immediately transition to the forwarding state, thereby skipping the time consuming 802.!D listening and learning port states. The only caveat is the port must be a point-to-point link. 

## Configuring and Verifying Varieties of STP 

By default all Cisco switches use STP without any config. However because STP runs on a per-VLAN basis, several options can be used to load balance traffic across redundant links. 

#### STP Configuration Overview

Before configuring or altering the behaviour of STP it is important to know the current default settings 

| Feature                     | Default Setting                                         |
|-----------------------------|---------------------------------------------------------|
|                             |                                                         |
| Enable State                | Enables STP on VLAN 1                                   |
| Spanning tree mode          | PVST+                                                   |
| Switch Priority             | 32768                                                   |
| Spanning tree port priority | 128                                                     |
| Spanning tree port cos      | 1 Gbps = 4 100 Mbps = 19 10 Mbps = 100                  |
| Spanning tree timers        | hello 2 seconds forward delay 15 secs MaxAge 20 seconds |

#### Configuring and Verifying the BID

Regardless of which PVST used, two main configuration options can help cheive load balancing: the bridge ID and the port cost manipulation. The bridge ID influences the choice of root switch and can be configured per VLAN. Each interfaces STP cost to reach the root influences the choice of designated port on each LAN segment. Because PVST requires that a seperate instance of spanning tree run for each VLAN, the BID field is required to carry VLAN information. This is accomplished by reusing a portion of the Priority field as the extended system ID to carry a VID.
To change the bridge ID, use the following:

```
Switch(config)# spanning-tree vlan vlan-id root {primary | secondary}
Switch(config)# spanning-tree vlan vlan-id priority *priority
```

To change the interface cost:
```
Switch(config-if)# spanning-tree vlan vlan-id cost cost
```

#### STP Topology

(3 switch example S1-S2-S3)
Network administrator wants S1 as root bridge and S2 as backup root bridge

```
S1(config)#spanning-tree vlan 1 root primary
```

```
S2(config)#spanning-tree vlan 1 root secondary
```

The **primary** keyword automatically sets the the priority to 24576 or to the next 4096 increment value below the lowest bridge priority detected on the network.

The **secondary** keyword automatically sets the priority to 28672, assuming that the rest of the network is set to the default 32768.

Alternatively, the network administrator can explicitly configure the priority value in increments of 4096 between 0 and 65536 using the following command:

```
S1(config)# spanning-tree vlan 1 priority 24576
```

```
S2(config)# spanning-tree vlan 1 priority 28672
```

To verify the current spanning tree instances and root bridges, use the ```show spanning-tree``` command

#### Configuring PortFast and BPDU Guard

To speed convergence for access ports when they become active, you can use Cisco's proprietary PortFast technology. After a PortFast is configured and a port is activated, the port immediately transitions from the blocking to forwarding state

In a valid PortFast configuration, BPDUs should never be received because receipt of a BPDU indicates that another bridge or switch is connected to the port, potentially causing a spanning tree lop. When it is enabled, BPDU guard puts the port in an errdisabled state upon receipt of a BPDU. The BPDU Guard provides a secure response to invalid configurations because you must manually put the interface back into service.

#### Configuring Rapid PVST+

PVST+ is the default operation of Cisco switches. To change to Rapid PVST+ us a single global command on all switches:
```
spanning-tree mode rapid-pvst
```

