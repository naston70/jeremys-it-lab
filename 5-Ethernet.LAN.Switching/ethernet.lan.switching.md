# Ethernet Frame


How an Ethernet frame looks: 

|Eth header|			Packet		 |Eth trailer|


Within the Ethernet Header:

Preamble|SFD|Destination|Source|Type

The Ethernet trailer only contains an FCS


### Preamble and SFD

**Preamble:**

7 bytes
Alternating 1's and 0's
Allows devices to sync their receiver clocks

**SFD:**
Start Frame Delimiter
1 byte length
Marks the end of the preamble, and beginning of the rest of the frame

The next to fields of the Ethernet header are:

### Destination and Source

**Destination:**

Indicates the devices sending and receiving the frame
Consists of the destination and source MAC address
'MAC' = Media Access Control
= 6 bytes or 48-bits address

### Type / Length
2 byte (16-bit) field

* A value of 1500 or less indicates the length of the encapsulated packet
* A value of **1536 or greater** in this field indicates the TYPE of the encapsulated packet (usually IPv4 or IPv6), and the length is determined via other methods
* IPv4 = 0x0800 in hex or 2048 in decimal
* IPv6 = 0x86DD in hex or 34525 in decimal

### FCS - Frame Check Sequence
* 4 bytes in length
* Detects corrupted data by running a 'CRC' algorithm over the received data
* CRC 'Cyclic Redundancy Check'


Preamble|SFD|Destination|Source|Type| PACKET |Trailer|
   |	  |       |         |     |				 |
   7      1       6         6     2				 4

Total of 26 bytes for header + trailer
