## Network Fundamentals

Practice Questions:

**1.0 Network Fundamentals**

**✓ 1.1 Explain the role and function of network components**
    1.1.a Routers
    1.1.b L2 and L3 switches
    1.1.c Next-generation firewalls and IPS
    1.1.d Access points
    1.1.e Controllers (Cisco DNA Center and WLC) 1.1.f Endpoints
    1.1.g Servers

**✓ 1.2 Describe characteristics of network topology architectures**
    1.2.a 2 tier
    1.2.b 3 tier
    1.2.c Spine-leaf
    1.2.d WAN
    1.2.e Small office/home office (SOHO) 1.2.f On-premises and cloud

**✓ 1.3 Compare physical interface and cabling types**
    1.3.a Single-mode fiber, multimode fiber, copper
    1.3.b Connections (Ethernet shared media and point-to-point) 1.3.c Concepts of PoE

**✓ 1.4 Identify interface and cable issues (collisions, errors, mismatch duplex, and/or speed)**

**✓ 1.5 Compare TCP to UDP**

**✓ 1.6 Configure and verify IPv4 addressing and Subnetting**

**✓ 1.7 Describe the need for private IPv4 addressing**

**✓ 1.8 Configure and verify IPv6 addressing and prefix**

**✓ 1.9 Compare IPv6 address types**
    1.9.a Global unicast 1.9.b Unique local 1.9.c Link local 1.9.d Anycast
    1.9.e Multicast
    1.9.f Modified EUI 64

**✓ 1.10 Verify IP parameters for Client OS (Windows, Mac OS, Linux)**

**✓ 1.11 Describe wireless principles 1.11.a Non-overlapping WI-FI channels**    1.11.b SSID
    1.11.c RF
    1.11.d Encryption

**✓ 1.12 Explain virtualization fundamentals (virtual machines).**

**✓ 1.13 Describe switching concepts.**
    1.13.a MAC learning and aging 1.13.b Frame switching
    1.13.c Frame flooding
    1.13.d MAC address table

-------------------------------------------------------------------------------

-------------------------------------------------------------------------------

1. How many broadcast domains are present in the network below?

       ---- HUB = pc1 & pc2
R1 - S1 
       ---- HUB = pc3 & pc4 

A: Only one d¡broadcast domain exists because a PC on the left hun can send an ARP request and the PC on the right hub can hear it. If multiple broadcast domains are desired, VLANs would have to be created and routed. 



2. How many potential collision domains are present in the network in the same network?

A: There are three potential collision domains. - A collision domain is a network segment in which collision can occure and the colliding frame is created.

3. Which statement is true about collision domains?

A. All computers in the collision domain have the potential to have a frame collision.
B. All computers in the collision domain have the potential to receive layer 2 broadcast messages.
C. All computers in the collision domain have the potential to receive layer 3 broadcast messages.

A: A - A collision domain is defined as a group of computers that can potentially have a frame collision. Adding switches that can negotiate full-duplex and forward/filter fixes these issues. 

4. In the following exhibit, which would be true if the hub was replaced with a switch?
(HUB with 4 devices connected)
A. The number of collision domains would increase. 
B. The number of collision domains would decrease. 
C. The number of broadcast domains would increase. 
D. The number of broadcast domains would decrease.

A. A - Currently all computers are in one collision domain, replacing the hub with a switch will create four seperate potential collision domains. The number of collision domains would only decrease if you swapped a switch for a hub, creating only on collision domain. The number of broadcast domains would be unaffected using either a switch or hub unless a router was used for routing between VLANs

5. Considering the following exhibit, which of the following is a correct statement?
A. One collision domain exists with one broadcast domain.
B. Two collision domains exist with one broadcast domain. 
C. Three collision domains exist with two broadcast domains. 
D. Seven collision domains exist with two broadcast domains.

A: C. In the network there are two broadcast domains, VLAN1 and VLAN2. In each broadcast domain there is a single collision domain, along with the collision domain between the switch and router. Therefore there are three collision domains and two broadcast domains

6. Which component acts as a distribution switch for the physical data center?
A. Top of Rack switch 
B. End of Row switch 
C. Core switch
D. Virtual switch

A: B - The End of Row (EoR) switch acts as a distribution switch for the Top of Rack (ToR) switches. A ToR switch will sit at the top of the rack and create an access method for all equipment in the rack. 

