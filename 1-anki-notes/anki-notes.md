# Notes from Jeremy's IT Lab Anki flashcards and Wendell Odom CCNA 201-300

### Interfaces and Cables
* 1000BASE-T  = 802.3ab
* 100BASE-T   = 802.3u
* 1000BASE-LX = 802.3z
* 10GBASE-SR,LR and ER defined in 802.3ae
* 10GBASE-ER max cable length = 30 kms
* 10GBASE-SR max cable length = 400 meters
* Switch receives on pins: 1 & 2
* Switch transmits on pins 3 & 6

### OSI Model
Which layer provides node to node connectivity: Layer 2 data link

### Intro CLI
What is the lowest-level mode in Cisco IOS - user EXEC mode

### Ethernet LAN Switching
* Ethernet header 'Type/Length' 		= 2 bytes
* Ethernet header 'Preamble'    		= 7 bytes
* Ethernet header 'SFD'					= 1 byte
* Ethernet trailer 'FCS'				= 4 bytes
* Size of the Ethernet header + trailer = 26 bytes

### IPv4 Addressing
- What is the minimum size of an Ethernet frame? (Header + Payload + Trailer) = **46 bytes**
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
- The 'Protocol' field 				  = 8 bits
- The 'Fragment Offset' field length  = 13 bits
- IPv4 header 'Checksum' field length = 16 bits
- DSCP field 						  = 6 bits
- IHL field 						  = 4 bits
- ECN field 						  = 2 bits
- IHL field (Internet Header Length) Max value =  15


- Which field is used to check for errors in the header? = Header Checksum

- IHL = Indicates the number of 4-byte blocks in the IPv4 header. The size of this field is 4 bits. Because an IPv4 header is a minimum of 20 bytes in size, the smallest value of the Internet Header Length (IHL) field is 5. IPv4 options can extend the minimum IPv4 header size in increments of 4 bytes. If an IPv4 option does not use all 4 bytes of the IPv4 option field, the remaining bytes are padded with 0’s, making the entire IPv4 header an integral number of 32-bits (4 bytes). With a maximum value of 0xF, the maximum size of the IPv4 header including options is 60 bytes (15´4).
- Which field is used to prioritize delay-sensitive network traffic? = DSCP


### Static Routing
- End host forwarding a packet to a dst in a different network will forward the packet to its: **DEFAULT GATEWAY**


### Subnetting Part 1


# Wendell Odoms CCNA 200 - 301 (Flashcard Notes
#### chapter 1 - TCP/IP
- Telnet port : TCP/23

#### chapter 8 - dhcp snooping and arp inspection
- Verify dynamic arp inspection status - show ip arp inspection
- Modify the rate limit settings for DAI? ip arp inspection limit rate pps [burst interval seconds]

#### chapter 11 - QoS
- What is CAC? :  Call Admission Control (used to limit calls on a network)
- 

#### chapter 13 - LAN Architecture
- Job of distribution layer switches - interconnect access layer switches

#### chapter 14 - WAN Architecture
- Cisco VPN - The Cisco AnyConnect Secure Mobility Client


#### chapter 17 - SDA
- Whats considered the fabric in an SDA setup? The combination of the overlay and underlay to deliver data across the network

#### chapter 19 - OSPF concepts
- Administrative distance for EIGRP - 90
- What are OSPF messages called that send LSA's? - LSU Link State Updates


Definition of convergence: The process of bringing a network to a stable state where each router has an up to date view of the topology
Whats an Ethernet LAN (E-LAN) service? - A WAN service that acts like a LAn, in that all devices can send frames to all other devices
MIC - Message Integrity Check
Name three different FHRP's (First Hop Redundancy Protocols):
	- HSRP - Hot Standby Router Protocol
	- VRRP - Virtual Router Redundancy Protocol
	- GLBP - Gateway Load Balancing Protocol
- Protocol and port number of CAPWAP - UDP 5247
- **inside global** : A public address that represents one or more local addresses to the outside world

- Verify DHCP snooping status: **show ip dhcp snooping**

- How do you configure PAT for an interface address ```#ip nat inside source list *acl* interface *interface* overload```
- Multiple APs interconnected by a switched infrastructure? - An extended service set ESS
- Cisco DNA - Digital Network Architecture
- Administrative distance for eBGP  - 20

- Routes from one routing protocol injected into another routing protocol - route redistribution
- Diff between WLC ports and interfaces - Ports are physical wired connections whereas interface are logical connections
- Purpose of Class Selector values (CS) - To support backward compatibility with network devices that still use the Precedence field.
- Config new standard for STP interface cost: spanning-tree pathcost method 
- Explain Ansible playbooks -  YAML files which contain logic and actions Ansible should execute on the target machine
