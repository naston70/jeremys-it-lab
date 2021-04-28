## WAN Overview

- LAN: a network that connect computers and other devices in a relatively small area, typically a small building or group of buildings
- WAN: a geographically distributed network that connects multiple LANs together
- MAN: a network that connects computers and other devices in an area larger than a LAN but smaller than a WAN

LAN Design - Collapsed distribution and core, a larger LAN has three layers

WANs can be connected and built in a variety of different ways

## VPN - Virtual Private Networks

* A private network uses links which are dedicated for an individual organisation
* Local Area Networks are private networks 
* WANs can also use physical links which are dedicated for an individual organisation

- A VPN provides a virtual tunnel between private networks across a shared public network such as the Internet
- Traffic traveling over the tunnel is encrypted and only readable by the authorised users on both sides
- Users can share data over the tunnel as if they were connected with a dedicated private link 

* VPNs allow an organisation to use the same physical links for connectivity to the Internet and between offices
* Because they use shared infrastructure, VPN connections are typically less expensive than dedicated physical links

#### Site-to-Site VPN 

- Site-to-Site VPN connections are terminated on a router or firewall in each office 
- Software does not need to be installed on user desktops
- IPsec is typically used for encryption 

#### Remote Access VPN 
* Remote Access VPN connections are between a router or firewall in the office and VPN software installed on an individual users device
* The user can access the VPN from anywhere with Internet connectivity
* They usually use SSL for encryption

#### Site-to-Site VPN configuration options 

**IPsec tunnel:** open standard IPsec tunnel, does not support multicast
**GRE Generic Routing Encapsulation over IPsec tunnel:** adds support for multicast
**IPsec VTI Virtual Tunnel Interface:** Cisco proprietary simplified configuration, supports multicast
**DMVPN - Dynamic Multipoint VPN:** Cisco proprietary. Scalable simple hub and spoke style configuration enables direct full mesh connectivity between all offices
**FlexVPN:** Cisco proprietary. Similar to DMVPN, newer technology
**GETVPN - Group Encrypted Transport VPN:** Cisco proprietary. Scalable centralised policy for VPN over non-public infrastructure eg MPLS

#### WAN connectivity options

* Multiple options are available for connecting geographically dispersed offices together
* Not all options are available in all locations

**Primary WAN Options**
* Leased Line
* MPLS 
* Satellite

* The service provider will typically provide an SLA with guarantees for uptime and traffic delay and loss on the link 

- Leased lines and satellite can be used for connectivity to the Internet, for direct connectivity between offices and/or connectivity between offices over VPN 
- MPLS uses a shared core infrastructure at the service provider. It can be used for connectivity to the Internet and/or connectivity between offices over VPN

#### Optical Fiber

- Optical Fiber is more suitable for long distances than copper wire
- It is commonly used for service provider backhaul connection, but can also be offered to their customers
- FTTx services:
    * Fiber to the Home
    * Fiber to the Premises
    * Fiber to the building
    * Fiber to the Neighborhood

DWDM - Dense Wavelength Division Multiplexing
* DWDM combines multiple optical signals into one optical signal transmitted over a single fiber strand
* Each signal is assigned a different Wavelength
* DWDM allows more capacity to be added to existing infrastructure without adding upgrades
* DWDM is used in all modern long haul optical connections

#### Dark Fiber
- Many service providers laid optical fiber cabling in the past and then found they didn't require It
- DWDM was a major reason for this
- The unused cable can be offered to customers as 'Dark Fiber'

#### WAN Backup and Small Office Solutions

* Less expensive options aimed at home user Internet access can be used as Internet VPN WAN backup options in corporate environments
* There typically will be no corporate level SLA with these services
* These can be used as the primary WAN connection method to the corporate network from smaller offices and for home users
    * DSL Digital Subscriber Line
    * Cable 
    * Wireless

#### Interface Cards

- ROuters typically comes with on-board Ethernet ports. Additional Ethernet interface cards can be added
- Ethernet is often used for WAN connections today
- Other WAN interfaces are modular and fit into a spare slot on the router
- There are many different types of WAN interface cardsPart numbers for different cards can be very similar 
- Different cards are compatible with different router platforms

## Leased Lines

* A leased line is a dedicated physical connection between two locations 
* It has fixed, reserved bandwidth which is not shared with anyone else 
* The same bandwidth is available in both directions
* They company may own the cable but typically it is leased from a service provider, hence the term 

- The first location is typically a corporate office 
- The second location is typically:
    * Another office, providing ptp connectivity between the two
    * A data centre thats connected to the company's existing WAN, providing multipoint connectivity between offices 
    * A data centre thats connected to the Internet, providing Internet connectivity, and optionally corporate office connectivity over Internet VPN 










