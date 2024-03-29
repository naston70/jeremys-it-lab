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

A VLAN is created in one of two ways, either in global Configuration mode or directly under the interface. The advantage to configuring in global configuration mode is that you can assign a name with the ```name vlan-name``` command. The advantage to configuring the VLAN in interface configuration mode is that you assign the VLAN to the interface and create the VLAN with just one command. However to name the VLAN, you still will need to use the global method. 

Creating VLANs:
```
# config t 
(config)# vlan 10
(config-vlan)# name Staff
(config-vlan)# interface fa0/12
(config-if)# switchport access vlan 20
(config-vlan)# name Students
(config-vlan)# vlan 30
(config-vlan)# name Guest(Default)
(config-vlan)# vlan 99
(config-vlan)# name Management&Native
(config-vlan)# end
```

Verify the creation with: ```show vlan brief```

To add to the interfaces add individually or by using the ```range``` command to configure all the interfaces. 

#### Assigning VLANs to interfaces

```
#conf t
(config)# interface range fa 0/11 - 17
(config-if-range)# switchport access vlan 10
```

## Trunking Configuration and Verification

Security best practice is to configure a different VLAN for the management and default VLAN. In a production network, you would want to use a different one for each, one for management VLAN and one for the native vlan.

#### Defining a New Management Interface
```
# conf t
(config)# interface vlan 99
(config-if)# ip address 172.15.1.1 255.255.255.0
#end
```

The IP is used to test connectivity to the switch as is the IP address the network administrator uses for remote access.

Depending on the switch model and Cisco IOS version, DTP might have already established trunking between two switches that are directly connected. For example, the default trunk configuration for 2950 switches is dynamic desirable. Therefore a 2950 initiates trunk negotiations. 2960 switches default trunk configuration is dynamic auto.
```
#conf t
(config)#interface range g0/1-2
(config-if-range)# switchport mode trunk 
(config-if-range)# switchport trunk native vlan 99
(config-if-range)# end 
```

(native vlan is also changed to 99)

#### Verifying Trunk Configuration
```
# show interfaces trun
```

Hosts on the same VLAN must be configured with an IP and subnet on the same subnet. Use ping to verify connectivity.

## VLAN Troubleshooting

If connectivity issues arise between VLANs and you have already resolved potential IP addressing issues, you can use the below chart to methodically track down issues related to VLAN configuration errors.

1. No connection among devices in same VLAN:
    - Is the port in the correct VLAN?
        * Yes - VLAN is present in VLAN db?
            * Yes - Verify connection among devices in same VLAN
            * No - Create VLAN in VLAN db 
        * No - Assign port to correct VLAN 

Step 1.
Use the ```show vlan``` command to check whether the port belongs to the expected VLAN, use the ```switchport access vlan number``` command to correct the VLAN membership. Use the ```show mac address-table``` command to check which addresses were learned on a particular port of the switch and see the VLAN to which that port is assigned. 

Step 2.
If the VLAN to which the port is assigned is deleted, the port becomes inactive. Use the ```show vlan``` or ```show vlan interfaces switchport``` command to discover issues with deleted VLANs. If the port is inactive, it is not functional until the missing VLAN is created using the ```vlan vlan_id``` command

#### Disabled VLANs

VLANs can be manually disabled. You can verify that VLANs are active by using the ```show vlan``` command. VLANs can be in one of two states: either *active* or *act/lshut*. The second of these states means the vlan is shut down

## Trunking Troubleshooting

To summarize issues with VLANs and trunking, you need to check for four potential issues in this order:

Step 1. Identify all access interfaces and their assigned access VLANs and reassign them into the correct VLANs

Step 2. Determine whether the VLANs exist and are active on each switch. If needed, configure and activate the VLANs to resolve problems.

Step 3. Check the allowed VLAN lists on the switches on both ends of the trunk and ensure that the lists of allowed vlans are the same

Step 4. Ensure that, for any links that should use trunking, one switch does not think it is trunking, while the other switch does not think it is trunking. 

#### Check Both Ends of a Trunk

For the CCNA, you should be able to notice a few errors that happen with bad configurations. 

It is possible to configure a different allowed VLAN list on opposite ends of a VLAN trunk, when the VLAN lists do not match, the trunk cannot pass traffic for that VLAN.

You can isolate the problem only by comparing the allowed lists on both ends of the trunk. 

The command ```show interfaces trunk```: allows for comparison of the allowed VLAN list.
If a VLAN is missing, add the VLAN to the correct interface, for example:
```
(config)# interface g0/2
(config-if)# switchport trunk allowed vlan add 10
```

Using the keyword **add** provides the capability to add one or more VLANs to the trunk without having to specify all the existing VLANs that are already allowed

#### Check Trunking Operational states

Trunks can be misconfigured. In some cases both switches conclude that their interfaces do not trunk. In other cases, one switch believes that its interface is correctly trunking, while the other switch does not.

The most common incorrect configuration, is a configuration that uses the ```switchport mode dynamic auto``` command on both switches on the link. The keyword auto does not mean that trunking happens automatically. Instead, both switches passively wait on the other device on the link to begin negotiations. 

The command ```show interfaces switchport``` on both switches can be used to confirm the administrative state and the fact that both switches operate as static access ports.
It is a good practice to check the trunks operational state on both sides of the trunk