7. Which advantage(s) are gained using switches?
A. Low latency
B. Software switching 
C. High cost
D. All of the above

A: A - Switches allow for low latency because frames are forwarded with ASIC hardware based switching and have low cost. Software switching is only used by legacy bridges and virtual switches. Software switching can actually create latency. 

8. Which is a correct statement when hubs are replaced with switches?        A. The replacement increases collision domains.
B. The replacement decreases collision domains.
C. The replacement increases broadcast domains.
D. The replacement decreases broadcast domains.

A: A - The replacement of hubs with switches increase collision domains and effectively increases bandwidth. 

9. Which is a function of a layer 2 switch?

A. Forwarding the data based upon logical addressing
B. Repeating the electrical signal to all ports
C. Learning the MAC address by examining the destination MAC addresses
D. Determining the forwarding interfaces based upon the destination MAC address and tables

A: D - The switch learns MAC addresses based upon incoming ports and examination of the source MAC address. It will build a MAC address table for future lookups. It then determines the forwarding interface based upon the destination MAC address contained in the frame.

10. What is a reason a network administrator would segment a network with a switch?
A. Create more broadcast domains 
B. Create isolation of ARP messages 
C. Create fewer collision domains 
D. Isolate traffic between segments

A: D - The switch creates micro-segmentation, which in turn isolates traffic between two talking computers from other computers that are not part of the communications. This in turn increase bandwidth for the computers that are not part of the communications between the two talking computers. The creation of broadcast domains can only be achieved with the addition of VLANs and a router. The isolation of ARP messages can only be achieved by the creation of broadcast domains. 

11. What is the maximum wire speed of a single port on a 48-port Gigabit Ethernet switch?

A. 1,000 Mb/s 
B. 2 Gb/s
C. 48 Gb/s
D. 96 Gb/s

A: A - Wire speed of a single port would be 1Gb/s or 1000 Mb/s. Theoretically a port can transmit and receive simultaneously 1 Gb/s but the wire speed refers to a single direction. 


12. Which statement describes the micro-segmentation that a switch provides?

A. All of the ports on the switch create a single collision domain.
B. Each port on the switch segments broadcasts.
C. Each port on the switch creates its own collision domain.
D. Each port on the switch creates an isolation for layer 2 broadcasts. 

A: C - Each port on switch creates its own collision domain. An increase in collision domains raises bandwidth since each port creates its own segment and isolates possible collisions on other ports. All the ports on a hub will create a single collision domain, in which a signal from one computer can and will collide with another. Each port on the switch will not segment broadcasts unless each port is assigned a different VLAN, which is not common practice. Although each port on a switch will create a collision domain it does not stop layer 2 broadcasts from being forwarded on all ports.

13. Given the information in the following exhibit, which statement is true when Computer A needs to communicate with Computer F?
A. Switch A and Switch B will flood the frame across all ports.
B. Only Switch A will flood the frame across all ports.
C. Only Switch B will flood the frame across all ports.
D. Switch A will flood the frame across all ports, Switch B will forward traffic only to Computer F’s port.

A: B - SInce the MAC address table is empty on Switch A, Switch A will flood the frame to all ports on the switch. This will include the router attached to interface Fa0/3. However, a router does not perform forward/filter decisions, so the frame will not be flooded any further on Router A. Switch A will forward the frame to all ports, but the router will not forward the frame to onto the segment where Switch B is located. Switch B will never see the frame from Switch A as Router A segments the two networks

14. When firewalls are placed in a network, which zone contains Internet- facing services?
A. Outside zone
B. Enterprise network zone
C. Demilitarized zone
D. Inside zone

A: C - The DMZ is where Internet facing servers/services are placed. Teh outside zone is where the public Internet connection is connected and it is the least trusted. The enterprise network is considered the inside zone. The inside zone is considered to be highest trusted network as it is the internal network an administrator controls 


15. According to best practices, what is the proper placement of a firewall?
A. Only between the internal network and the Internet 
B. At key security boundaries
C. In the DMZ
D. Only between the DMZ and the Internet

