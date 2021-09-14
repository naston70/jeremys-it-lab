## CCNA Checklist Days 31-21 

## Create a diagram of the layered models

###### OSI Model 

**7. Application** - Network process to Application
**6. Presentation** - Data Representation and Encryption
**5. Session** - Interhost communication 
**4. Transport** - End to end communication and reliability
**3. Network** - Best path determination and IP addressing
**2. Data-Link** - MAC and LLC
**1. Physical** - Media, Signal and Binary Transmission 

###### TCP Model 
 
**Application** - (Application, Session, Transport)

**Transport** - Transport

**Internet** - Network 

**Network Access** - Network Access and Internet 

#### Describe details of sending an email from source to destination 

First the sender enters the email address of the recipient along with the message using an email application.
Then the 'send' button is clicked and the email goes to the Mail Transfer Agent (MTA) via the SMTP protocol. 

Next is the DNS lookup. The system sends a request to find out the corresponding MTA of the recipient with the help of the MX record. In the DNS zone for the receivers addresses domain, there will be an MX record (Mail Exchanger). This is a DNS resource record which specifies the mail server of a domain. So after the DNS lookup, a response is given to the requested mail server with the IP address of the recipients mail server.

The next step is the transfer of the message between mail severs. The STMP protocol is used for this communication. 

###### Protocols used for email service

POP3, IMAP and SMTP. SMTP is used to forward the email while the other two are used to retrieve email from an email server

IMAP uses port 143 and over SSL 993
POP3 uses port 110 and 995
SMTP uses 25, 2525 and 465


## Describe the CSMA/CD process

Carrier Sense Multiple Access with Collision Detection is a MAC method used notably in early Ethernet technology for LAN networking. It uses carrier sensing to defer transmissions until no other stations are transmitting. This is used in combination with collision detection in which a transmitting station detects collisions by sensing transmission from other stations while it is transmitting a frame. (wiki)

Half-Duplex networks use CSMA/CD, commonly in networks with repeaters and hub as all their ports are in the same collision domain. 

## Purpose of a MAC Address

Network functionality in the OSI model is subdivided into layers. MAC addresses function at the Data-Link Layer allowing computers/ NICs to identify themselves at this level. Also can be used in filtering and data recovery

## Describe structure and purpose of IPv4

The IPv4 packet is composed of a number of different fields that can be used by the source and intermediary devices to determine the way a specific packet us treated when being transported. These are the different fields within:

| Version 4 bits || IHL 4 bits || TOS 8 bits || Length 16 bits |
|Identification 16 bits| |Flags 4 bits| |Fragment Offset 12 bits|
| TTL 8 bits | | Protocol 8 bits | | Checksum 16 bits |
|Source Address 
|Destination address
| Options 24 bits | | Padding 8 bits |

###### Version Field

The version field is one of the fields with a more obvious name and uses 4 bits. There are currently two version of IP, 4 and 6. Version 4 packet version field is '0100' 6 is '0110'

###### Internet Header Length

The IHL field is used to specify the total length of the header and is represented in 32 bit words. The minimum value for the field is 5

###### Type of Service/DSCP/ECN 

When IP was initially designed this part of the packet header was called the Type of Service field that used 8 bits; this field was used to define a precedence value along with other quality of service parameters for the packet. The modern implementation has changed from using this part of the packet from a single 8-bit TOS field to a 6-bit DSCP and 2-bit ECN field. The DSCP field extends on the way that QoS is placed upon a specific packet. The ECN is used to provide end-to-end congestion notifications

###### Length

Unlike the IHL field, the Length field is used to indicate the total length of the IP packet including data. The

###### Identification

The Identification field uses 16 bits and is uniquely set by the sender to help identify specific packets when they are being reassembled from fragments. If these is only one packet and it is not fragmented then it will be the only packet with that specific identification value. For fragmented packets, the value is the same across all the fragments and is used by the destination device to reassemble the data

###### Flags

The Flags field is used to control how a specific IP packet is treated by a device. The field is 3 bits and is formatted as follows:
- First bit is always set to 0
- Second bit represents whether a packet is allowed to be fragmented
    * A value of 0 means it is allowed 
    * A value of 1 means it is NOT allowed to be fragmented
Third bit represents the location of a packet in a series of fragmented packets
    * 0 means the packet is the last fragment in a series OR is not fragmented
    * 1 means it is not the last and should expect more 

###### Fragment Offset

The Fragment Offset field uses 13 bits and is represented in octets. This field is used to indicate to the destination device where a received fragment should be placed when all of the data from the packets is being reassembled. The fragment offset, along with the identification field, is used to identify packets that have been fragmented and reassemble them in the correct order. Packets that are not fragmented and the first packet in a series of fragmented packets will always have a fragment offset set to 0 

###### TTL 

The TTL field is used to limit the amount of time that a packet is allowed to exist on the network. The field uses 8 bits and is represented in seconds. Each device decrements the TTL by 1 and any device which decrements to 0 is required to drop the packet. It is also common for TTL to be represented in hops

###### Protocol

The Protocol field uses 8 bits and indicates the next level protocol that is contained within the data portion of the packet. ie TCP, UDP, ICMP etc 

###### Checksum 

The Checksum field uses 16 bits and is computed for only the packet header. Checksum is recalculated at each device as the TTL changes 

###### Source and Destination Address 

32 bits representing the source and destination addresses

###### Options

The options field is variable in length depending on the specific options that are being set; the field is optional. 

###### Padding 

