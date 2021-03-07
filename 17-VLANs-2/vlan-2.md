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

#### Native VLAN

802.1q has a feature called the **native vlan**

The native vlan is vlan 1 by default on all trunk ports, but can be manually configured on each trunk port

The switch does not add an 802.1q tag to frames in the native vlan

When a switch receives an untagged frame on a trunk port it assumes the frame belongs to the native VLAN - **it is very important that the native vlan matches**

For security purposes, it is best to change the native VLAN to an **unused VLAN**

The ```show vlan brief```command shows the access ports assigned to each VLAN NOT the trunk ports that allow each VLAN

The ```show interface trunk``` command is used to confirm trunk ports

#### Router on a Stick (ROAS)

The name used for this method of inter-vlan routing with only a single interface connecting the router and the switch. One interface can be seperated into seperate sub-interfaces 

Router configuration for ROAS:
(adding sub interfaces onto g0/0 for vlans 10,20 and 30)
```
R1(config-if)#interface g0/0.10
R1(config-subif)#ip address 192.168.1.62 255.255.255.192
R1(config-if)#interface g0/0.20
R1(config-subif)#ip address 192.168.1.126 255.255.255.192
R1(config-if)#interface g0/0.30
R1(config-subif)#ip address 192.168.1.190 255.255.255.192
```


