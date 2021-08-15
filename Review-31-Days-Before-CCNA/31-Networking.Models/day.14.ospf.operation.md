## OSPF Operation

Exam Topics
- Determine how a router makes a forwarding decision by default
- Configure and verify single-area OSPFv2

#### Single-Area OSPF Operation 

The IETF chose OSPF over IS-IS as its recommended IGP. In 1998 OSPFv2 was updated. IOS chooses OSPF routes over RIP routes as OSPF AD is 110 and RIPs is 120

#### OSPF Message Format

The data portion of an OSPF message is encapsulated in a packet. This data field can include one of five OSPF packet types. 
The OSPF packet header is included with every OSPF packet, regardless of its type. The OSPF packet header and packet type-specific data are then encapsulated in an IP packet. In the IP packet header, the protocol field is set to 89 to indicate OSPF and the destination address is typically set to one of two multicast addresses. 224.0.05 or 224.0.0.6. 

If the OSPF packet is encapsulated in an Ethernet frame, the destination MAC address is also a multicast address

#### OSPF Packet Types