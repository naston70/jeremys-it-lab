## Wireless Networking 

#### Wireless Network Types 

**WPAN:** Wireless Personal Area Network 
* Devices are usually within 10 meters of each other
* Bluetooth often used

**WLAN:** Wireless Local Area Network 
* Provides access to a campus network, without the need for a cable
* Devices within 100m of a Wireless Access Point 

**WMAN:** Wireless Metropolitan Area Network 
* Covers a large area such as a city 

- Two or more wireless stations communicate directly with each other 
- This is known as an IBSS - Independent Basic Service Set 

#### Infrastructure Mode

* Stations communicate via a Wireless Access Point 
* Multiple Access Points can be deployed to provide the required coverage area 

- Wireless stations work in either Ad-Hoc or Infrastructure Mode
- They can not operate in both at the same time 

#### WiFi Direct 
* WiFi Direct allows devices to be connected to an Access Point and also be part of a peer-to-peer wireless network
* It does not operate in Ad-Hoc IBSS mode, it is an extension to Infrastructure mode
* WPS WiFi Protected Setup enables connection setup by pushing a button 
* It is WPAN Wireless Personal Area Network

#### WiFi Direct Predefined Services
- Miracast to wireless external monitor
- DLNA Digital Living Network ALliance allows devices to stream music and video 
- Direct Print 

#### Wireless Bridges 
- Wireless Bridges can be used to connect areas which are not reachable via cable to the network 

#### Wireless Mesh Networks 
- Another option to spread the coverage area of a WLAN is Mesh
- One AP radio is used to serve clients
- The other radio connects to the backhaul network 

## Infrastructure Mode and Wireless Access Points

#### Wireless Access Points 

- Wireless access Points provide connectivity between wireless stations and between wireless and wired networks 

* Wireless is half-duplex
* Only one device can communicate at a time 

#### BSS Basic Service Set 

* An access point centralizes access and control over a group of wireless devices 
* The devices and their wireless settings make up a BSS

#### DS - Distribution System

- A Distribution system connects Wireless Access Points to the wired network

#### BSSID - Basic Service Set Identifier 
- Devices within Basic Service Sets are identified by their BSSID which is based on their MAC address 

#### BSA - Basic Service Area 
- The BSA is the wireless coverage area of an Access Point 
- Also known as the wireless cell

#### SSID - Service Set Identifier
- The SSID is a unique identifier that names the wireless network

#### Multiple SSID Service Set Identifiers
- A single Access Point can support multiple SSID's 
- Different SSID's can have different security settings and be mapped to different VLANs

#### Beacons
- Wireless Access Points broadcast information about their WLANs with beacon frames (including SSID and authentication requirements)
- This can be disabled 

#### ESS - Extended Service Set
- The same SSID can be supported across multiple Access Points to give a larger coverage area

#### Roaming 
- Wireless client stations can roam across Wireless APs supporting the same WLANs



## Wireless LAN Controllers and CAPWAP
- In a large campus, configuring a large amount of APs one by one becomes unmanageable
- A wireless LAN controller can be used as a central point of management 

#### Autonomous vs Lightweight Access Points
* Standalone Access Points are known as Autonomous Access Points
* Access Points with a WLC are known as Lightweight Access Points
* The installed software image determines whether an AP is Lightweight or Autonomous

#### Zero Touch Provisioning
* Lightweight Access Points support Zero Touch Provisioning
* The discover their Wireless LAN Controller via these methods:
    - DHCP - option 43 gives the IP of the WLC
    - DNS - 'cisco-capwap-controller' resolves the IP address of the WLC
    - Local subnet broadcast

#### Wireless Access Points  

* The lightweight AP downloads its configuration from the Wireless LAN controller
* This includes what WLANs it should support and their settings
* The WLC also monitors the wireless quality and controls the channels and power of the APs
* It can also detect rogue APs

#### Roaming with Wireless LAN Controller 
* Wireless stations can roam across Wireless APs supporting the same WLANs
* The Infrastructure can be configured to make roaming seamless

## CAPWAP - Control and Provisioning of Wireless Access Points
- A standardized protocol that enables a Wireless LAN Controller to manage a collection of Wireless Access Points 
- Communications are encrypted inside a DTLS CAPWAP tunnel
- It uses UDP port 5246 and 5247

#### Split MAC 
* Work is removed from the APs to the WLC which is why they are called Lightweight APs
* Real-time traffic is still handled by the AP in order to provide suitable performance, the rest is handled by the WLC
* This is known as 'Split Mac'

###### Split MAC - AP Operations
- Client handshake when connecting 
- Beacons
- Performance monitoring
- Encryption and Decryption
- Clients in power save 

###### Split MAC - WLC Operations

* authentication
* roaming control 
* 802.11 - 802.3 Communications
* Radio frequency management
* Security management
* QoS management

#### Traffic Flow with CAPWAP
- management traffic between the AP and WLC passes through the CAPWAP tunnel
- LAG Link Aggregation is often used on the WLC to switch link 

#### FlexConnect
* Traffic is forwarded locally when FlexConnect is configured
* This is useful for small branch offices without a Wireless LAN Controller 


## Switch Configuration for Wireless Networks 

#### Wireless Channels and Radio Frequencies

- WiFi services operate in the 2.4 and 5 GHz frequency spectrum 
- This is allocated for ISM industrial, scientific and medical use 
- A radio operators license is not required 
- ISM devices do not have regulatory protection against interference from other users of the band 

#### 2.4Ghz spectrum
* 2.4 GHz ISM spectrum ranges from 2.4 to 2.4835
* The spectrum is divided into smaller (22 MHz) ranges of frequencies called channels
* Each AP operates in one channel
* Some channels overlap and can cause interference with each other 
* Access points with overlapping service areas should use non-overlapping channels 

#### 5 GHz spectrum
* 5 GHz channels are 20 MHz wide 
* They have less overlap than 2.4 GHz channels 
* Neighboring APs should be seperated by at least one channel
* Channels can be bonded to multiply data rates by 2,4 or 8x 

As ISM band is unlicensed it comes with a lot of interference

#### 2.4 vs 5 GHz
* 2.4 has greater range and better propagation through obstacles
* 2.4 is more crowded
* 5 GHz has higher throughput 
* Clients may only have 2.4 compatible devices

#### Site Survey

* Site surveys should be carried out for WiFi networks 
* The purpose is to find the best placement of APs for maximum coverage of the required area, and minimum leakage outside it 
* It should also discover potential sources of interference 
* A WLC  an manage channel allocation and power levels of APs

#### Wireless Security 
- WiFI coverage can leak outside the desired area 
- End stations do not need physical access to join the network
- This can make it more vulnerable to attack 
- Strong authentication and encryption techniques should be used 

#### Wireless Security Standards 
- WEP - WPA - WPA2 - WPA3 

**WPA Personal** - uses pre-shared keys (PSKs)
**WPA Enterprise** - uses a AAA server 















