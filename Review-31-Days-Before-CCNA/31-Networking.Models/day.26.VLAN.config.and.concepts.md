## VLAN and Trunking Concepts and Configurations

#### EXAM TOPICS
- Configure and verify VLANs (normal range) spanning multiple switches

- Configure and verify interswitch connectivity

#### VLAN Concepts 

Although a switch comes out of the box with only one VLAN, normally a switch is configured to have two or more VLANs. With such a switch, you can create multiple broadcast domains by putting some interface into one VLAN and other interfaces into other VLANs.

**Reasons for VLANs**:
* Grouping users by department instead of physical location
* Segmenting devices into smaller LANs to reduce processing overhead for all devices on the LAN
* Reducing the workload of STP by limiting a VLAN to a single access switch
* Separating IP voice traffic from data traffic 
* Assisting troubleshooting by reducing the size of the failure domain

**Benefits of VLANs**:
* Security - sensitive data can be isolated to one VLAN, seperated

* Cost reduction - reduced need for expensive upgrades and better efficiency of bandwidth and uplinks leading to cost saving

* Higher performance - Dividing a flat layer 2 network into multiple logical broadcast domains reduces unnecessary traffic on the network and boosts performance

* Broadcast storm mitigation - VLAN segmentation prevents broadcast storms from propagating throughout the entire network

* Ease of management and troubleshooting - A hierarchical addressing scheme groups network addresses contiguously.

#### Traffic Types

The key to successful VLAN deployment is understanding the traffic patterns and the various traffic types in the organization. 

**Network management**: Many types of network management traffic can be present on the network. To make network troubleshooting easier, some designers assign a seperate VLAN to carry certain types of network management traffic

**Ip telephony**: Two types of IP telephony traffic exist: signaling information between end devices and the data packets of the voice conversation. Designers often configure the data to and from the IP phones on a seperate VLAN designated for voice traffic so that they can apply quality of service measures to give high priority to voice traffic

**IP multicast**: Multicast traffic can produce a large amount of data streaming across the network. Switches must be configured to keep this traffic from flooding onto devices that have not requested it and routers must be configured to ensure that multicast traffic is forwarded to the network areas where it is requested. 

**Normal Data**: Normal data traffic is typical application traffic that is related to file and print services, email, browsing, db access and other net apps

**Scavenger class**: Scavenger class includes all traffic with protocols or patterns that exceed their normal data flows. Applications assigned to this class have little or no contribution to the organizational objectives of the enterprise and are typically entertainment based

#### Types of VLANs

Some VLAN types are defined by the type of traffic they support, others by the specific functions they perform. The principal VLAN types and their descriptions follow:

- **Data VLAN**: Configured to carry only user-generated traffic, ensuring that voice and management traffic is seperated from data traffic.

- **Default VLAN**: All the ports on a switch are members of the default VLAN when the switch is reset to factory defaults. The default VLAN for Cisco switches is VLAN 1. VLAN 1 has all the features of any VLAN except that it cannot be renamed and cannot be deleted. It is a security best practice to restrict VLAN 1 to server as a conduit only for Layer 2 control traffic (eg CDP) and support no other traffic

- **Black hole VLAN**: A security best practice is to define a black hole VLAN to be a dummy VLAN distinct from all other VLANs defined in the switched LAN. All unused switch ports are assigned to the black hole VLAN so that any unauthorized device connecting to an unused switch port is prevented from communicating beyond the switch to which it is connected

- **Native VLAN**: This VLAN type serves as a common identifier on opposing ends of a trunk link. A security best practice is to define a native VLAN to be a dummy VLAN distinct from all other VLANs defined in the switched LAN. The native VLAN is not used for any traffic in the switched network unless legacy bridging devices happen to be present in the network or a multiaccess interconnection exists between switches joined by a hub

- **Management VLAN**: The network administrator defines this VLAN as a means to access the management capabilities of a switch. By default, VLAN 1 is the management VLAN. It is a security best practice to define the management VLAN to be distinct from all other VLANs defined in the switched LAN. 

