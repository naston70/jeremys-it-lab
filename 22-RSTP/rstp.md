# RSTP - Rapid Spanning Tree Protocol

Rapid spanning tree improves the up to 50 seconds in can take for regular STP to converge.

802.1D users timers to move to a forwarding state, the heart of the new protocol is a new bridge-bridge handshke mechanism which allows ports to move directly to forwarding. 

#### Similarities between STP and RSTP

- RSTP serves the same purpose as STP, blocking specific ports to prevent Layer 2 loops
- RSTP elects a root bridge with the same rules as STP
- RSTP elects root ports with the same rules as STP
- RTSP elects designated ports with the same rules as STP

#### RSTP Port States

| STP Port State | SEND/RECEIVE BPDUs | Frame Forwarding | Mac Learning | Stable / Transitional |
|----------------|--------------------|------------------|--------------|-----------------------|
| Discarding     | NO/YES             | NO               | NO           | STABLE                |
| Learning       | YES/YES            | NO               | YES          | TRANSITIONAL          |
| Forwarding     | YES/YES            | YES              | YES          | STABLE                |

#### Port Roles

The **root port** role remains unchanged in RSTP.
	- The port that is closest to the root bridge becomes the root port for the switch
	- The root bridge is the only switch that doesn't have a root port

The **designated port** role remains unchnaged in RSTP.
	- The port on a segment (collision domain) that sends the best BPDU is that segments designated port (one per segment)

The **non-designated port** role is split into two seperate roles in RSTP:
	* the **alternate port** role &
	* the **backup port** role


###### alternate port role
* The RSTP **alternate** port role is a discarding port that receives a superior BPDU from another switch.
* The same as **blocking ports*** in STP.
* It functions as a backup to the root port
* If the root port fails, the switch can immediately move its best alternate port to forwarding	
* These are the features of UplinkFast, that are now built in to RSTP.
- **BackboneFast** is also built into RSTP, which allows a switch to expire the max age timers on its interface and rapidly forward superior BPDUs when an interface fails and a switch may begin to send its own BPDUs mistakenly assuming it is now root bridge.

###### backup port role
* RSTP backup port role is a discarding port that receives a superior BPDU form another interface on the same switch
* This only happens when two interfaces are connected to the same collsion domain (via a hub)
* Hubs arent used in modern networks so should not be encountered
