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

