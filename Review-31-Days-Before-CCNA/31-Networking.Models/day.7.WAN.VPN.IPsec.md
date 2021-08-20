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
