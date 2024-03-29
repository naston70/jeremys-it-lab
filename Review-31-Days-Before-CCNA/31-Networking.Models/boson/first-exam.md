## First Exam

Exam Mode: Study Mode
Exam Bank: Random Exam
Result   : FAIL

#### Review of Incorrect Questions

1.
VLAN Hopping  - An attacker send double tagged 802.1Q frames over a trunk link
MAC Flooding  - An attacker sends traffic out every port on a switch
ARP Poisoning - Attacker intercepts traffic intended for another recipient
MAC Spoofing  - An attacker identifies itself using the address of another host
DHCP Spoofing - An attacker installs a rogue server on the network

4.
A host configuration with the Internet IP 172.16.12.10, subnet of 255.255.255.240 and default gateway of 172.16.12.1 is valid for hosts on 172.16.12.0/28. In this scenario, the /28 is CIDR = 255.255.255.240.

The /28 means 28 bits are used for the network portion of the address. 4 bits remain for host addresses (2**4) = 16 addresses are available on the subnet. 14 are usable. Therefore .10 is in the valid range 

5.
A company that uses a service providers infrastructure, programming tools and programming languages to develop and server cloud-based applications is an example of a Platform as a Service (PaaS)

6.
Routers are unable to form an adjacency because the OSPF areas must match. Although it is possible to configure multi-area OSPF, the OSPF areas on adjacent interfaces must match in order for two OSPF routers to form an adjacency

8.
Switches uses destination MAC addresses to make forwarding decisions.

9.
The ```show ip nat translations``` command displays mapping between internal and external IP addresses when NT is configured on a router. NAT translates between public and private IP addresses to enable hosts on a privately addresses network to access a public network such as the internet. By default NAT provides only a one-to-one mapping of addresses. If multiple hosts require simultaneous access of the public network, NAT must be configured to use either a pool of public IP addresses or NAT overloading.

The ```show ip nat translations``` command displays five fields of information for each NAT translation session:
* Protocol 
* Inside global - displays an IP that represents an inside host as seen by hosts on the outside network
* Inside local - displays the IP address configured on a host on the local network
* outside local - displays the IP address of a host on the outside network as seen from a host on the inside network 

10.
EIGRP supports unequal-cost load balancing.
OSPF only supports equal cost 
RIP only supports equal cost 

12.
Authentication and resource reservation are functions performed by a wireless LAN controller in a split-MAC deployment. In a Cisco Unified Wireless Network deployment, the MAC functions that are normally handled by a single device in an autonomous wireless network are distributed between lightweight APS and WLCs. A WLC handles tasks that are not time sensitive such as security management, lightweight AP config and client load balancing. The WLC is also responsible for client association requests, data encapsulation, client auth, key exchange, security policy enforcement and RF management.

By contrast, the functionality provided by the lightweight AP includes handling the real-time processing of data, such as sending and receiving 802.11 traffic, responding to beacon and probe messages, encryption and packet prioritization. 

14.
An interface identifier in EUI-64 format is created by taking the first half of the hosts MAC address, which is referred to as the OUI, adding the HEX number FFFE, and then appending the last half of the hosts MAC address. The seventh binary bit in the OUI, which is referred to as the U/L bit, is then flipped.

15.
FTP uses TCP for reliable transfer. FTP uses TCP ports 20 and 21

16.
You want to configure an IP for a routers serial interface that will provide a point to point connection to a branch office.
Which IP addresses are you most likely to choose?
- 172.16.17.24/30
- 172.16.17.19/30
- 172.16.17.20/30
- 172.16.17.23/30
- 172.16.17.18/30

In this scenario you should first determine whether each address is a network address, broadcast address or a host address. A /30 subnet mask is 255.255.255.252 indicating 30 bits used for the network portion and 2 bits remain for the host portion 2**2 - 2 = 2.

17.
**CDP:** 
- 60 second update frequency
- has 180 hold timer
- enabled by default
- layer 2 protocol
- proprietary protocol 
- can convey vtp

**LLDP:**
- has a 30 second update frequency
- has a 120 second hold timer
- is disabled by default
- is a layer 2 protocol 
- is an open-standard

19.
After restarting OSPF process will a router ID of 5.5.5.5 remain?

