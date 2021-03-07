# Notes from Jeremy's IT Lab Anki flashcards and Wendell Odom CCNA 201-300

### Ethernet LAN Switching
* Ethernet header 'Type/Length' 		= 2 bytes
* Ethernet header 'Preamble'    		= 7 bytes
* Ethernet header 'SFD'					= 1 byte
* Ethernet trailer 'FCS'				= 4 bytes
* Size of the Ethernet header + trailer = 18 bytes

### IPv4 Addressing
- What is the minimum size of an Ethernet frame? (Header + Payload + Trailer) = **64 bytes**
- What is the minimum size of an Ethernet Payload? = 46 bytes
- The 'Status' field of the ```show ip interface brief```command is LAYER 1
- Class C contains 2,097,152 networks


### Switch Interfaces
* CSMA-CD means Carrier Sense Multiple Access with Collision Detection
* Are all devices connected to an Ethernet switch in the same collision domain? 
	No -  every port on a bridge, switch, or a router is in a separate collision domain. This eliminates the possibility of collisions and enables the devices to use the full-duplex mode of communication, which effectively doubles the maximum data capacity.

### IPv4 Header
Minimum length of 'Total Length' field = 20 (which is a header with no data) max = 65535
Maximum length of IPv4 header = 60 bytes
Recommended default TTL = 64
- The 'Identification' field length   = 16 bits
- The 'Fragment Offset' field length  = 13 bits
- IPv4 header 'Checksum' field length = 16 bits
- DSCP field 						  = 6 bits
- IHL field (Internet Header Length) Max value =  15


- Which field is used to check for errors in the header? = Header Checksum

- IHL = Indicates the number of 4-byte blocks in the IPv4 header. The size of this field is 4 bits. Because an IPv4 header is a minimum of 20 bytes in size, the smallest value of the Internet Header Length (IHL) field is 5. IPv4 options can extend the minimum IPv4 header size in increments of 4 bytes. If an IPv4 option does not use all 4 bytes of the IPv4 option field, the remaining bytes are padded with 0’s, making the entire IPv4 header an integral number of 32-bits (4 bytes). With a maximum value of 0xF, the maximum size of the IPv4 header including options is 60 bytes (15´4).
- Which field is used to prioritize delay-sensitive network traffic? = DSCP


### Static Routing
- End host forwarding a packet to a dst in a different network will forward the packet to its: **DEFAULT GATEWAY**


### Subnetting Part 1
