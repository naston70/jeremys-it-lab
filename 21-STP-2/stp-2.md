# STP-2

#### Spanning Tree Port States

| STP Port State | Stable/Transitional |
|----------------|---------------------|
| Blocking       | Stable              |
| Listening      | Transitional        |
| Learning       | Transitional        |
| Forwarding     | Stable              |

* Root/ Designated ports remain stable in a Forwarding state
* Non-designated ports remain stable in a Blocking state
* Listening and Learning are transitional states which are passed through when an interface is activated, or when a Blocking port must transition to a forwarding state due to a change in the network topology


#### Blocking State

| STP Port State | Stable/Transitional |
|----------------|---------------------|
| Blocking       | Stable              |

- Non-designated ports are in a **Blocking** state
- Interfaces in a Blocking state are effectively disabled to prevent loops
- Interfaces in a Blocking state do not send/receive regular network traffic
- Interfaces in a Blocking state receive STP BPDUs (Bridge Protocol Data Unit)
- Interfaces in a Blocking state do not forward STP BPDUs
- Interfaces in a Blocking state do not learn MAC addresses

After the blocking state, interfaces with the Designated or Root role enter the **Listening** state.

#### Listening State

| STP Port State | Stable/Transitional |
|----------------|---------------------|
| Listening      | Transitional        |

- Only designated or root ports enter the listening state (non designated ports are always blocking)
- The listening state is 15 seconds long by default. This is determined by the Forward delay timer

* An interface in the Listening state ONLY forwards/receives STP BPDUs
* An interface in the Listening state does NOT send/receive regular traffic
* An interface in the Listening state does not learn MAC addresses from regular traffic that arrives on the interface


After the Listening state, a Designated or Root port will enter the Learning state.

#### Learning State

| STP Port State | Stable/Transitional |
|----------------|---------------------|
| Learning       | Transitional        |

- The Learning state is 15 seconds long by default. This is determined by the **Forward delay** timer.

* An interface in the Learning state ONLY sends/receives STP BPDUs
* An interface in the Learning state does not send/receive regular traffic
* An interface in the Learning state **LEARNS** MAC addresses from regular traffic that arrives on the interface.

Finally, Root and Designated ports are in a Forwarding state

#### Forwarding State

| STP Port State | Stable/Transitional |
|----------------|---------------------|
| Forwarding     | Stable              |

- A port in the Forwarding state operates as normal:
	* A port in the Forwarding state sends/receives BPDUs
	* A port in the Forwarding state sends/receives normal traffic
	* A port in the Forwarding state learns MAC addresses

| STP Port State | Send/Receive BPDU's | Frame  Forwarding | MAC  Learning | Stable/ Transitional |
|----------------|---------------------|-------------------|---------------|----------------------|
| Blocking       | NO/YES              | NO                | NO            | Stable               |
| Listening      | YES/YES             | NO                | NO            | Transitional         |
| Learning       | YES/YES             | NO                | YES           | Transitional         |
| Forwarding     | YES/YES             | YES               | YES           | Stable               |
| Disabled       | NO/NO               | NO                | NO            | Stable               |



## Spanning Tree Timers

Timers: 

Hello, Forward Delay and MAX Age. 2 seconds, 15 seconds and 20 seconds (2 * Hellos) in duration 

Purpose:

Hello: How often the root bridge sends HELLO BPDUs

Forward Delay: How long the switch will stay in the Listening and Learning states (Each state lasts 15 seconds so 30 in total)

MAX Age: How long an interface will wait after it ceases to receive Hello BPDUs to change the STP topology. 

##### Hello
When you turn on switches they all assume they are Root Bridge and send BPDUs, once fully converged only the Root Bridge continues to send BPDUs (Hellos). Then the other switches forward these BPDUs on their designated ports (not root or no designated ports). These messages are sent every 2 seconds.

##### Forward delay
This is the length of the listening and learning states. 

