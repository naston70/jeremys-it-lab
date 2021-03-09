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