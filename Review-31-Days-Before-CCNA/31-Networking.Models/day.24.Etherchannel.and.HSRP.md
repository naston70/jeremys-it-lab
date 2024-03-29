## EtherChannel and HSRP

#### Exam Topics

- Configure and verify EtherChannel
- Describe the purpose of first hop redundancy protocol

EtherChannel enables you to bundle multiple physical interfaces into one logical channel to increase the bandwidth on point-to-point links. In addition, EtherChannel provides a sway to prevent the need for Spanning Tree Protocol convergence when only a single port or cable failure occurs

Most end devices do not store routes to reach remote networks. Instead, an end device is typically configured with a default gateway than handles routing for the device. 

What if this device fails? To ensure that a device will still have access to remote networks, you should implement some type of default gateway redundancy in the network. That is the role of first-hop redundancy protocols (FHRPs)

#### EtherChannel Operation

EtherChannel, a technology that cisco developed, can bundle up to 8 equal-speed links between two switches. STP sees the bundle of links as a single interface. As a result, if at least one of the links is up, STP convergence does not have to occur. This makes much better use of available bandwidth while reducing the number of times STP must converge. 

Without the use of EtherChannel or modification of the STP configuration, STP would block all links except one. 

#### Benefits of EtherChannel

When EtherChannel is configured, the resulting virtual interface is called a port channel. The physical interfaces are bundled together into a port channel interface. EtherChannel has the following benefits:

* Most configuration tasks can be done on the EtherChannel interface instead of on each individual port, thus ensuring configuration consistency throughout the links. 
* EtherChannel relies on existing switch ports to increase bandwidth. No hardware upgrades are required
* Load balancing is possible between links that are part of the same EtherChannel
* EtherChannel creates an aggregation that STP recognizes as one logical link. 
* EtherChannel provides redundancy

#### Implementation Restrictions

There are a few limitations when implementing EtherChannel on Cisco 2960 Catalyst switches:
- Interface types cannot be mixed within the same EtherChannel
- Each EtherChannel can consist of up to 8 compatibly configured Ethernet ports
- Cisco IOS software currently supports up to six EtherChannels
- Some servers also support EtherChannel to the switch to increase bandwidth, however the server then needs at least two EtherChannels to provide redundancy because it can send traffic to only one switch through the EtherChannel
- The EtherChannel configuration must be consistent on the two switches. The trunking configuration (native, allowed vlans, etc) must be the same. All ports must be Layer 2 ports. 
- All ports in the Etherchannel must be Layer 2 ports or all ports must be Layer 3 ports

## EtherChannel Protocols

You can configure EtherChannel as static or unconditional; however you can also use two protocols to configure the negotiation process:
Port Aggregation Protocol(PAgP), which is Cisco proprietary, and Link Aggregation Control Protocol (LACP - iEEE 802.3ad) These two protocols ensure that the two sides of the link have compatible configurations - same speed, duplex setting and VLAN information: The modes for each can differ slightly.

#### Port Aggregation Protocol

PAgP is a cisco proprietary protocol that aids in the automatic creation of EtherChannels. PAgP check for configuration consistency and manages link additions and failures between the two switches. It ensures that when an EtherChannel is created, all ports have the same type of configuration. PAgP uses the following modes:
- **On:** this mode forces the interface to channel without PAgP
- **Desirable:** the interface initiates negotiations with other interfaces by sending PAgP negotiation
- **Auto:** the interface responds to the PAgP packets that it receives but does not initiate PAgP negotiation 

The modes must be compatible on the two sides of the EtherChannel.

| S1                | S2             | Channel Established? |
|-------------------|----------------|----------------------|
| on                | on             | yes                  |
| auto/desirable    | desirable      | yes                  |
| on/auto/desirable | not configured | no                   |
| on                | desirable      | no                   |
| auto/on           | auto           | no                   |

#### Link Aggregation Control Protocol