A: B - Firewalls should always be placed at key security boundaries, which can be the Internet and your internal network. However, proper placement is not exclusive to the boundaries of the Internet and internal networks. Ie. it could be placed between two internal networks. The Demilitarized zone (DMZ) is segment of a firewall where Internet-facing services are placed. Firewalls are normally not placed only between the DMZ and the Internet because most networks have an internal network 

16. Which is a false statement about firewalls?
A. Firewalls can protect a network from external attacks.
B. Firewalls are commonly deployed to protect a network from internal attacks.
C. Firewalls can provide stateful packet inspection.
D. Firewalls can control application traffic.

A: B - Firewalls are not commonly deployed to provide protection from internal attacks on internal resources. They are designed to protect networks from external attacks or attacks emanating from the outside or directed toward the Internet. Firewalls normally provide stateful packet inspection. Firewalls can also control application traffic by port number and higher layer attributes

17. Which of the following statements does not represent the logical management of a firewall?
A. All physical access to the firewall should be tightly controlled.
B. All firewall policies should be documented.
C. Firewall logs should be regularly monitored.
D. Firewalls should allow traffic by default and deny traffic explicitly.

A: A - All physical access to a firewall should be tightly controlled so that it is not tampered with, which could allow external threats to enter the network. Physical access to the firewall is a security principle and therefore not a consideration for the management of a firewall. All firewall policies should be documented as a part of the firewall management process, firewall logs should be regularly monitored for suspicious activity as part of the firewall management process. 

18. What is the reason firewalls are considered stateful? 
A. Firewalls keep track of the zone states.
B. Firewalls keep accounting on the state of packets. 
C. Firewalls track the state of a TCP conversation. 
D. Firewalls transition between defense states.

A: C - Firewalls keep track of the TCP conversation before and after the three way handshake. This is done so that an attack on the TCP/UDP flow is not executed; in addition, DoD attacks can be thwarted, such as a SYN flood. ***Zone state*** is terminology that is used with firewalls; therefore it is an incorrect answer. Firewalls do not protect by keeping statistics or accounting information for the state of packets. Firewalls do not transition between defense states.

19. You have an Adaptive Security Appliance (ASA) and two separate Internet connections via different providers. How could you apply the
same policies to both connections?
A. Place both connections into the same zone.
B. Place each connection into an ISP zone.
C. Apply the same ACL to both of the interfaces. 
D. Each connection must be managed separately.

A: A - ASAs allow for zones to be created and the connections applied to the zones. This methodology allows for security rules to be applied uniformly to the outside zone. There is no such thing as an ISP zone. You can apply an ACL to the zone but not directly to the interface. Each connection can be managed by a group once it is added to the same zone. 


20. Why should servers be placed in the DMZ?
A. To allow unrestricted access by Internet clients
B. To allow access to the Internet and the internal network 
C. To allow the server to access the Internet
D. To restrict the server to the Internet

A: B -  Servers should be placed in the DMZ so they can access both the inside zone and the outside zone. This would allow a server, such as a web server, to allow client access from the Web. Rules could also be applied so that the server could allow access to data from within the internal network. Placing the servers into the DMZ will give flexibility to apply rules for external access on the Internet and rules for internal access on the internal network. 

21. Which type of device will detect but not prevent unauthorized access? 
A. Firewall
B. IPS
C. IDS
D. Honeypots

A: C - An IDS, Intrusion Detection System, will detect unauthorized access. However it will not prevent access. It is a form of audit control in a network. A firewall will protect your network from attack by placing rules on connection as to how people can connect as well as which traffic can pass. An IPS, will detect and notify an admin to the presence of an Intrusion

22. Which term describes what it is called when more than one wireless access point (WAP) covers the same SSID?
A. Broadcast domain 
B. Basic service set 
C. Extended service set 
D. Wireless mesh

A: C - When more than one WAP covers the same SSID, it is called an extended service set. A wireless LAN controller coordinates the cell or coverage area so the same SSID is on two different channels. 
A broadcast domain is one single layer 3 broadcast network in which layer 3 broadcasts will traverse. 
A basic service set (BSS) is used when a WAP covers a single SSID, such as wireless in the home. 
A wireless mesh is used when an Ethernet cable cannot be run to each WAP. The WAPs will use one frequency to connect to each other for the backhaul of the data while using another frequency to serve clients

