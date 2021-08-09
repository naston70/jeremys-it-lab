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


