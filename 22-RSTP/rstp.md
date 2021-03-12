# RSTP - Rapid Spanning Tree Protocol

Rapid spanning tree improves the up to 50 seconds in can take for regular STP to converge.

802.1D users timers to move to a forwarding state, the heart of the new protocol is a new bridge-bridge handshke mechanism which allows ports to move directly to forwarding. 

#### Similarities between STP and RSTP

- RSTP serves the same purpose as STP, blocking specific ports to prevent Layer 2 loops
- RSTP elects a root bridge with the same rules as STP
- RSTP elects root ports with the same rules as STP
- RTSP elects designated ports with the same rules as STP