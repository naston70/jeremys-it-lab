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

##### Internet Header Length (IHL)
	- The final field of the IPv4 header (options) is variable in length, so this field is required to indicate the total length of the header
	- Identifies the length of the header in 4-byte increments 
	- Ie: A value of 5 = 5 * 4 = 20 bytes length of the header
    - Min value = 5
    - Max value = 15
    - MINIMUM IPv4 HEADER LENGTH = 20 BYTES
    - MAXIMUM IPV4 HEADER LENGTH = 60 BYTES

##### DSCP 
	- Differentiated Service Code Point
	- Used for QoS
	- Used to prioritize delay-sensitive data (voice, video etc)


##### ECN Field
	- Explicit Congestion Notification
	- Provides end to end notification of network congestion without dropping packets.
	- Optional feature that requires both endpoints, as well as the underlying network infrastructure to support it

##### Total Length
	- Indicates total length of the packet
	- Measured in bytes