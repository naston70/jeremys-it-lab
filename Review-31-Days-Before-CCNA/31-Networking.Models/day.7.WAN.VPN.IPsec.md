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

In the past, the main limitation of wireless access was the need to be within range of a wireless router or a wireless modem with a wired connection to the Internet; however, the following wireless technologies enable users to connect to the Internet from almost any location: 

* Municipal Wi-Fi: Many cities have setup municipal wireless networks. Can provide high speed broadband for free, or substantially reduced connect
* WiMAX: IEEE 802.16 technology provides high speed broadband service with wireless access and provides broad coverage similar to a cell phone network instead of through small Wi-Fi hotspots
* Satellite Internet: Typically used in rural areas where cable and DSL are unavailable
* Cellular service: an option for connecting users and remote locations where no other WAN access technology is available. Common cellular access methods include 3/4G and LTE

#### VPN Technology

A virtual private network (VPN) is an encrypted connection between private networks over a public network such as the Internet. Instead of using a dedicated Layer 2 connection such as leased line, a VPN uses virtual connections called VPN tunnels, which are routed through the Internet from the company's private network to the remote site or employee host

###### VPN Benefits 

- Cost savings: eliminates the need for expensive dedicated WAN links and modem banks 
- Security: uses advanced encryption and authentication protocols that protect data from unauthorized access
- Scalability: can add large amounts of capacity without adding significant infrastructure
- Compatibility with broadband technology: supported by broadband service providers, so mobile workers and telecommuters can take advantage of their home high-speed Internet service to access their private networks

######Types of VPN Access

* Site-to-site VPNs: Site-to-site VPNs connect entire networks to each other. ie a site-to-site VPN can connect a branch office network to a company head office. Each site is equipped with a VPN gateway, such as a router, firewall, VPN concentrator or security appliance. 

* Remote-access VPN: remote-access VPNs enable individual hosts, such as telecommuters, mobile users and extranet consumers, to access a company network securely over the Internet. Each host typically has client software for a client based VPN connection or uses a web browser for clientless VPN connection. 

* Generic Routing Encapsulation (GRE): A standard IPsec VPN (non GRE) can only create secure tunnels for unicast traffic. GRE is a nonsecure site-to-site VPN tunneling protocol that can support multicast and broadcast traffic needed for network layer protocols. However, GRE does not by default support encryption, therefore, it does not provide a secure VPN tunnel. To solve this problem, you can encapsulate routing protocol traffic by using a GRE packet and then encapsulate the GRE packet into an IPSec packet to forward it securely to the destination VPN gateway. The terms used to describe the encapsulation of GRE over IPSec tunnel are passenger protocol for the routing protocol, carrier protocol for GRE and transport protocol for IPsec.

* Dynamic Multipoint VPN (DMVPN): DMVPN is a Cisco-Proprietary solution for building many VPNs in an easy, dynamic and scalable manner. DMVPN allows a network administrator to dynamically form hub-to-spoke tunnels. DMVPn simplifies the VPN tunnel configuration and provides a flexible option for connecting a central site with branch sites. It uses hub-and-spoke configuration to establish a full mesh topology. Spoke sites establish secure VPN tunnels with the hub site. Each site is configured using multipoint Generic Routing Encapsulation (mGRE). The mGRE tunnel interface allows a single GRE interface to dynamically support multiple IPSec tunnels.
DMVPn uses the following technologies:
1. Next Hop Resolution Protocol (NHRP): Maps public IP addresses for all tunnel spokes
2. IPsec encryption: Provides the security to transport private information over public networks
3. mGRE: Allows a single interface to support multiple IPsec tunnels
4. IPsec Virtual Tunnel Interface (VTI): Like DMVPN, VTI simplifies the configuration process required to support multiple sites and remote access. IPsec VTI is capable of sending an receiving both IP unicast and multicast encrypted traffic. Therefore, routing protocols are automatically supported without the need to configure GRE tunnels
5. Service provider MPLS VPNs: MPLS can provide clients with managed VPN solutions; therefore securing traffic between client sites is the responsibility of the service provider. Two types of MPLS VPN solutions are supported by service providers: 
    - Layer 3 MPLS VPN: The service provider participates in customer routing, redistributing the routes through the MPLS network to the customers remote locations
    - Layer 2 MPLS VPN: The service provider is not involved in the customer routing. Instead, the provider deploys Virtual Private LAN Service (VPLS) to emulate an Ethernet multiaccess LAN segment over the MPLS network. No routing is involved. The customers routers effectively belong to the same multiaccess network. 

