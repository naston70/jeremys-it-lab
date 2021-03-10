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
