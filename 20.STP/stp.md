# Spanning Tree Protocol

Layer 2 Protocol

#### Network Redundancy

- Redundancy is an essential part of network design
- Modern networks are expected to run 24/7/365
- If one network component fails, you must ensure that other components will take over with little or no downtime
- As much as possible, redundancy must be implemented at every possible point in the network

STP helps to stop broadcast storms caused by switches flooding broadcast frames in a loop. Network congestion isn't the only problem. Each time a frame arrives on a switchport, the switch uses the source MAC address field to 'learn' the MAC address and update its MAC address table. When frames with the same source MAC address repeatedly arrive on different interfaces, the switch is continuously updating the interface in its MAC address table. This is known as **MAC Address Flapping.**

#### Spanning Tree Protocol

- 'Classic Spanning Tree Protocol' is IEEE 802.1D
- Switches from all vendors run STP by default
- STP prevents Layer 2 loops by placing redundant ports in a blocking state, essentially disabling the interface
- These interfaces act as backups that can enter a forwarding state if an active (currently forwarding) interface fails
- Interfaces in a forwarding state behave normally. They send and receive all normal traffic.
- Interfaces in a blocking state only send or receive STP messages - (BPDU's) Bridge Protocol Data Units

* By selecting which ports are forwarding and which ports are blocking, STP creates a single path to/from each point in the network. This prevents Layer 2 loops.
* There is a set process that STP uses to determine which ports should be forwarding and which should be blocking
* STP-enabled switches send/receive Hello BPDU's out all interface, the default timer is 2 secs
* If a switch receives a Hello BPDU on an interface, it knows that interface is connected to another switch (routers,pc's etc do not use STP)

- Switches use one field in the STP BPDU, the **Bridge ID** field, to elect a **root bridge** for the network
- The switch with the lowest **Bridge ID** becomes the **root bridge**
- ALL ports on the root bridge are put in a forwarding state and the other switches in the topology must have a path to reach the root bridges

The Bridge ID used to be used to decide root bridge:
	| Bridge Priority (16 bit)   |  MAC Address (48 bits) |

Which was then extended to use the Extended System ID (VLAN ID)

	| Bridge   | Extended System ID (VLAN ID)|      MAC Address (48 bits)       |
	  Priority      
	|  4 bits  |			12 bits			 |									|

Why include the VLAN ID? Cisco switches use a version of STP called PVST (per vlan spanning tree). PVST runs a seperate STP instance in each VLAN, so in each VLAN different interfaces can be forwarding /blocking

If you need to change the switches priority (without changing VLAN numbers), what is the minimum unit of increase/decrease?

The extended system ID is a single field of the bridge ID, however the extended system id is set and cannot be changed - as it is determined by the VLAN ID. Therefore you can only change the total bridge priority in units of 4096, the value of the least significant bit of the bridge priority.

Designated Ports:
All interfaces on the root bridge are **designated ports.** Designated ports are in a forwarding state.

* When a switch is powered on, it assumes it is the root bridge
* It will only give up its position if it receives a 'superior' BPDU (lower bridge ID)
* Once the topology has converged and all switches agree on the root bridge, only the root bridge sends BPDUs
* Other switches in the network will forward these BPDUs but will not generate their own original BPDUs


## The Spanning Tree Process

1) The switch with the lowest bridge ID is elected as the root bridge. All ports on the root bridge are **designated ports** (forwarding state)

2) Each remaining switch will select ONE of its interfaces to be its **root port**. (forwarding state) The interface with the lowest root cost will be the root port. Root ports are also in a forwarding state. Ports across from the root port are always **designated ports**
Root Port Selection:
1: Lowest root cost
2: Lowest neighbour bridge ID
3: Lowest neighbour Port ID

The NEIGHBOUR switch's port ID is used to tie-break, not the local switch's port ID

STP COSTS:

SPEED 	 |	STP-COST

10 Mbps		100
100 Mbps	19
1 Gbps		4
10 Gbps		2

Every collision domain has a single STP designated port

3) Each remaining collision domain will select ONE interface to be a **designated port** (forwarding state). The other port in the collision domain will be **non-designated** (blocking)
Designated port selection:
1: Interface on switch with lowest root cost
2: Interface on switch with lowest bridge ID