The Padding field is variable in length and is used when the Options field is used to ensure that the packet header ends at a 32 bit boundary

###### Data 

The Data field inside a packet is variable in length and can contain any number of different protocols - TCP, UDP etc 


## What is IPv4?

IPv4 works on the network layer of the TCP/IP stack. The main task of the protocol is to transfer data blocks from the sending host to a destination host where the senders and receivers are computers uniquely identified by IP addresses. 

#### What are the types of IP addresses?

There are several types of IP addresses.
Public IP addresses are addresses on the global internet. They can be used to access the Internet and to provide access all over the world. The
Private addresses are used to create a local network, in an office or enterprise and are used to save public addresses. 

Additionally there are static and dynamic addresses. 

#### Types of VLANs and use 

VLAN is created on Layer 2 switches to reduce the size of the broadcast domain. It is one of the technologies used to improve network performance by the separation of large broadcast domains into smaller ones.

###### There are 5 types of VLANs depending on the type of network they carry:

1. **Default VLAN**
When the switch initially starts up, all switch ports become a member of the default VLAN, which makes them all part of the same broadcast domain. Using default VLAN allows any network device connected to any of the switch ports to connect with other devices. It cannot be renamed or deleted

2. **Data VLAN**
Data VLAN is used to divide the whole network into 2 groups. One group of users and one group of devices

3. **Voice VLAN**
Voice VLAN is configured to carry voice traffic. Voice VLANs are mostly given high priority over other types of traffic 

4. **Management VLAN**
A management VLAN is configured to access the management capabilities of a switch (traffic like system logging, monitoring). VLAN 1 is the management VLAN by default (BAD CHOICE) This VLAN also ensures that bandwidth will be available for management even when user traffic is high

5. **Native VLAN**
This VLAN identifies traffic coming from each end of a trunk link. A native VLAN is allocated only to an 802.1Q trunk port. The 802.1q port places untagged traffic on the native VLAN (Traffic that doesn't come from any VLAN). Best to configure the native VLAN as an unused VLAN


## How Trunking Works 

Trunking refers to a network configuration that efficiently conveys data between multiple entities without using one-to-one links. For MSPs trunking in networking will typically relate either to link aggregation or VLAN trunking, a practice integral to VLAN configuration

#### What does trunk mean in networking

A trunk is a single channel of communication that allows multiple entities at one end to correspond with the correct entity at the other end. It is a 'link' that carries many signals at the same time, creating more efficient network access between 2 nodes. 

#### VLAN Trunking

To answer what is VLAN trunking, it is important to understand why networks hae VLANs. VLANs came into use in part to mitigate some difficulties with switched networks, which replaced hubs. Switches offer enhanced control compared to hubs, including increased throughput, reduced collisions and more. However, these switched networks have a flat topology that can create some congestion and redundancy issues. VLANs offer a solution.

A VLAN is a way to provide connectivity for subnets on a network. With a VLAN, its possible to configure a single switched network to better suit system requirements without making physical network changes. MSPs can assign switches to VLANs and create logical groups to partition communication. Network switches support VLANs and create Layer 2 subnet implementation. On a practical level, this both prevents certain devices from interacting and allows others to connect more efficiently

#### switchport nonegotiate

DTP is enabled on all modern Cisco switches - why? - should switches form trunks on their own? There are several reasons to not.

First it is bad design, trunks should be present where they were intended and only there. Secondly, leaving ports set to dynamic mode is a security hole. It would only take the correct DTP packet to form a trunk from an access port and the intruder could easily inject traffic to all allowed VLANs. 

These two issues can be resolved by configuring a static switchport mode either 'access' or 'trunk'

However even when a port is statically configured, DTP is still active on the port. DTP advertisements include the VTP domain, even if the port are manually configured in trunking mode. Fortunately DTP can be killed with the ``` switchport nonegotiate``` command on the interface.

## Spanning Tree (STP) Convergence

###### What is Layer 2 Network Convergence

STP convergence happens when bridges and switches have transitioned to either the forwarding or blocking state. When Layer 2 is converged, Root switch is elected and **Root Ports, Designated Ports and Non-designated ports** in all switches are selected. At converged condition ROot ports and designated ports are in a forwarding state, all other ports are in a blocking state. The

For Layer 2 switches, convergence occurs once STP has completed: a Root Switch is elected, Root Ports and Designated Ports have been chosen, the Root Ports and Designated Ports have been placed in a forwarding state and all other ports are blocking. 

If a port has to go through all four states, convergence takes 50 seconds, 20 secs blocking, 15 listening and 15 learning.
If a port doesn't have to go through the blocking state but starts at listening, convergence only takes 30 seconds. 

#### Varieties of STP

Several varieties of spanning-tree protocols since the original 802.1D

**STP:** Defined in 802.1D, this is the original standard that provided a loop free topology in a network with redundant links. It assumed one spanning-tree instance for the entire bridged network, regardless of the number of VLANs

**PVST+:** PVST+ is a Cisco enhancement of STP that provides a separate 802.1D spanning tree instance for each VLAN configured in the network with

**Rapid Spanning Tree Protocol (RSTP):** RSTP is defined in IEEE 802.1w. It is an evolution of STP that provides faster convergence than STP that

**Rapid Per-VLAN Spanning Tree:** RPVST+ is a CIsco enhancement of RSTP that uses PVST+ and provides a separate instance of 802.1w for each VLAN configured

**Multiple Spanning Tree Protocol (MSTP):** defined in 802.1s maps multiple VLANs into the same spanning-tree instance.

#### The Benefits of EtherChannel

