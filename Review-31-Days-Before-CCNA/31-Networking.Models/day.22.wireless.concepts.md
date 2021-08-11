## Wireless Concepts

#### Exam Topics

- Explain the role and function of network components
- Describe wireless principles
- Compare cisco wireless architectures and AP modes
- Describe physical infrastructure connections of WLAN components
- Describe AP and WLC management access connections
- Describe wireless security protocols

## Wireless Standards

The 802.11 WLAN standards define how radio frequencies are used for wireless links. To avoid interference, different channels within an RF can be used.

#### RF Spectrum

The RF spectrum includes all types of radio communications, including 2.4GHz and 5-GHz frequencies used by wireless devices.

###### Channels

A frequency range is typically called a band of frequencies. ie, a wireless LAN device with 2.4-GHz antenna can actually use any frequency from 2.4000 to 2.4835 GHz. The 5-GHz band lies between 5.150 and 5.825.

The bands are further subdivided into frequency channels. Channels become particularly important when the wireless devices in a specific area become saturated. Each channel is known by a channel number and is assigned to a specific frequency. As long as the channels are defined by a national or international standards body, they can be used consistently in all locations.

The 5-GHz band consists of nonoverlapping channels. Each channel is allocated a frequency range that does not encroach on or overlap the frequencies allocated for any other channel. This is not true with 2.4-GHz, the only way to avoid any overlap between adjacent channels is to configure access points (APs) to use only one channels 1,6 and 11

#### 802.11 Standards

Most of the standards specify that a wireless device must have one antenna to transmit and receive wireless signals on the specified radio frequency. Some of the newer standards that transmit and receive at higher speeds require APs and wireless client to have multiple antennas using the multiple input multiple output technology (MIMO). MIMO uses multiple antennas as both the transmitter and receiver to improve communication performance. Up to four antennas can be supported. 

#### Wireless Topologies

The 802.11 standard identifies two main wireless topology modes: **infrastructure mode** and **Independent Basic Service Set (IBSS)**.
IBSS is also known as ad-hoc mode. With the ubiquity of wireless networks, mesh topologies are now common.

#### Infrastructure Mode 

With infrastructure mode, wireless clients interconnnect via an AP. 
Configuration of APs to share the same SSID allows wireless clients to roam between BSAs

Infrastructure terminology:
- Basic Service Set (BSS): This consists of a single AP interconnecting all associated wireless clients 

- Basic Service Area (BSA): This is the area that is bound by the reach of the APs signal. The BSA is also called a cell 

- Basic Service Set Identifier (BSSID): This is the unique machine readable identifier for the AP that is in the format of a MAC address and is usually derived from the APs wireless MAC address

- Service Set Identifier (SSID): This is a human-readable, non unique identifier used by the AP to advertise its wireless service.

- Distribution System (DS): APs connect to the network infrastructure using the wired DS, such as Ethernet. An AP with a wired connection to the DS is responsible for translating frames between 802.3 Ethernet and 802.11 wireless products

- Extended Service Set (ESS): When a single BSS provides insufficient coverage, two or more BSSs can be joined through a common DS into an ESS. An ESS is the union of twp or more BSSs interconnected by a wired DS. Each ESS is identified by its SSID and each BSS is identified by its BSSID

#### Independent Basic Service Set (IBSS), or Ad Hoc modes

In the 802.11 standard, IBSS is defined as two devices connected wirelessly in a peer-to-peer manner without the use of an AP. One device takes he role of advertising the network to clients. The IBSS allows two devices to communicate directly without the need for any other wireless devices, IBSS does not scalle well beyond 8 to 10 devices.

#### Mesh 

Having a wired DS connecting all APs is not always practical or necessary. Instead APs can be configured to connect in mesh mode. In this mode APs bridge client traffic between each other. Each AP in the mesh maintains a BSS on one channel used by wireless clients. Then the APs bridge between each other using other channels. The mesh network runs its own dynamic routing protocol to determine the best path to the wired network.

## AP Architectures

APs can be networked together in a variety of architectures. The size and scalability of the network determine which architecture is most suited for a given implementation.

#### Autonomous AP Architecture

An Autonomous AP is a self contained device with both wired and wireless hardware so that it can bridge to the wired VLAN infrastructure wireless clients that belong to SSIDs. Each autonomous AP must be configured with a management IP so that it can be remotely accessed using Telnet, SSH or a web interface. Each AP must be individually managed and maintained unless using a management platform such as Cisco DNA Center.

#### Cloud-Based AP Architecture 

Cloud-Based AP management is an alternative to purchasing a management platform. The AP management function is push into the cloud, ie Cisco Meraki is a cloud based AP management service that allows you to automatically deploy Cisco Meraki APs. These APs can then be managed from the Meraki cloud wen interface.

There are two distinct paths for data using this system. One for data traffic and one for management traffic, corresponding to the following two functions:

- A control plane: Traffic used to control, configure, manage and monitor the APs
- A data plane: End-user traffic passed through the APs

#### Lightweight AP Architectures

Wireless LAN controllers (WLCs) use Lightweight Access Point Protocol (LWAPP) to communicate with lightweight APs (LAPs). LAPs are useful in situations where many APs are required in the network. They are 'Lightweight' because they only perform the 802.11 wireless operation for wireless clients. Each LAP is automatically configured and managed by the WLC. 

#### CAPWAP Operation

The division of labor between the WLC and LAPs is known as split-MAC architecture. The LAP must interact with wireless clients on some low level, known as the Media Access Control layer. These functions must stay with the LAP hardware closet to the clients. The management functions are not integral to handling frames but are things that should be centrally administered. Therefore, thos functions can be moved to a centrally located platform away from the AP. 


| AP MAC Functions                            | WLC MAC Functions                                   |
|---------------------------------------------|-----------------------------------------------------|
| Beacons and probe responses                 | Authentication                                      |
| Packet acknowledgement and  re-transmissions | Association and re-association of roaming client    |
| Frame queuing and packet prioritization     | Frame translation to other protocols                |
| MAC layer data encryption and decryption    | Termination of 802.11 traffic  on a wired interface | 

LWAPP has been replaced by the Control and Provisioning of Wireless Access Points (CAPWAP) tunneling protocol to implement thes MAC functions. CAPWAP uses two tunnels - one for control and one for data.

* CAPWAP control message tunnel:
Carries exchanged that are used to configure the LAP and manage its operation. The control messages are authenticated and encrypted, so the LAP is securely controlled by only the appropriate WLC and then transported over the control tunnel using UDP prot 5246 

* CAPWAP data tunnel: Used for packets traveling to and from wireless clients that are associated with the AP. Data packets are transported over the data tunnel using UDP 5247 but are not encrypted by default. When the data encryption is enabled for a LAP, packets are protected with Datagram transport layer security (DTLS)

## Wireless Security Protocols

Wireless traffic is inherently different from traffic traveling over a wired infrastructure. Any wireless device operating in the same frequency can hear the frames and potentially read them. Therefore WLANs need to be secured to allow only authorized users and devices and to prevent eavesdropping and tampering of wireless traffic

#### Wireless Authentication Methods