23. Which protocol allows a Lightweight AP (LWAP) to forward data to the wired LAN?
A. Spanning Tree Protocol (STP)
B. Bridge Protocol Data Units (BPDUs)
C. Orthogonal Frequency Division Multiplexing (OFDM)
D. Control and Provisioning of Wireless Access Points (CAPWAP)

A: D - Control and Provisioning of Wireless Access Points (CAPWAP) is a protocol thats responsible for provisioning of LWAPs and forwarding of data to the wireless LAN controller. 

24. Which component allows wireless clients to roam between access points and maintain authentication?
A. Basic service set
B. Extended service set
C. Wireless LAN controller 
D. Service set ID 

A: C - Wireless LAN Controller is responsible for centralized authentication of users and/or computers on a wireless network. When a wireless device is roaming, the WLC is responsible for maintaining the authentication between access points. A BSS is normally served by a single WAP for a single SSID. An extended service is used when two or more WAPs provide coverage for one or more SSIDs. SSID is the name beaconed to wireless clients 

25. Why would you use Multiprotocol Label Switching (MPLS) as a connectivity option?
A. You need support for multicast packets.
B. You need support for both IPv4 and IPv6 packets. 
C. You need a high amount of bandwidth.
D. You require encryption.

A: B - The requirement for multiple protocols is a compelling reason to use MPLS. The protocols moving across MPLS nodes are irrelevant to the technology. This is because layer 3 information is not examined to route packets. The use of MPLS can be configured to support multicast packets, but this is not the primary driver in selecting MPLS. The use of MPLS does not give higher bandwidth and MPLS supports encryption just as any other WAN technology 

26. What is a service-level agreement (SLA) for network connectivity?
A. It is an agreement of bandwidth between the ISP and the customer.
B. It is a quality of service agreement between the ISP and the customer.
C. It is an agreement of uptime between the ISP and the customer.
D. All of the above.

A: D -  A service-level agreement (SLA) is a contracted agreement between the ISP and the customer. This agreement defines the level of service. SLAs are based on uptime, QoS and bandwidth and any other stipulations. 

27. Which is a valid reason to implement a wireless LAN controller?
A. Centralized authentication
B. The use of autonomous WAPs 
C. Multiple SSIDs
D. Multiple VLANs 

A: A - Centralized authentication of clients is a valid reason to implement a WLC. Although a WLC makes it easier to implement multiple SSIDs and VLANs, this can be performed with autonomous WAPs, each performing its own authentication. The use of autonomous WAPs negates the reasons you would use a WLC because each WAP would be independently managed and no coordination would exist between the autonomous WAPs. The use of multiple SSIDs can be achieved with an autonomous WAP without a WLC. Multiple VLANs can also be used with an autonomous WAP without WLC. 

28. Which allows for seamless wireless roaming between access points?        A. Single SSID
B. Single service set
C. 802.11ac
D. Wireless LAN controller

A: D - A wireless LAN controller keeps track of which LWAP a client has associated it with and centrally forwards the packets to the LWAP that appropriate for a client to access while roaming.

29. Which is one of the critical functions that a wireless LAN controller performs?
A. Allows autonomous WAPs
B. Synchronizes the WAPs with the same IOS 
C. Triangulates users for location lookups
D. Allows for the use of all frequency channels

A: B - When WAPs are introduced to the wireless LAN controller, the WLC is responsible for synchronizing the WAPs to a standardized IOS. This allows for uniform support and features of the wireless system and is dependent on the model of WAP. 

30. Which should only be performed at the core layer?                        A. Routing
B. Supporting clients 
C. Configuring ACLs 
D. Switching

A: D - Only switching between campus switches should be performed at the core layer. Nothing should be done to slow down forwarding of traffic. Routing of data should be performed at the distribution layer of the cisco three-tier model. Supporting clients should be done at the access layer and configuration of access should be done at the distribution layer

31. Which network topology design has a centralized switch connecting all of the devices?
A. Star topology
B. Full mesh topology 
C. Partial mesh topology 
D. Hybrid topology

A: A - A star topology has a centralized switch connecting all of the devices outward like a star. A full mesh topology allows for a decentralized switching design, where any link failure will not affect switching. A partial mesh topology is normally performed between the layers of core, distribution and access to allow for a single link failure while maintaining switching services. A hybrid is where several topolgies are employed. 