##### Max Age
If a port ceases to receive BPDUs:
	* If another BPDU is received before the max age timer counts down to 0, the time will reset to 20 seconds and no changes will occur
	* If another BPDU is not received, the max age timer counts down to 0 and the switch will reevaluate its STP choices, including root bridge, and local root, designated and non-designated ports
	* If a non-designated port is selected to become a designated or root port, it will transition from the blocking state to the listening state and finally to the forwarding state. So it can take a total of **50** seconds for a blocking interface to transition to forwarding. 20 Max Age + 15 + 15 = 50 secs
	* These timers and transitional states are to ensure that loops are not accidentally created by an interface moving to a forwarding state too quickly.
	* A forwarding state can move directly to a blocking state but a blocking interface cannot move directly to a forwarding state - it must go through listening and learning states

##### Trivia: PVST+ MAC used for BPDUs: 01:00:0c:cc:cc:cd | Regular STP uses 0180.c200.0000

### STP - Toolkit

Portfast:
	- Can be enabled on ports connected to end hosts
	- When there is no risk of causing a Layer 2 loop, Portfast enables quicker connectivity
	- Allows a port to move immediately to the Forwarding state
	- If enabled on a port connected to another switch it could cause a Layer 2 loop
	- enabled at the interface level

```
SW1(config-if)#spanning-tree portfast
%Warning (omitted)
SW1(config-if)
```

Spanning-tree can also be enabled on all access ports using:
```
SW1(config)# spanning-tree portfast default
```

To protect against the use of Portfast accidentally causing Layer 2 loops there is BPDU Guard:

BPDU Guard
	- If an interface with BPDU Guard enabled receives a BPDU from another switch, the interface will be shutdown to prevent a loop from forming

Configure at an interface level:
```
SW1(config-if)#spanning-tree bpduguard enable
SW1(config-if)
```

Or to enable globally on all Portfast enabled interfaces:

```
SW1(config)#spanning-tree portfast bpduguard default
SW1(config-if)
```

Root Guard - If enabled, **root guard**, even when the interface receives a superior BPDU will not accept the new switch as the root bridge. The interface will be disabled

Loop Guard - If enabled on an interface, even if the interface stops receiving BPDUs, it will not start forwarding. The interface will be disabled


#### Basic Spanning Tree Config

##### Selecting STP mode
```
SW1(config)#spanning tree mode ?
	mst 		 Multiple spanning tree mode
	pvst 		 Per-Vlan spanning tree mode
	rapid-pvst   Per-Vlan rapid spanning tree mode
```
##### Configuring the Primary Root Bridge
```
SW3(config)#spanning-tree vlan 1 root primary 
```

This command ```spanning-tree vlan vlan-number root primary sets the STP priority to 24576. If another switch already has a priority lower than 24576, it sets this switch's priority to 4096 less than the other switch's priority.

##### Configuring the Secondary Root Bridge
```
SW3(config)#spanning-tree vlan 1 root secondary
```

This command sets the STP priority to 28672


## STP Load Balancing

Spanning Tree load balancing requires two characteristics to be built into the network:
	* Multiple paths that form loops
	* Multiple VLANs

If the network doesn't contain loops, there cannot be multiple paths over which the load can be distributed. For example, if two switches only have one FastEthernet link between them, it is fairly difficult to do any load-balancing. This is couple with the desire/ requirement to have redundancy. Most networks should employ at least two links to meet reliability and availability requirements even if the bandwidth demands are low. However, after redundancy is added to a network or to the OLT/ Wiring closet, How are they made use of?
Load Balancing can provide redundancy and speed.

If loops do exist, the function of Spanning Tree is to remove them from the active topology, so how can multiple paths be used if Spanning Tree prunes the network back to a single set of paths connecting every location to every other location. 

This is where VLANs make it possible to create multiple Spanning Tree domains over a single physical infrastructure. Meaning one Spanning Tree domain can become multiple domains via the use of VLANs.
By designing different different active topologies on a per VLAN basis, multiple paths can be utilized. Within a single VLAn, the traffic is loop free and only utilizes a single path to each destination, two VLANs can use both redundant links that are still installed to the OLT/ wiring closet