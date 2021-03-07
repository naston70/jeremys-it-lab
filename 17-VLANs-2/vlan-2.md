# VLANs Part 2

### Trunk Ports

In small networks it is possible to use a seperate interface for each VLAN, however when the number of VLANs increases, this is not viable - wasted interfaces and often not enough.

Trunk ports can be used to carry traffic from multiple VLANs over a single interface.

Switches know which VLANs traffic belongs to as switches 'tag' all frames they send over a trunk link. This allows the receiving switch to know which VLAN the frame belongs to.

Trunk ports are also known as tagged ports and access ports as untagged.

### VLAN tagging

There are two main trunking protocols: 
	- ISL Inter Switch Link &
	- IEEE 802.1Q (dot1q)

ISL is an old proprietary protocol create dbefore the industry standard dot1q
Dot1q is an industry standard protocol created by the IEEE.

The dot1q is inserted between the Source field and Type field in the Ethernet Header:

| preamble | sfd | destination | source | 802.1q | type |

* The tag is 4 bytes long (32 bits)
* The tag consists of two main fields:
	- Tag Protocol Identifier (TPID)
	- Tag Control Information (TCI)
* The TCI consists of three sub-fields

**TPID field:**
* 16 bits (2 bytes) in length
* Always set to a value of 0x8100. This indicates that the frame is 802.1q tagged
* It is placed in the header where the switch would usually have the Type field

**TCI:**

PCP - Priority Code Point
- 3 bits in length
- Used for Class of Service (CoS), which prioritizes important traffic in congested networks

DEI - Drop Eligible Indicator
- 1 bit in length
- Used to indicate frames that can be dropped if the network is congested

VID - VLAN ID
- 12 bits in length
- Identifies the VLAN the frame belongs to
- 12 bits in length (2**12) = 4096 total VLANs
- VLANs 0 and 4095 are reserved and cant be used

**802.1Q tag format**

|		     16 bits		|	3 bits	|1 bit|		12 bits		|
			TPID							TCI
							|   PCP		| DEI |		 VID        |

Tag protocol identifier (TPID) - A 16-bit field set to 0x8100 in order to identify the frame as 802.1q tagged.

Tag control information (TCI)  - A 16 bit field containing the above subfields


#### VLAN Ranges

The range of VLANs 1 - 4094 is divided into two sections:
	- Normal VLANs 1 - 1005
	- Extended VLANs 1006 - 4094
Some older devices cannot use the extended range however modern switches will

A switch will forward traffic in the same VLAN but not in a different VLAN
