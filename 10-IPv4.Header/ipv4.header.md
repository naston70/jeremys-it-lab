# IPv4 Headers

Review

Layer 2 PDU     ----> Frame
Layer 3 PDU     ----> Packet
Layer 4 PDU     ----> Segment
Upper Layer PDU ----> Data

#### Fields of the IPv4 Header

###### Version Field
	- Identifies the version of IP used
	- IPv4 = 4 (0100)
	- IPv6 = 6 (0110)

##### Internet Header Length (IHL) - 4 bits
	- The final field of the IPv4 header (options) is variable in length, so this field is required to indicate the total length of the header
	- Identifies the length of the header in 4-byte increments 
	- Ie: A value of 5 = 5 * 4 = 20 bytes length of the header
    - Min value = 5
    - Max value = 15
    - MINIMUM IPv4 HEADER LENGTH = 20 BYTES
    - MAXIMUM IPV4 HEADER LENGTH = 60 BYTES

##### DSCP - 6 Bits
	- Differentiated Service Code Point
	- Used for QoS
	- Used to prioritize delay-sensitive data (voice, video etc)


##### ECN - 2 bits
	- Explicit Congestion Notification
	- Provides end to end notification of network congestion without dropping packets.
	- Optional feature that requires both endpoints, as well as the underlying network infrastructure to support it

##### Total Length - 16 bits
	- Indicates total length of the packet
	- Measured in bytes
    

##### Identification Field
	- If a packet is fragmented due to being too large, this field is used to identify which packet the fragment belongs to.
	- All fragments of the same packet will have their own IPv4 header with the same value in this field
	- Packets are fragmented if larger than the MTU (Maximum Transmission Unit)
    - Usually 1500 bytes

##### Flags Field
	- Used to control/ identify fragments
	- Bit 0: Reserved, always set to 0
	- Bit 1: Dont Fragment (DF bit) used to indicate a packet that should not be fragmented
	- Bit 2: More Fragments (MF bit) set to 1 if there are more fragments in the ppacket

##### Fragment Offset Field
	- Used to indicate the position of the fragment within the orginal, unfragmented IP packet
	- Allows fragmented packets to be reassembled

##### TTL
	- A router will drop a packet with a TTL of 0
	- Used to prevent loops
	- Originally designed to indicate the packets max lifetime in seconds
	- In practice indicates a 'hop count' each time the packet arrives at a router the router decreases TTL by 1

##### Protocol
	- Indicates the protocol of the encapsulated L4PDU
	- Value of 6: TCP
	- VAlue of 17: UDP
	- Value of 1: ICMP
	- Value of 89: OSPF

##### Header Checksum
	- Calculated checksum used to check for errors in the header
	- When a router receives a packet it calculates the checksum of the header and compares it to the one in this field of the header
	- If they do not match the router drops the packet
	- Only checks for error in the HEADER

##### Source IP / Destination IP
	- 32 bits in length
	- Source = Sender
	- Destination =  Receiver

##### Options
	- Optional
	- Rarely used
	- If the IHL field is greater than 5 it means the options are present


