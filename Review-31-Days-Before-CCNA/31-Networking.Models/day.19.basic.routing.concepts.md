## Basic Routing Concepts

Exam Topics:

- Explain the role and function of network components
- Determine how a router makes a forwarding decision by default

#### Packet Forwarding

Packet forwarding by routers is accomplished through path determination and switching functions. The path determination function is the process the router uses to determine which path to use when forwarding a packet. To determine the best path, the router searches its routing table for a network address that matches the packets destination IP address.

This search results in one of three path determinations:

- **Directly connected network:** If the destination IP address of the packet belongs to a device on a network that is directly connected to one of the routers interfaces, the packet is forwarded directly to that device. This means the destination IP address of the packet is a host address on the same network as this routers interface
- **Remote network:** If the destination IP address of the packet belongs to a remote network, the packet is forwarded to another router. Remote networks can be reached only by forwarding packets to another router. 
- **No route determined:** If the destination IP address of the packet does not belong to a connected or remote network and the router does not have a default route, the packet is discarded. The router sends an ICMP Unreachable messages  to the source IP of the packet.

In the first two result, the router completes the process by switching the packet out the correct interface. It does this by reencapsulating the IP packet into the appropriate Layer 2 data-link frame format for the exit interface. This type of interface determines the type of Layer 2 encapsulation. ie if the exit interface is Fast Ethernet, the packet is encapsulated in an Ethernet frame. If the exit interface is a serial interface configured for PPP, the IP packet is encapsulated in a PPP frame.

## Routing Methods


