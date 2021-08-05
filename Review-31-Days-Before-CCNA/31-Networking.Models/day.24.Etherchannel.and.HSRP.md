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