32. Which is a direct benefit of a full mesh topology?
* A. Increased bandwidth
* B. Increased redundancy
* C. Decreased switch count
* D. Increased complexity

A: B - Increased redundancy of connections is a direct benefit of a full mesh topology. 

33. Where is the hybrid topology most commonly seen in the three-tier design model?
A. Core layer
B. Distribution layer 
C. Access layer
D. Routing layer

A: C - Devices are connected in a star topology and the access layer switches are partially meshed to the distribution layer switches. 

34. Where is the full mesh topology commonly seen in the three-tier design model?
A. Core layer
B. Distribution layer
C. Access layer
D. Routing layer

A: B -  Distribution layer switches are fully meshed for redundancy. 

35. Where is the star topology most commonly seen in the three-tier design model?
A. Core layer
B. Distribution layer 
C. Access layer
D. Routing layer

A: A - Core layer switched are commonly set up in a star topology. This is because core layer switches connect multiple campuses via distribution layer switches. The distribution layer is normally implemented with a full mesh topology, the access layer is normally implemented with a hybrid topology. 


36. Which topology does the collapsed core layer switch use in a two-tier design model?
A. Star topology
B. Full mesh topology 
C. Partial mesh topology 
D. Hybrid topology

A: The collapsed core layer switch uses a star topology connecting outward to the access layer switches. This design is often found in small enterprise and single campus design. The full mesh topology is normally found at the distribution layer in the Cisco three-tier design model. 

37. The two-tier design model contains which layer switches? 
* A. Core, distribution, and access
* B. Core and distribution
* C. Distribution and access
* D. Internet, core, distribution, and access

A: C - The two tier, or collapsed core, model contains only the distribution and access layer switches. The three-tier design model contains the core, distribution, and access layer switches. 

38. You have one campus, which contains 2,000 PCs, and each edge switch will contain 25 to 40 PCs. Based on this layout, which design model should be used?
A. Collapsed core model 
B. Three-tier model
C. DOD model
D. Access model

A: A - Based on the layout of your network, the collapsed core model is the most appropriate model to design. If at a later time other campuses are joined to the network, the core layer can be added. The three-tier model is better situated for a network with multiple campuses.


39. Which is an accurate statement about the collapsed core design concept?
A. It is best suited for large-scale networks. 
B. It allows for better bandwidth.
C. It is best suited for small enterprises.
D. It bottlenecks bandwidth.

A: C - Best suited for a small enterprise. It can later be expanded out to a three tier model as an enterprise grows in size. 

40. Access layer switches in the three-tier design model perform which task?
A. Connect to other switches for redundancy 
B. Connect to users
C. Connect campuses
D. Connect to the Internet

A: - B

41. Distribution layer switches in the three-tier design model perform which task?
A. Connect to other switches for redundancy 
B. Connect to users
C. Connect campuses
D. Connect to the Internet

A: - A

42. Core layer switches in the three-tier design model perform which task?    A. Connect to other switches for redundancy
B. Connect to users
C. Connect campuses
D. Connect to the Internet

A: - C 

43. You have four campuses, each containing 500 PCs, and each edge switch will contain 20 to 30 PCs. Based on this layout, which design model should be used?
A. Collapsed core model 
B. Three-tier model
C. DoD model
D. Access model

A: - B

44. Which layer in the three-tier model is where redistribution of routing protocols should be performed?
A. Core layer
B. Distribution layer 
C. Access layer
D. Routing layer

A: - B, It should never be performed at the access or core layers. The core layer is for basic routing and switching without slowing down any of the backbone.

45. Which layer in the three-tier model is where collision domains should be created?
A. Core layer
B. Distribution layer 
C. Access layer
D. Routing layer

A: - C, the access layer. This is called network segmentation. 

46. In Cisco’s three-tier architecture, the links between the distribution layer switches indicate what kind of topology?
A. Full mesh topology 
B. Partial mesh topology 
C. Star topology
D. Ring topology

A: - B.
The distribution layer is a partial mesh topology. Links between the distribution switches and core switches are multi homed to each device for redundancy. Also the links between the distribution switches and access switches are multi homed to each device for redundancy. Although this might seem to be a full mesh topology, the distribution switches are not connected to each other. A full mesh topology can often be found between the distribution and core layers. The core layer uses a star topology in a collapsed core design to connect lower layer switches. 