- **Voice VLAN**: A voice VLAN enables switch ports to carry IP voice traffic from an IP phone. The network administrator configures a voice VLANand assigns it to access ports. Then when an IP phone is connected to the switch port, the switch sends CDP messages that instruct the attached IP phone to send voice traffic tagged with the voice VLAN.  

#### Voice VLAN example

Using one port on a switch to connect a users IP phone and PC. 
The switch port is configured to carry data traffic on VLAN 20 and voice traffic on VLAN 150. The cisco IP phone contains an integrated 10/100 switch to provide the following dedicated connections:

* Port 1 connects to the switch or other voip device
* Port 2 is an internal 10/100 interface that carries the IP phone traffic
* Port 3 (access port) connects to a PC or other device 

The traffic from the PC attached to the IP phone passes through the IP phone untagged. The link between the switch and the IP phone acts as a modified trunk to carry both the tagged voice traffic and untagged data traffic

#### Trunking VLANs

A VLAN trunk is an Ethernet point-to-point link between an Ethernet switch interface and an Ethernet interface on another networking device, such as a router or switch, carrying the traffic of multiple VLANs over the singular link. A VLAN trunk enables you to extend the VLANs across an entire network. A VLAN trunk does not belong to a specific VLAN, instead it serves as a conduit for VLANs between switches. 

When a frame is placed on a trunk link, information about the VLAN it belongs to must be added to the frame. This is accomplished by using IEEE 802.1Q frame tagging. When a switch receives a frame on a port configured in access mode and destined for a remote device through a trunk link, the switch takes apart the frame and inserts a VLAN tag, recalculates the frame check sequence (FCS) and sends the tagged frame out the trunk port. 

The VLAN tag field consists of a 16-bit Type field called the EtherType field and a Tag control information field. the EtherType field is set to the hexadecimal value 0x8100. This value is called the tag protocol ID (TPID) value. With the EtherType field set to the TPID value, the switch receiving the frame knows to look for information in the Tag control information field. The Tag control information field contains the following:

- 3 bits of user priority : provides expedited transmission of Layer 2 frames, such as voice traffic 
- 1 bit of Canonical Format Identifier (CFI): enables token ring frames to be easily carried across Ethernet links
- 12 bits of VLAN ID: provides VLAN id numbers

#### Dynamic Trunking protocol

DTP is a Cisco proprietary protocol that negotiates both the status of trunk ports and the trunk encapsulation of trunk ports. DTP manages trunk negotiation only if the other switch is configured in a trunk mode that supports DTP. A switch port on a Cisco Catalyst switch supports a number of trunking modes. The trunking mode defines how the port negotiates using DTP to set up a trunk link with its peer port. 

**Trunking modes:**

* if the switch is configured with the ```switchport mode trunk``` command, the switch port periodically sends DTP messages to the remote port, advertising that it is an unconditional trunking state.
* if the switch is configured with the ```switchport mode trunk dynamic auto``` command, the local switch port advertises to the remote switch port that it is able to trunk but does not request to go to the trunking state. After a DTP negotiation, the local port ends up in the trunking state only if the remote port trunk mode has been configured so that the status is on or desirable. If both ports are set to auto they do not negotiate to be in a trunking state. They negotiate to be in the access mode state. 
* if the switch is configured with the ```switchport mode dynamic desirable``` command, the local switchport advertises to the remote switch port that it is able to trunk and asks the remote switch port to go to the trunking state. If the local port detects that the remote port has been configured as on, desirable or auto mode, the local port ends up in the trunking state. If the remote switch port is in the nonegotiate mode, the local switch port remains as a nontrunking port. 
* if the ```switchport nonegotiate``` command is configured, the local port is considered to be in an unconditional trunking state. Use this when configuring a trunk using another vendor. 


#### VLAN Configuration and Verification 

 