The Link Aggregation Control Protocol (LACP) is part of an IEEE specification 802.3.ad that allows a switch to negotiate an automatic bundle by sending LACP packets to the peer. It performs a function similar to PAgP with Cisco EtherChannel. Cisco devices support both PAgP and LACP.
LACP uses the following modes:
* **On:** This mode forces the interface to channel without LACP
* **Active:** The interface initiates negotiations with other interfaces by sending LACP packets
* **Passive:** The interface responds to the LACP packets that it receives but does not initiate LACP negotiation.

As with PAgP, the LACP modes must be compatible on the two sides of the EtherChannel. 

###### LACP Mode Settings

| S1                | S2             | Channel Established? |
|-------------------|----------------|----------------------|
| on                | on             | yes                  |
| active/passive    | active         | yes                  |
| on/active/passive | not configured | no                   |
| on                | active         | no                   |
| passive/on        | passive        | no                   |

#### Configuring EtherChannel

To implement EtherChannel;

**Step 1.** Specify the interfaces that you want to bundle together iin one link by using the ```interface range interfaces``` command

**Step 2.** Create a port channel by using the ```channel-group identifier mode mode``` command. the identifier can be between 1 and 6 inclusive and does not have to match the other switch. The mode is either ```on``` or one of the PAgP or LACP modes.

**Step 3.** Enter interface configuration mode for the new port channel with the ```interface port-channel identifier``` command. identifier is the same number used with the ```channel-group``` command

**Step 4.** Configure the trunking and VLAN settings.

###### Example

Sw1 is configured for EtherChannel with g0/1 and g0/2 trunking. The native VLAN is 86. The allowed VLANs are 1,10,20 and 86. EtherChannel is forced on. No PAgP or LACP is needed:
```
sw2(config)# interface range g0/1-2
sw2(config-if-range)#channel-group 1 mode on

creating port-channel 1:
Sw2(config-if-range)# interface port-channel 1
Sw2(config-if)# switchport mode trunk
Sw2(config-if)# switchport trunk native vlan 86
Sw2(config-if)# switchport trunk allowed vlan 1,10,20,86
```

#### Verifying EtherChannel

If you configured management addressing, you can quickly verify both sides of an EtherChannel bundle by pinging across the trunk. The two switches should be able to ping each other.
Devices configured as members of the various VLANs should also be able to ping each other. 
```
#show run | begin interface Port
for an overall summary of the EtherChannel:
#show etherchannel summary 
```

#### Troubleshooting EtherChannel

All interfaces within an EtherChannel must have the same configuration of speed for the duplex mode and allowed VLANs on trunks and access VLAN on access ports:

- Assign all ports in the etherchannel to the same VLAN or configure them as trunks. Ports with different native VLANs can not form an EtherChannel
- When configuring a trunk on an EtherChannel, verify the trunking mode on the EtherChannel. Configuring trunking mode on individual ports that make up the EtherChannel is not recommended. However if it is done, verify that the trunking configuration is the same on all interfaces.
- As EtherChannel supports the same allowed range of VLANs on all ports. If the allowed range of VLANs is not the same, the ports do not form an EtherChannel even when PAgP is set to auto or desirable 
- The dynamic negotiation options for PAgP and LACP must be compatibly configured on both ends of the EtherChannel

Configuration issues with the **channel-group** command include:

* Configuring the **on** keyword on one switch and desirable, auto, active or passive on the other switch. The **on** keyword does not enable PAgP or LACP. Both switches should be configured on one of the acceptable PAgP or LACP modes
* Configuring the **auto** keyword on both switches. This enables PAgP, but each switch waits on the other to begin negotiations.
* Configuring the **passive** keyword on both switches. This enables LACP, but each switch waits on the other to begin negotiations
* Mixing keywords from PAgP and LACP.

#### First-Hop Redundancy Concepts

Both routers are configured with a virtual IP address. the virtual IP address is the default gateway address configured on end devices. A redundancy protocol provides the mechanism for determining which router should take the active role in forwarding traffic. It also determines when a standby router must take over the forwarding role. The transition from one forwarding router to another is transparent to the end devices. This capability of a network to dynamically recover from the failure of a device acting as a default gateway is known as *first-hop redundancy*

Regardless of which FHRP is implemented, the following steps take place when the active router fails:

Step 1. The standby router stops seeing hello messages from the forwarding router

Step 2. The standby router assumes the role of forwarding router