No as issuing the ```no router-id 5.5.5.5```removes the manual router ID configuration for OSPF process 100 on RouterA. The IP address of 10.10.10.10 is the highest IP address assigned to a loopback on router A. If no manual router ID is configured on an OSPF router, the router will use the highest IP address assigned to a loopback interface as the router ID. If no loopback interfaces have been configured with IP addresses, the router will use the highest IP address assigned to an active physical interface.

21.
- Local host routes are marked with an L
- Manually configured IPs with /32 are considered connected and marked with a C
- Routes with an O are OSPF, routes with D are EIGRP, 
- Routes with an S are static routes 
- Routes marked with a * are default routes 

25.
* Platinum wireless prioritizes VoIP traffic on a WLAN
* Gold wireless QoS level prioritizes video traffic
* Silver QoS level is default setting on a Cisco WLC 
* Bronze QoS provides the lowest bandwidth and is typically of guest services

27.
TCP - HTTP, FTP, SMTP
UDP - SNMP, DHCP, TFTP

UDP and TCP - DNS 

28.
Which of the following is not a type of IEEE 802.11 management frame?
* power-save poll
* probe request
* association response 
* beacon 

A power-save poll frame is not a type of IEEE management frame, it is a control frame. 
There are three general types of 802.11 frames, cont7rol, management and data. Each of these general types is further subdivided into several more granular subtypes. The 2-byte Frame Control (FC) field of the 802.11 header is used to identify the type and subtype of each frame.

Management frames are used to manage the connection between an access point (AP) and wireless client. Numerous types of management frames exist, including beacons, probe responses, association requests, responses, auth requests and responses and more. Each has a specific duty necessary to initialize, maintain or terminate wireless transmissions between an AP and client.

Control frames are used to manage access to the wireless medium. Numerous types of control frames exist, including RTS (ready to send), CTS (clear to send), ACK (acknowledgements)

Data frames are used to convey user data through the wireless network. Numerous types of this frame exist

34.
IPv6 address types:
* fc00::/7 = unique local addresses:
These addresses are reserved for home and enterprise use and not in public address space 

* fe80::/10 = Link Local Addresses
These addresses are used on a single link or a non-routed common access
network, such as an Ethernet LAN. They do not need to be unique outside of that link

* 2000::/3 = Global unicast
Global IPs that can be found using WHOIS

* ff00::/8 = Multicast 
used to identify multicast groups. 

36.
By default, Cisco phones assign a Class of Service (CoS) priority value of 0 to traffic receives from a host on its access port.

40.
 Administrative distances:

 directly connected route = 0 
 static route             = 1
 EIGRP summary route      = 5
 eBGP                     = 20
 EIGRP                    = 90
 IGRP                     = 100
 OSPF                     = 110
 IS-IS                    = 115
 RIP                      = 120

48.
HSRP uses the virtual MAC 0000.0c07.ACxx where xx is the group number in hex format

51.
A cloud based access point deployment enables a Cisco Meraki AP to automatically configure itself when it is connected to a network. 

53.
EIGRP uses the lowest segment bandwidth and the sum of the segment delays in the calculation of metric weights.

54.
FlexConnect ACLs are supported on the native VLAN. FlexConnect ACLs are similar to traditional ACLs in that they are rules that permit or deny traffic from a given source to a given destination. However FlexConnect ACLs are configured on Cisco wireless LAP VLAN interfaces if the lightweight AP is operating in FlexConnect mode. 

58.
Which of the following are used by WPA2 to provides MICs and encryption?

TKIP, GCMP, CCMP, AES, RC4

AES and CCMP are used by WPA2 to provide message integrity checks (MICs) and encryption. WPA2 also uses CCMP to provide encryption. CCMP is an encryption mechanism that uses block ciphers. In WPA2 CCMP is used by AED during encryption. The WPA2 encryption process is thus sometimes known as AES-CCMP.

RC4 is used in WEP 
TKIP is used in WPA 

59.

APIs for appropriate Interfaces:
**Northbound:**
OSGi and REST 

**Southbound:**
NETCONF, OnePK, Openflow, OpFlex

Northbound APIs enable an SDN controller to communicate with applications in the application plane:
OSGi is a JAVA based API architecture northbound
REST is a northbound API 

A southbound API is sometimes called a SBI - SBIs enable an SDN controller to communicate with devices on the network data plane