47. Which technology provides for a hub-and-spoke design?
A. E-Tree services 
B. Wireless WAN 
C. E-Line services 
D. E-LAN services

A: - A. The E-Tree services of Metro Ethernet allow for a root to be established to server the remote sites or leaf endpoints. The root can communicate to the leaf endpoints and the leaf endpoints can communicate to the root. However, the leaf endpoints cannot communicate with each other. 

48. Which is a typical use case for hub-and-spoke WAN design?
A. Connections for an enterprise spread over a metropolitan area 
B. Connections for an Internet service provider to its customers 
C. Connections between two or more corporate locations
D. Connection internally inside of a service provider’s network

A: - B. The most common hub and spoke WAM design is the way an ISP is connected to its customers. The Internet connection is located centrally in a common physical location. All lines connect out from this point in a hub and spoke design. 

49. Which WAN connectivity technology is always configured in a hub-and-spoke topology?
A. IPsec
B. MPLS
C. DMVPN
D. Metro Ethernet

A: - C. The Cisco Dynamic Multipoint VPN is always configured in a hub and spoke topology. The central router created a multiport GRE connection between all of the branch routers. 

50. Which sub-protocol inside of the PPP suite is responsible for authentication?
A. MPLS 
B. NCP 
C. LCP 
D. ACP

A: - C, The Link Control Protocol provides the authentication phase of a PPP connection 

51. Which encapsulation protocol is used with PPP to transmit data over serial links?
A. PPPoE 
B. HDLC 
C. MPLS 
D. X.25

A: - B, The HDLC protocol is used as the encapsulation method for serial links. This protocol is the open standard HDLC compared to the native Cisco proprietary version. 

52. Which authentication method used with PPP uses a nonce (random number) to hash the password and prevent replay attacks?
A. PAP 
B. PSAP 
C. CHAP 
D. LDAP

A: - C, the Challenge handshake authentication protocol (CHAP) works by sending a random number called the challenge. This challenge is received by the authenticating router and used to hash the password. The password is transferred to the challenging router ans authenticates the authenticating router. 

53. Which sub-protocol inside of the PPP suite facilitates multi-link connections?
A. MPLS 
B. NCP 
C. LCP 
D. ACP

A: - C, The Link Control Protocol provides the facility for multi-link 

54. Which is a benefit of using MLPPP?
A. Simplified layer 3 configuration
B. Does not require routing protocols
C. Does not require authentication protocols 
D. Provides end-to-end encryption

A: - A, MultiLink PPP simplifies layer 3 configuration. It does this by bundling the connections together at layer 2. It provides a pseudo interface representing the individual interface where all layer 3 configuration is applied. You can use routing protocols with MLPPP, and in larger networks, it is recommended and required. 

55. Which configuration will create the multilink interface for an MLPPP connection to an adjoining router?

A. 
```
RouterA(config)#interface multilink 1 
RouterA(config-if)#encapsulation ppp 
RouterA(config-if)#ppp multilink
RouterA(config-if)#ip address 192.168.1.1 255.255.255.0 
RouterA(config-if)#ppp multilink group 1
```
B. 
```
RouterA(config)#interface multilink 1 
RouterA(config-if)#ppp multilink
RouterA(config-if)#ip address 192.168.1.1 255.255.255.0
```
C. 
```
RouterA(config)#interface multilink 1 
RouterA(config-if)#encapsulation ppp multilink
```
D. 
```
RouterA(config)#interface multilink 1 
RouterA(config-if)#ip address 192.168.1.1 255.255.255.0 
RouterA(config-if)#ppp multilink group 1
```
A: - A, The pseudo interface must be created first with the command [interface multilink 1]- Then the encapsulation set to PPP. 


56. You need to set up PPP authentication for RouterA. The adjoining router is named RouterB, and both routers will have a matching password of cisco. Which commands will achieve this?
A. 
```
RouterA(config)#username RouterA password cisco 
RouterA(config)#interface serial 0/1/0 
RouterA(config-if)#ppp authentication chap pap
```

B. 
```
RouterA(config)#username RouterB password cisco 
RouterA(config)#interface serial 0/1/0 
RouterA(config-if)#ppp authentication chap pap
```