#### VPN Components

In a typical VPN topology the following components are required to establish a VPN:
- An existing enterprise network with servers and workstations 
- A connection to the Internet 
- VPN gateways, such as routers, firewalls, VPN concentrators and Adaptive Security Appliances (ASAs) that act as endpoints to establish, manage and control VPN connections

#### Establishing Secure VPN Connections

VPNs secure data by encapsulating and encrypting it. With regard to VPNs, encapsulation and encryption are defined as follows: 
* Encapsulation is also called tunneling because encapsulation transmits data transparently from source network to destination network through a shared network infrastructure
* Encryption codes data into a different format by using a secret key, which is then used on the other side of the connection for decryption

#### VPN Tunneling

Tunneling uses three classes of protocols:
* Carrier protocol: the protocol over which information travels, such as frame relay, ppp or mpls 
* Encapsulating protocol: the protocol that is wrapped around the original data, such as GRE, IPsec, L2F, PPTP or L2TP
* Passenger protocol: the protocol over which the original data was carried, such as IPv4, IPv6, IPX or Appletalk

#### VPN Encryption Algorithms

The degree of security provided by any algorithm depends on the keys length. Some of the most common encryption algorithms and the lengths of the keys they use are:
- **Data Encryption Standard (DES):** Uses a 56-bit key and ensures high performance encryption. DES is a symmetric key cryptosystem
- **Triple DES (3DES):** Newer variant of DES that encrypts with one key, decrypts with a different key, then encrypts again with another key 
- **Advanced Encryption Standard (AES):** Provides stronger security than DES and is computationally more efficient than 3DS. AES offers 3 key lengths, 128, 192 and 256 
- **Rivest, Shamir and Adleman (RSA):** An asymmetric key cryptosystem. The key uses bit length of 512, 768 or 1024

With symmetric encryption, the encryption key and decryption key are the same. With asymmetric encryption, they are different

#### Hashes

VPNs use a keyed hashed message authentication code (HMAC) data-integrity algorithm to guarantee a messages integrity and authenticity without any additional mechanisms

The cryptographic strength of the HMAC depends on the cryptographic strength of the underlying hash function, the keys size and quality and the size of the hash output length in bits. There are 2 common HMAC algorithms:
* Message Digest 5 (MD5) - uses a 128-bit shared secret key
* Secure Hash Algorithm 1 (SHA-1) - Uses a 160 bit secret key 

#### VPN Authentication 

The device on the other end of the VPN tunnel must be authenticated before the communication path is considered secure. The two peer authentication methods are as follows: 
* Pre-Shared Key (PSK): A secret key is shared between the two parties using a secure channel before it needs to be used
* RSA signature: This method uses the exchange of digital certificates to authenticate the peers

#### IPsec Security Protocols

Both IPsec and SSL VPN technologies offer access to virtually any network application or resource However, when security is an issue IPsec is the superior choice.

###### IPsec and SSL for Remote Access

| Feature                 | IPsec             | SSL                    |
|-------------------------|-------------------|------------------------|
|                         |                   |                        |
| Applications supported  | All IP based      | web based/file sharing |
| Authentication strength | Strong            | Moderate               |
| Encryption strength     | Strong            | Moderate to strong key |
| Connection complexity   | Medium preinstall | Low - only web browser |
| Connection Option       | Limited devices   | Extensive              |
|                         |                   |                        |


