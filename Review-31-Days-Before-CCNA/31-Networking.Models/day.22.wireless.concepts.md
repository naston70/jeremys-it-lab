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

For wireless devices to communicate over a network, the must first associate with the AP. An important part of the 802.11 process is discovering a WLAN and subsequently connecting to it. During this process, transmitted frames can reach any device within range. If the wireless connection is not secured, then others can read the traffic. 

The best way to secure a wireless network is to use authentication and encryption systems.

The two types of authentication were introduced with the original 802.11 standard:

- **Open System Authentication:** Should only be used in situations where security is of no concern. The wireless client is responsible for providing security such as by using a VPN to connect securely
- **Shared Key Authentication:** Provides mechanisms to authenticate and encrypt data between a wireless client and an AP. However, the password must be pre-shared between the parties to callow connection.

**Shared Key Authentication Methods:**
* **WEP**: The original 802.11 specification designed to secure data using the RC4 encryption method with a static key. However, the key never changes when exchanging packets. This makes it easy to hack and WEP is no longer recommended

* **WPA**: A Wi-Fi Alliance standard that uses WEP but secures the data with the much stronger TKIP algorithm. TKIP changes the key for each packet, making it much more difficult to hack.

* **WPA2**: The current industry standard for securing wireless networks. It uses the AES standard for encryption. AES is currently considered the strongest encryption protocol.

* **WPA3**: The next generation of Wi-Fi security. All WPA3 enabled devices use the latest security methods, disallow outdated legacy protocols, and require the use of Protected Management Frames (PMF). However devices with WPA3 are not readily available

#### WPA and WPA2

Home routers typically have two choices for authentication: WPA and WPA2. WPA2 is the stronger of the two. WPA2 authentication methods included the following:

- Personal: Intended for home or small office networks, users authenticate using a PSK. Wireless clients authenticate with the wireless router using a pre-shared password. No special authentication server is required

- Enterprise: Intended for enterprise networks but requires a Remote AuthenticationDial-In User Service (RADIUS) authentication server. Although more complicated to set up, it provides additional security. The device must be authenticated by the RADIUS server, and then users must authenticate suing the 802.1X standard, which uses EAP Extensible Authentication Protocol for authentication.

#### 802.1X/EAP

With open and WEP authentication, wireless clients are authenticated locally at the AP without further intervention. The scenario changes with 802.1X: The client uses open authentication to associate with the AP, and then the client authentication process occurs at a dedicated authenticated server. There is a three-party 802.1X arrangement, which consists of the following entities.

- Supplicant: The client device that is requesting access
- Authentication: The network device that provides access to the network
- Authentication Server: The device that permits or denies network access based on a user database and policies.

#### WPA3

WPA3 includes four features:
    - **WPA-3 Personal:** In WPA2-Personal, threat actors can listen in on the 'handshake' between a wireless client and the AP and use the brute-force attacks to try to guess the PSK. WPA3-Personal thwarts such attacks by using Simultaneous Authentication of Equals (SAE), a feature specified in the IEEE 802.11. The PSK is never exposed, making it impossible for the threat actor to guess
    - **WPA-3 Enterprise:** WPA3-Enterprise still uses 802.1X/EAP authentication. However, it requires the use of a 192-bit cryptographic suite and eliminates the mixing of security protocols for previous 802.11 standards. WPA3-Enterprise adheres to the Commercial National Security Algorithm (CNSA) suite, which is commonly used in high-security Wi-Fi networks
   - **Open Networks:** Open networks in WPA2 send user traffic in unauthenticated plaintext. In WPA3, open or public Wi-Fi networks still do not use any authentication. However, they do use Opportunistic Wireless Encryption (OWE) to encrypt all wireless traffic
   - **IoT onboarding:** Although WPA2 included Wi-Fi Protected Setup (WPS) to quickly onboard devices that were not previously configured, WPS is vulnerable to a variety of attacks and is not recommended. Furthermore, IoT devices are typically headless, meaning they have no built-in GUI for configuration and need any easy way to get connected to the wireless network. Device Provisioning Protocol (DPP) was designed to address this need. Each headless device has a hard-coded public key. The key is typically stamped on the outside of the device or its packaging as a Quick Response (QR) code. The network administrator can scan the QR code and quickly onboard the device. Although DPP is not strictly part of the WPA3 standard, it will replace WPS over time.

#### Wireless Encryption Methods

Encryption is used to protect data. An intruder may be able to capture encrypted data, but they would not be able to decipher it in any reasonable amount of time. The following encryption protocols are used with wireless authentication:

* TKIP: TKIP is the encryption method used by WPA. It provides support for legacy WLAN equipment and addresses the original flaws with 802.11 WEP encryption. It makes use of WEP but encrypts the Layer 2 payload using TKIP and carries out a message integrity check in the encrypted packet to ensure that the message has not been altered
* AES: AES is the encryption method used by WPA2. It is the preferred method because it is very strong method of encryption. It uses Counter Cipher Mode with Block Chaining Message Authentication Code Protocol, which allows destination hosts to recognise if the encrypted and non encrypted bits have been altered
* The Galois/Counter Mode Protocol (GCMP): This is a robust authenticated encryption suite that is more secure and more efficient than CCMP.
