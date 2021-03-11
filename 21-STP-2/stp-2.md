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
- Interfaces in a Blocking state receive STP BPDUs
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