Step 3. Because the new forwarding router assumes both the IP and MAC address of the virtual router, the end stations do not recognize a disruption in service.

#### FHRPs

The following list defines the three options available for FHRPs:

* **HSRP:** 
A Cisco proprietary FHRP designed to allow for transparent failover of a first-hop IPv4 device. The function of the HSRP standby router is to monitor the operational status of the HSRP group and to quickly assume packer-forwarding responsibility if the active router fails

* **Virtual Router Redundancy Protocol (VRRP):**
An IETF standard that dynamically assigns responsibility for one or more virtual routers to the VRRP routers on an IPv4 LAN. Its operation is similar to that of HSRP. VRRPv3 supports IPv4 and IPv6

* **Gateway Load Balancing Protocol (GLBP):**
A Cisco proprietary FHRP that protects data traffic from a failed router or circuit, as in HSRP and VRRP, while also load balancing between a group of redundant routers. 

CCNA covers HSRP

## HSRP Operation

HSRP uses an active/standby model in which one router actively assumes the role of default gateway for devices on the subnet. One or more routers on the same subnet are then in standby mode. The HSRP active router implements a virtual IP address and matching virtual MAC address. This virtual IP address is part of the HSRP configuration and belongs to the same subnet as the physical interface IP but is a different IP. The router then automatically creates the virtual MAC address. All cooperating HSRP routers know these virtual addresses, but only the HSRP active router uses these addresses at any one point in time.

Assume two routers R1 and R2. These HSRP routers send each other messages to negotiate which router should be active. Then they continue to send each other messages so that the standby router can detect when the active router fails. If the active router fails the standby router automatically assumes the virtual IP and MAC address and serves as the default gateway for the LAN.
The new active router then sends out gratuitous ARP so that the switches on the subnet will change their MAC address tables to reflect the correct port to reach the virtual MAC. This failover process is transparent to end devices, which are all configured with the virtual IP address as the default gateway.

Load balancing? Is the capacity of a second router and the links connected to it wasted if connected in just 1 LAN? Yes. However, if VLANs are configured, the routers can share the load by each serving as the active router for some of the VLANs. 

#### HSRP Versions

Version 1 supports group numbers 0 - 255
Version 2 supports group numbers 0 - 4095

#### HSRP Priority and Preemption

By default,t he router with the numerically highest IPv4 address is elected as the active HSRP router. To configure a router to be the active router, regardless of IPv4 addressing, use the **standby priority** interface configuration control. The default priority is 100. The router with the highest priority will be the active HSRP router assuming that no election has already occurred.

To force a new HSRP election, preemption must be enabled with the ```standby preempt``` interface configuration command.

## HSRP Configuration and Verification

HSRP requires only one command on both routers:
```
Router(config-if)# standby group ip ip-address
```

The interface must be on the same subnet as the other HSRP router or routers. The group number and virtual ip-address must be the same on all HSRP routers.

Unless the **priority** command is used, the first router configured becomes the HSRP active router. To ensure a router regains priority after a loss in connectivity, the ```standby preempt``` command is configured. 

The ```show standby brief``` command displays the most pertinent information you might need in a few lines of output. The more verbose **show standby** command provides additional information 

## HSRP Load Balancing 

As with STP you might want HSRP routers to be configured in an active/active state, with one router active for one set of VLANs and the other router active for the remaining VLANs.
To implement HSRP load balancing for different VLANs configure one router for half the VLANs and the second router active for the other half of VLANs

#### Troubleshooting HSRP:

Issues with HSRP most likely result from one or more of the following:

- The active router that controls the virtual IP address for the group was not successfully elected
- The standby router did not successfully keep track of the active router
- No decision was made regarding when to hand another router control of the virtual IP for the group
- End devices failed to successfully configure the virtual IP address as the default gateway

Common HSRP configuration issues include the following:
* The HSRP routers are not connected to the same network segment
* The HSRP routers are not configured with IPv4 addresses from the same subnet
* The HSRP routers are not configured with the same virtual IPv4 address 
* The HSRP routers are not configured with the same HSRP group number 
* End devices are not configured with the correct default gateway 