60.
PSK should be the key management method selected from the AUTH KEY MGMT drop-down list box if you want to configure the WPA2 passphrase in ASCII. PSK configures WPA or WPA2 to use the Pre-shared Key method.

61.
Which of the following does RED and WRED address?

bandwidth guarantees, bandwidth starvation, tail drop, strict-priority queuing

Random Early Detection (RED) and Weighted RED (WRED) are congestion avoidance mechanisms that address tail drop, which occurs when new incoming packets are dropped because a routers queues are too full to accept them. Tail drop particularly affects TCP traffic because when TCP packets are dropped, the sources of the traffic must resend. TCP also detects congestion and slows down.
RED will randomly drop packets at an increasingly faster rate. WRED improves upon RED by employing different tail drop thresholds for each IP precedence or DSCP value, where lower priority traffic will be more likely dropped than higher priority.

62.
On which interfaces is the OSPF nonbroadcast network type enabled by default (2)

X.25, PPP, HDLC, Frame Relay, Ethernet, FDDI

*Answer A and D*

The OSPF nonbroadcast type is enabled by default on Frame Relay and X.25 interface. If the ```ip ospf network``` command has not been issued for an OSPF instance, the default network type will be used. The default OSPF network type depends upon the type of network to which the interface is connected.

There are 5 OSPF network types:

- Broadcast 
- Nonbroadcast 
- Point-to-Point 
- Point-to-multipoint broadcast
- Point-to-multipoint nonbroadcast 

The OSPF broadcast network type is enabled by default on FDDI and Ethernet interfaces. On broadcast networks, DR and BDR elections are performed. 

65.
When a Catalyst 2950 switch is powered up with factory settings, the default VTP mode is Server Mode. Server mode is required on at least one switch on a network where VTP is being implemented. Server mode allows to create, modify or delete any VLAN in the VTP domain

69.

Logging a verified users file access is a form of accounting. Accounting is a feature of AAA systems that enables admins to track resource usage across a network.
- authentication = verifying a users identity
- authorization  = verifying the level of access configured for a user
- accounting     = recording the use of resources

70.

The EIGRP routing table contains only successors, which are the best next-hop routes to a destination. EIGRP routers maintain a routing table, topology table and a neighbor table. 

71.
Which config management tool accepts inbound requests from agents by HTTPS on port 8140?

Chef, Ansible, Puppet, Salt 

Answer = Puppet

Puppet is the tool that accepts inbound requests via HTTPS on TCP port 8140. 
Chef uses 443 (traditional https) config in cookbooks
Ansible uses SSH on port 22 configs stored in playbooks
Salt use 4505 and 4506

72.
You should use ```enable secret level 7 cisco``` to encrypt the password that is required to access privilege level 7.

79.

Log Levels 

0 - emergency
1 - alert
2 - critical
3 - errors
4 - warnings 
5 - notifications 
6 - informational 
7 - debugging

83.
Which is Cisco proprietary FHRP that elects an AVG and up to four primary AVFs?

HSRP, GLBP, LACP, VRRP

GLBP is a proprietary first hop routing protocol that elects an active virtual gateway (AVG) and up to four active virtual forwarders (AVFs).

89.
You are disabling DTP on a port when using the switchport nonegotiate command. In addition by assigning the port to unused VLAN 4 this is further best practice.
Moving an unused port to an unused vlan creates a logical barrier that prevents rogue devices from communicating on the network. furthermore, switchport mode access and then shutdown the port with shutdown command.

91.
Example of authentication by something you have:

pin, password, driving license, fingerprints

Auth by something you have is the process of identity by using a device or document that you carry with you such as a fob, smart card, license or phone.

Auth by something you know is a PIN or Password

Auth by something you are can be fingerprints, iris or retina

96.
Class A - 10.0.0.0 to 10.255.255.255
Class B - 172.16.0.0 to 172.31.255.255
Class C - 192.168.0.0 to 192.168.255.255

97.
In a controller based network, the functions of which of the following protocols are moved to a centralized controller?

In a controller-based network, the functions of OSPF or other routing protocols will be moved to a centralized controller. Routing protocols like OSPF operate in the control plane of a traditional distributed network. In a controller-based network, such as a SDN network, the control plane is centralized. OSPF makes routing decisions for packets that require routing among Layer 3 devices. In a controller-based network, the decision-making logic is either moved to a central controller or monitored by a central controller.