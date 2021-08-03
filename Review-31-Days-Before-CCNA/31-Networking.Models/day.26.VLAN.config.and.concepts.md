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