C. 
```
RouterA(config)#username RouterA cisco 
RouterA(config)#interface serial 0/1/0 
RouterA(config-if)#ppp authentication chap pap
```
D.
``` 
RouterA(config)#username RouterA password cisco 
RouterA(config)#interface serial 0/1/0 
RouterA(config-if)#authentication chap pap
```

A: - B, the first step is to set the username of the other router, RouterB to use for authenticating. Then the interface. All others are incorrect. 

58. You have obtained an ADSL circuit at a remote office for central office connectivity. What will you need to configure on the remote office router?
A. Metro Ethernet 
B. PPPoE
C. PPP
D. MPLS

A: - B, ADSL typically uses PPPoE to authenticate subscribers. The subscribers credentials are often relayed to a RADIUS server for subscription checks. 


59. Amazon Web Services (AWS) and Microsoft Azure are examples of what?
A. Public cloud providers 
B. Private cloud providers 
C. Hybrid cloud providers 
D. Dynamic cloud providers

A: - A, 

60. You are looking to create a fault tolerant co-location site for your servers at a cloud provider. Which type of cloud provider would you be searching for?
A. PaaS 
B. IaaS 
C. SaaS 
D. BaaS

A: - B, Infrastructure As A Service. This allows installation of OS and Applications

61. Which is not a NIST criterion for cloud computing?                         A. Resource pooling
B. Rapid elasticity 
C. Automated billing 
D. Measured service

A: - C, automated billing is not a NIST criterion for cloud computing. The five NIST criteria are i)on-demand self service, ii)broad network access, iii)resource pooling, iv)rapid elasticity, v)measured service 

62. Which term describes the type of cloud an internal IT department hosting virtualization for a company would host?
A. Public cloud 
B. Elastic cloud 
C. Private cloud 
D. Internal cloud

A: - C, Internally hosted clouds are private clouds. Public cloud is open to the public, elastic cloud is a cloud that has elasticity and an internal cloud is not a term for virtualization

63. What is the role of a cloud services catalog?
A. It defines the capabilities for the cloud.
B. It defines the available VMs for creation in the cloud. 
C. It defines the available VMs running in the cloud.
D. It defines the drivers for VMs in the cloud.

A: - B, A cloud services catalog satisfies the self-service aspect of cloud computing. It does this by listing all of the available virtual machines that can be created in the cloud environment, such as web servers, databases and so on. The cloud services catalog does not define the capabilities for the cloud 
since the capabilities could be much more expansive than the cloud services catalog. 

64. A hosted medical records service is an example of which cloud model?      A. PaaS
B. IaaS 
C. SaaS 
D. BaaS

A: - C, its an example of a Software as a Service model. The cloud provider is responsible for the delivery of the software, maintenance of the OS and the maintenance of the hardware. 

65. A hosted environment that allows you to write and run programs is an example of which cloud model?
A. PaaS 
B. IaaS 
C. SaaS 
D. BaaS

A: - A, a hosted service that allows you to develop upon it is an example of the Platform as model. The cloud provider is responsible for the delivery of APIs that developers use to create programs. 

66. Which cloud connectivity method allows for seamless transition between public clouds?
A. MPLS VPN
B. Internet VPN
C. Intercloud exchange
D. Private WAN

A: - C, an Intercloud exchange is a service that connects multiple public clouds through a common private WAN connection. This allows a network engineer to configure the private WAN once and be able to transition between the public clouds on the service side without reconfiguration of the private WAN. 

67. Which option is not a consideration when converting to an email SaaS application if the majority of users are internal? (Choose two.)
A. Internal bandwidth usage
B. External bandwidth usage
C. Location of the users
D. Branch office connectivity to the Internet

A: - A & D. Internal bandwidth usage is not a consideration after conversion to an SaaS application. External bandwidth should be considered since internal users will access the application through the Internet. Location of the users should also be a deciding factor in moving to an SaaS model.

68. You purchase a VM on a public cloud and plan to create a VPN tunnel to the cloud provider. Your IP network is 172.16.0.0/12, and the provider has assigned an IP address in the 10.0.0.0/8 network. What virtual network function (VNF) will you need from the provider to communicate with the VM?
A. Virtual switch
B. Virtual firewall
C. Virtual router
D. Another IP scheme at the provider

