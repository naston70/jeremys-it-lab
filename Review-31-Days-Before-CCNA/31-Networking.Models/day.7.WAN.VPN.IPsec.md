## WAN, VPN and IPsec

#### WAN Topologies

There are four basic WAN topology options that a business can select for its WAN infrastructure
* Point to point: typically uses a leased-line connection 
* Hub-and-spoke: Offers a single homed, point to multipoint topology in which a single interface on the hub router can be shared with multiple spoke routers through the use of virtual interfaces
* Full mesh: gives each router a connection to every other router. Requires a large number of interfaces
* Dual-homed: Provides redundancy for a single homed hub-and-spoke topology by providing a second hub to connect to spoke routers

## WAN Connection Options

Many options for implementing WAN solutions are currently available. They differ in speed, cost and technology. Requires

#### WAN Link Connection Options:

WAN:

**Private:**- Dedicated = Leased Lines
            - Switched = Circuit Switched (PTSN-ISDN) and Packet Switched (Frame Relay, Metro Ethernet x25 ATM)

**Public:**- Internet -> Broadband VPN -> DSL, Cable, Wireless

#### Dedicated Connection Options

Also called leased lines, dedicated connections are established point-to-point WAN connections from the customer premises through the provider network to a remote destination 

Leased lines are usually more expensive than switched services because of the dedicated, always on cost of providing WAN services to the customer. The dedicated capacity removes latency and jitter and provides a layer of security because only the customers traffic is allowed on the link

###### Leased Line Types and Capacities

T1 = 1.544 Mbps  (the standard in America), 
E1 and J1 = 2.048 Mbps (the standard in Europe),
E3 = 34.064 Mbps 
T3 = 44.736 Mbps
OC range for higher speeds

#### Circuit-Switched Connection Options

The two main types of circuit switched connections are analog dialup and ISDN. Both technologies have limited implementation bases in today's networks. However, they are both still used in remote rural areas and other areas of the world where more recent technologies are not available.

Analog dialup uses modems at very low-speed connections that might be adequate for the exchange of sales figures, prices, emails or as an emergency backup.

ISDN turns the local loop into a TDM digital connection, which enables it to carry digital signals that result in higher capacity switched connections than are available with analog modems. Two types of ISDN interfaces exist:

* Basic Rate Interface (BRI): Provides two 64 kbps B-channels for voice or data transfer and an 16 kbps D-channel for control signalling
* Primary Rate Interface: Provides 23 B-channels with 64 kbps and 1 D-channel with 64 kbps in North America. Europe uses 30 B-channels and 1 D-channel 

#### Packet-Switched Connection Options

The most common packet-switching technologies used in today's enterprise WANs include Metro Ethernet and MPLS. Legacy is X.25 and ATM.

###### Metro Ethernet

MetroE uses IP-aware Ethernet switches in the service providers network cloud to offer enterprises converged voice, data and video services at Ethernet speeds. Some benefits of MetroE:

- **Reduced expenses and admin:** Enables businesses to inexpensively connect numerous sites in a metropolitan area to each other and to the Internet without the need for expensive conversions to ATM or Frame Relay
- **Easy integration with existing networks:** Connects easily to existing Ethernet LANs
- **Enhanced business productivity:** Enables businesses to take advantage of productivity-enhancing IP applications that are difficult to implement on TDM or Frame Relay networks, such as hosted IP communications, VoIP, and streaming and broadcasting video

###### MPLS - Multiprotocol Label Switching 

MPLS has the following characteristics:

- **Multiprotocol:** MPLS can carry any payload, including IPv4, IPv6, Ethernet, ATM, DSL and Frame Relay traffic
- **Labels:** MPLS uses labels inside the service providers network to identify paths between distant routers instead of between endpoints
- **Switching:** MPLS actually routes IPv4 and IPv6 packets, but everything else is switched connections
 There are CE (customer edge) and PE (provider edge) routers - PE routers add and remove the labels. 

#### Internet Connection Options

Broadband connection options typically are used to connect telecommuting employees to a corporate site over the Internet. Includes DSL, cable and wireless.

###### DSL

DSL technology is an always-on connection technology that uses existing twisted-pair telephone lines to transport high-bandwidth data and provides IP services to subscribers. Current DSL technologies use sophisticated coding and modulation techniques to achieve data rates of up to 8.192 Mbps. A variety of DSL types, standards and emerging technologies exist. DSL is a popular choice for enterprise departments to support home workers

###### Cable Modem 

A cable modem provides an always-on connection and simple installation. A subscriber connects a computer or LAN router to the cable modem, which translates the digital signals into the broadband frequencies for transmitting on a cable television network.

###### Wireless

In the past, the main limitation of wireless access was the need to be within range of a wireless router or a wireless modem  