A: - C, A virtual router running static NAT to translate the two different IP networks. This type of service is called a virtual network function, or VNF. A virtual switch is built into most virtualization platforms, since layer 2 communications are normally required. A virtual firewall is a piece of software that allows you to protect your virtualization Infrastructure.

69. Which protocol would you use to synchronize the VM in the public cloud with an internal time source at your premises?
A. DNS 
B. rsync 
C. NTP 
D. VPN

A: - C, Network Time Protocol 

70. Which cable type would you use to connect a switch to a switch?
- A. Straight-through cable
- B. Crossover cable
- C. Rolled cable
- D. Shielded cable

A: B, You would use a crossover cable because a switch is a data communications equipment (DCE) Ethernet device. When connecting a DCE Ethernet device to another DCE Ethernet device, you would need to cross the connection with a cross over cable. Newer switches have medium dependent interface-crossover (MDI-X) capabilities and will automatically switch the cable over of a Straight-through cable is used. A Straight-through cable is used to connect a DCE Ethernet device such as a switch to data terminal equipment (DTE) such as a host. 

71. Which fiber optic standard utilizes a 50 micron core?
A. UTP
B. Multi-mode
C. Single-mode 
D. STP

A: - B, Multi-mode fiber can be either 50 microns or 62.5 microns at its core. The maximum distance for a 50 micron fiber is 550 meters utilizing the 1000Base-LX specification. 

72. Which type of cable would be used to connect a computer to a switch for management of the switch?
A. Straight-through cable 
B. Crossover cable
C. Rolled cable
D. Shielded cable

A: - C, although operation of computers connected to a switch uses a straight-through cable, management via the console port requires a rolled cable.

73. Which specification for connectivity is currently used in data centers for lower cost and simplicity?
A. 10GBase-T
B. 40GBase-T
C. 10GBase-CX 
D. 100GBase-TX

A, 10GBase-CX is commonly used in data centers. It is referred to by its nickname of Twinax. It is a fixed balanced coaxial pair that can be run up to 25 meters. 10GBase-T is usually category 6 cable that is nominally run up to 55 meters in length to achieve 10 Gb/s speeds. 

74. If you had an existing installation of Cat5e on your campus, what is the highest speed you could run?
A. 10 Mb/s 
B. 100 Mb/s 
C. 1 Gb/s 
D. 10 Gb/s

A: - C, Cat5e can support up to 1 Gb/s via the 1000Base-T specification.

75. Which statement is correct about straight-through cables and crossover cables?

A. Crossover cables are wired with pins 1 through 8 on one side and 8 through 1 on the other side.
B. Crossover cables are wired with the 568B specification on both sides.
C. Straight-through cables are wired with the 568B specification on one side and the 568A specification on the other side.
D. Crossover cables are wired with the 568B specification on one side and the 568A specification on the other side.

A: - D, crossover cables are wired with the 568B specification on one side and on the other side the 568A specification is used. This change in wiring delivers the TX pair on pins 3 and 6 to the RX pair in pins 1 and 2. Straight-through cables are wired with the 568B specification on both sides.

77. Which device is responsible for adding the label to a MPLS packet? 
A. Customer edge (CE) router
B. Provider edge (PE) router
C. Customer premise switch
D. Label switch routers (LSR)

A: - B, the Provider Edge (PE) router is responsible for adding the MPLS label to a packet. 

78. What is the term that defines the end of the provider’s responsibility and the beginning of the customer’s responsibility?
A. CPE
B. CO
C. Local loop 
D. Demarc

A: - D, The demarc or demarcation point, is the end of the providers responsibility for the connection and the point where the customers responsibility begins. This point is often a physical location where the provider can test their connection and hand off the service to the customer. 

79. What is the speed of a DS1 connection in North America?
 
A. 2.048 Mb/s 
B. 44.736 Mb/s 
C. 1.544 Mb/s 
D. 622.08 Mb/s

A: - C, The speed of a DS1 connection is 1.544 Mb/s, it is also referred to as a T1 connection. European DS1 called an E1 is 2.048 Mb/s. 
80. Which command would you run to diagnose a possible line speed or duplex issue?
A. Switch#show speed
B. Switch#show duplex
C. Switch#show interface status D. Switch#show diagnostics
