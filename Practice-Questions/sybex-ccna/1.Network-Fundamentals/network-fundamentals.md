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
C. Switch#show interface status 
D. Switch#show diagnostics

A: - C, when checking for speed and/or duplex issues, the [show interface status] command will detail all of the ports with their negotiated speed and duplex. 

81, 82 - images

83. You have just resolved a problem and now need to monitor the problem on the interface. How would you reset the error counts for a single interface?
- A. Switch#reset counters interface fast 0/1 
- B. Switch#clear interface fast 0/1
- C. Switch#clear counters interface fast 0/1 
- D. Switch#clear statistics interface fast 0/1

A: - C

84. Interface is showing down, line protocol is down (disabled)
- A. The interface is shut down.
- B. The interface is negotiated at half-duplex.
- C. The interface is operating normally.
- D. The cable is disconnected for the node.

A: - D, the counters on this interface are all nominal, but the interface and line protocol are down/down. This most likely suggests that the cable is disconnected. If the interface was shutdown, it would state that the interface was administratively shut down. 

85. A router is connected to the switch via a Fast Ethernet interface. Intermittently you experience an outage. What should be done first to remedy the problem?
A. The speed and duplex should be set statically. 
B. Change the VLAN to a less crowded VLAN. 
C. Change the switchport mode to a trunk.
D. Set the switchport to auto-negotiate.

A: - A, it is recommended to set all servers and networking hardware statically for speed and duplex. If a network interface flaps, auto-negotiation of speed and duplex will be performed again, which could create a service outage.

86, images

87. You have statically set an interface to 100 Mb/s full-duplex. However, the device you are plugging in will not work. Which command would you use to set speed and duplex back to auto-negotiate?
- A. Switch(config-if)#speed auto 
     Switch(config-if)#duplex auto
- B. Switch(config-if)#speed autonegotiate 
     Switch(config-if)#duplex autonegotiate
- C. Switch(config-if)#switchport autonegotiate
- D. Switch(config-if)#interface autonegotiate

A: - A

88. You have auto-negotiation turned off on the node, but it is turned on at the switch’s interface connecting the node. The interface is a 10/100/1000 Mb/s interface and the node is 100 Mb/s full-duplex. What will the outcome be when you plug in the node?
A. The switch interface will be set to the 100 Mb/s full-duplex. 
B. The switch interface will be set to the 100 Mb/s half-duplex. 
C. The switch interface will be set to the 10 Mb/s full-duplex. 
D. The switch interface will be set to the 10 Mb/s half-duplex.

A: - B, Cisco switches can auto-detect speed, so the speed sensed will be 100 Mb/s. However, if the switch cannot detect the speed, then it will fall back to 10 Mb/s. Duplex is decided upon by bandwidth when IEEE auto-negotiation is turned off. If the speed is 10 or 100 Mb/s, then the duplex will be half duplex, otherwise it will be full-duplex on 1000 Mb/s links.

89. You plug a 100 Mb/s hub into a switch. What is the expected outcome? 
A. The switch interface will be set to the 100 Mb/s full-duplex.
B. The switch interface will be set to the 100 Mb/s half-duplex.
C. The switch interface will be set to the 10 Mb/s full-duplex.
D. The switch interface will be set to the 10 Mb/s half-duplex.

A: - B, hubs do not participate in IEEE negotiation and therefore speed will be detected. However, since duplex cannot be negotiated, 10 and 100 Mb/s will be half duplex 

90. You want to see the status of all speed and duplex negotiations for all interfaces. Which command would you use?
A. Switch#show run
B. Switch#show interfaces counters 
C. Switch#show interfaces status 
D. Switch#show counters interfaces

A: - C, displays port, descriptions, connected status, VLAN, duplex, speed and type of interface.

91. Flow control can be found at which layer of the OSI? 
A. Transport layer
B. Network layer 
C. Data Link layer 
D. Session layer

A: - A, the Transport Layer is responsible for the flow control via TCP/IP protocols of TCP and UDP. The Network Layer is responsible for logical addressing of network nodes. The Data Link layer is responsible for the framing of data and the physical addressing of local nodes. The session layer is responsible for the setup of the dialog between two hosts. 

92. Which protocol requires the programmer to deal with lost segments? 
A. SSL
B. TCP 
C. UDP 
D. NMS

A: - C, User Datagram Protocol does not guarantee segments are delivered 

93. Which is a correct statement about the Transmission Control Protocol (TCP)?
A. TCP is a connectionless protocol.
B. TCP allows for error correction.
C. TCP is faster than UDP.
D. TCP allows for retransmission of lost segments.

A: - D, TCP is a connection based protocol via the three way handshake. It is not faster than UDP. However, it allows for the retransmission of lost segments because of sequences and acknowledgments. TCP does not allow for error correction, only the detection of errors and lost or missing segments.

94. Which statement correctly describes what happens when a web browser initiates a request to a web server?
A. The sender allocates a port dynamically above 1024 and associates it with the request.
B. The receiver allocates a port dynamically above 1024 and associates it with the request.
C. The sender allocates a port dynamically below 1024 and associates it with the request.
D. The receiver allocates a port dynamically below 1024 and associates it with the request.

A: - A, the sender allocates a port dynamically above 1024 and associates it with the request through a process called a handle. This way if a web browser creates three requests for three different pages the pages are loaded into their respective windows. The receiver will respond back to the requesting port dynamically allocated to the request (over 1024); these ports are also known as ephemeral ports. Dynamic allocation is always over 1024, not below 1024, and it is always the responsibility of the sender not the receiver.

95. Which protocol and port number is associated with SMTP? 
A. UDP/69
B. UDP/68 
C. UDP/53 
D. TCP/25

A: - D, SMTP uses TCP port 25 to send mail 

96. How does TCP guarantee delivery of segments to the receiver? 
A. Via the destination port
B. TCP checksums
C. Window size
D. Sequence and acknowledgment numbers

A: - D, TCP guarantees delivery of segments with sequence and acknowledgment numbers. At the Transport layer, each segment is given a sequence number that is acknowledged by the receiver. The source and destination ports are used for the delivery of segments, but they do not guarantee delivery. 

97. When a programmer decides to use UDP as a transport protocol, what is a decision factor?
A. Redundancy of acknowledgment is not needed. 
B. Guaranteed delivery of segments is required.
C. Windowing flow control is required.
D. A virtual circuit is required.

A: - A, when a programmer decides to use UDP, it is normally because the programmer is sequencing and acknowledging datagrams already. The redundancy of acknowledgments at the Transport Layer is not needed. 

98. Which mechanism allows for programs running on a server (daemons) to listen for requests through the process called binding?
A. Headers
B. Port numbers 
C. MAC address 
D. Checksums

A: - B, when a daemon or server process starts, it binds to a port number on which to listen for a request. 

99. Which is a correct statement about sliding windows used with TCP?
A. The window size is established during the three-way handshake.
B. Sliding windows allow for data of different lengths to be padded.
C. It allows TCP to indicate which upper-layer protocol created the request.
D. It allows the router to see the segment as urgent data.

A: - A, the window size, which is a buffer, is established and agreed upon by the sneder and receiver during the three-way handshake. 

100. Why does DNS use UDP for queries?
A. DNS requires acknowledgment of the request for auditing.
B. The requests require flow control of UDP.
C. DNS requests are usually small and do not require connections setup.
D. DNS requires a temporary virtual circuit.

A: - C, DNS requests are usually small and do not require the overhead of sequence and acknowledgment of TCP. 


101. What is required before TCP can begin sending segments?
A. Three-way handshake
B. Port agreement
C. Sequencing of segments
D. Acknowledgment of segments

A: - A, a three-way handshake is required between sender and receiver before TCP can begin sending traffic. During this three-way handshake, the senders window buffer size is synchronized with the receivers window size. 

102. Which class is the IP address 172.23.23.2? 
A. Class A
B. Class B
C. Class C
D. Class D

A: - B, class B

103. Which is the default subnet mask for a Class A address? 
A. 255.0.0.0
B. 255.255.0.0
C. 255.255.255.0 
D. 255.255.255.255

A: - A.

104. Which address is a multicast IP address? 
A. 221.22.20.2
B. 223.3.40.2 
C. 238.20.80.4 
D. 240.34.22.12

A: - C, the multicast range begins with 224 and ends in 239 in the first Octet

105. Which is true of the IP address 135.20.255.255? 
A. It is a Class A address.
B. It is a broadcast address.
C. It is the default gateway address. 
D. It has a default mask of 255.0.0.0.

A: - B.

106. What is the CIDR notation for a subnet mask of 255.255.240.0? 
A. /19
B. /20 
C. /22 
D. /28

A: - B.

107. You have been given an IP address network of 203.23.23.0. You are asked to subnet it for two hosts per network. What is the subnet mask you will need to use to maximize networks?
A. 255.255.255.252
B. 255.255.255.248 
C. 255.255.255.240 
D. 255.255.255.224

A: - A, this will allow for two hosts per network for a total of 64 networks. The formula for solving hosts is 2x - 2 is equal to or greater than 2 hosts, which in this case is 2**2 - 2 = 2. So 2 bits used on the host side, leaving 6 bits for the subnet side. 6 bits + 24 bits = 30 or 255.255.255.252

108. You have been given an IP address network of 213.43.53.0. You are asked to subnet it for 22 hosts per network. What is the subnet mask you will need to use to maximize networks?
A. 255.255.255.252 
B. 255.255.255.248 
C. 255.255.255.240 
D. 255.255.255.224

A: - D, 2**5 = 32 - 2 = 30 so 5 bits for the host portion, 3 bits for network.

109. Which valid IP is in the same network as 192.168.32.61/26? 
A. 192.168.32.59
B. 192.168.32.63 
C. 192.168.32.64 
D. 192.168.32.72

A: - A.

110. You are setting up a network in which you need 15 subnetworks. You have been given a network address of 153.20.0.0, and you need to maximize the number of hosts in each network. Which subnet mask will you use?
A. 255.255.224.0 
B. 255.255.240.0 
C. 255.255.248.0 
D. 255.255.252.0

A: - B. The subnet mask will be 255.255.240.0. To solve for the number of networks the equation is: 2x is equal to or greater than 15 networks. So 2**4 = 16. The 4 bits represent the subnet side; you add the 4 bits to the 16 bits of the class B subnet which is 16 + 4 = /20 255.255.255.240


111. An ISP gives you an IP address of 209.183.160.45/30 to configure your end of the serial connection. Which IP address will be on the side at the ISP?
A. 209.183.160.43/30 
B. 209.183.160.44/30
C. 209.183.160.46/30
D. 209.183.160.47/30 

A: C, the valid range is 45-46, both IPs are part of the .44/30 network

112.113 images

114. Which subnet does host 131.50.39.23/21 belong to? 
A. 131.50.39.0/21
B. 131.50.32.0/21 
C. 131.50.16.0/21 
D. 131.50.8.0/21

A: - B, The /21 subnet mask has subnets in multiples of 8. So the networks would be 131.50.8.0/21, 131.50.16.0/21, 131.50.24.0/21, 131.50.32.0/21 and 131.50.16.0/21. The IP address .39.23 would belong to the 131.50.32.0/21 network with a range of 131.50.32.1 - 131.50.39.254


115. A computer has an IP address of 145.50.23.1/22. What is the broadcast address for that computer?
A. 145.50.254.255 
B. 145.50.255.255 
C. 145.50.22.255 
D. 145.50.23.255

A: D. The network for the computer with an IP address of 145.50.23.1/22 is 145.50.20.0/22. Its valid range is 145.50.20.1 to 145.50.23.254; the broadcast address for the range is 145.50.23.255. 

116. Which RFC defines private IP addresses?
A. RFC 1819
B. RFC 1911 
C. RFC 1918 
D. RFC 3030

A: - C.

117. What is a major reason to use private IP addressing?
A. It allows for the conservation of public IP addresses.
B. Since private IP addresses are non-routable on the Internet, they are secure.
C. It keeps communications private.
D. It allows easier setup than public IP addresses.

A: - A.

118. What is required when using private IP addresses to communicate with Internet hosts?
A. Internet router
B. IPv4 tunnel
C. VPN tunnel
D. Network Address Translation

A: - D.

119. Which is the Class A private IP address range? 
A. 10.0.0.0/8
B. 10.0.0.0/12 
C. 172.16.0.0/12 
D. 10.0.0.0/10

A: - A.

120. Which is the Class B private IP address range? 
A. 10.0.0.0/8
B. 10.0.0.0/12 
C. 172.16.0.0/12 
D. 10.0.0.0/10

A: - C.

121. Which is the Class C private IP address range? 
A. 192.168.1.0/24
B. 192.168.0.0/24 
C. 192.168.0.0/16 
D. 192.168.0.0/12

A: - C, range 192.168.0.0 - 192.168.255.255 in cidr 192.168.0.0/16

122. You plug a laptop into a network jack. When you examine the IP address, you see 169.254.23.43. What can you conclude?
A. The network jack is not working.
B. Your laptop has a static IP address configured. 
C. The network is configured properly.
D. The DHCP server is down.

A:- D, link local address 

123. You want to put a web server online for public use. Which IP address would you use?
A. 192.168.34.34
B. 172.31.54.3 
C. 10.55.33.32 
D. 198.168.55.45

A:- D

124. Who is the governing body that distributes public IP addresses? 
A. IANA
B. RFC 
C. IAB 
D. IETF

A:- A.

125. Which protocol allows multicast switches to join computers to the multicast group?
A. ICMP B. IGMP C. IPMI D. IPGRP

A:- B, IGMP, Internet Group Messaging Protocol, allows switches to join computers to the multicast group table. This allows the selective process of snooping to occur when a transmission is sent.

126. Why is IPv6 needed in the world today?
A. It does not require NAT to operate.
B. The IPv4 address space is exhausted.
C. IPv4 is considered legacy, and IPv6 is the replacement. 
D. IPv6 does not support subnetting.

A:- B.

127. How many bits is an IPv6 address? 
A. 32 bits
B. 64 bits 
C. 128 bits 
D. 256 bits

A:- C, 64 bits is the host ID and 64 bits is the network ID


128. You have two facilities and both use IPv6 addressing internally. However, both facilities are connected to the Internet via IPv4. What is
one recommended method you can use to communicate between the facilities over the Internet?
A. Dedicated leased line 
B. Frame Relay
C. Dual stack
D. 6to4 tunnel

A: - D, A 6to4 tunnel can be achieved between the routers. This encapsulates the IPv6 header in an IPv4 header so that it can be routed across the Internet. Lease line and Frame relay are WAN methods.

129. Which command is required on a router to support IPv6 static addressing?
A. Router(config)#ipv6 address
B. Router(config)#ipv6 routing
C. Router(config)#ipv6 enable
D. Router(config)#ipv6 unicast-routing

A:- D, In order to enable IPv6 on a router it must be globally configured

130, image

131. Which field of the IPv6 header allows for a dual stack host to decide which stack to process the packet in?
A. Version field
B. Flow label
C. Source address
D. Destination address

A:- A, first 4 bits

132. You want to see all of the interfaces on a router configured with IPv6. Which command would you use?
A. Router#show ipv6 interfaces brief 
B. Router#show ip interfaces brief 
C. Router#show interfaces status
D. Router#show ip addresses

A:- A.

133. Which is a valid shortened IPv6 address for 2001:0db8:0000:0000:0000:8a2e:0000:1337?
A. 2001:db8:0000::8a2e::1337 
B. 2001:db8:::8a2e:0000:1337 
C. 2001:db8::8a2e::1337
D. 2001:db8::8a2e:0:1337

A:- D.

134. Which is the correct expansion for the IPv6 address 2001::456:0:ada4? 
A. 2001:0000:0000:0456:0000:ada4
B. 2001:0000:0000:0000:456:0000:ada4
C. 2001:0000:0000:0000:0000:0456:0000:ada4
D. 2001:0000:0000:0000:0456:0000:0000:ada4

A:- C.

135. In the IPv6 address 2001.0db8:1234:0016:0023:8080:2345:88ab/64, what is the subnet quartet?
A. 1234 
B. 0016 
C. 0023 
D. 8080

A:- B, First 48 bits of an IPv6 address are the global prefix; the next 16 bits are the subnet portion. 

136. What is the network prefix for the IPv6 address 2001.db8::8080:2345:88ab/64?

A. 2001:db8::/64
B. 2001:0db8:8080:2345/64
C. 2001:0db8:0000:8080/64
D. 2001:0db8:0000:2345/64

A:- A.

137. You need to verify connectivity to the IPv6 address fc00:0000:0000:0000:0000:0000:0000:0004. Which command would you use?

A. Router#ping fc00::4
B. Router#ping fc::4
C. Router#ping ipv6 fc00::4 
D. Router#ping ipv6 fc::4

A:- C.

138. Which method is used to direct communications to a single host? 
A. Unicast
B. Broadcast 
C. Multicast 
D. Anycast

A:- A.

139. Which protocol uses broadcasting at layer 3? 
A. ARP
B. DHCP 
C. IGMP 
D. SNMP

A:- B, DHCP uses a packet called a Discover packet. This packet is addressed to 255.255.255.255. Although ARP uses a broadcast it is a layer 2, IGMP is a layer 3 protocol that uses unicast to register members of a multicast group. SNMP is a layer 3 management protocol that uses unicast for messaging

140. Which method is used to direct communications to all computers in a subnet?
A. Unicast 
B. Broadcast 
C. Multicast 
D. Anycast

A:- B.

141. You work for an ISP. The American Registry for Internet Numbers (ARIN) has given you the 2001:0db8:8/34 IP address block. How many /48 blocks can you assign to your customers?
A. 32,768 
B. 16,384 
C. 8,192 
D. 4,096

A:- B, subtract 34 bits from 48 = 14 bits 2**14 = 16384

142. What protocol/process in IPv6 replaces the IPv4 ARP process? 
A. NDP (NS/NA)
B. DAD (NS/NA) 
C. SLAAC (RS/RA) 
D. ARPv6 (NS/NA)

A:- A, Neighbor discovery protocol (NDP) uses Neighbor Solicitation (NS) and Neighbor Advertisement (NA) messages to look up an IP address from a MAC address through the use of multicast messages. 

143. Which address is a global unicast address? 

A. fe80:db80:db01:ada0:1112::1
B. 2005:acd:234:1132::43
C. fd00:ac34:34b:8064:234a::7
D. ff00:101:4ab0:3b3e::10

A:- B, global unicast range is defined as 2000::/3. This provides a range of 2000:: to 3fff::
An Address with Fe80 is a link local address 
An Address with fc00 is a unique local unicast address 
An Address with ff00::/7 is a multicast address 

144. For global unicast addresses, which part of the address is allotted by the regional Internet registry (RIR) for the corresponding region?
A. First 23 bits B. First 32 bits C. First 48 bits D. First 64 bits

A:- A, the first 23 bits are alloted to the ISP by the RIR for the region of the world for which the ISP is requesting the prefix

145. Which address is a unique local address? 
 
A. fe80:db80:db01:ada0:1112::1
B. 2005:acd:234:1132::43
C. fd00:ac34:34b:8064:234a::7
D. ff00::10

A:- C, the unique local address is defined as fc00::/7



146. Which IPv6 address type is similar to IPv4 RFC 1918 addresses?
A. Link-local addresses
B. Global unicast addresses 
C. EUI-64 addresses
D. Anycast addresses

A:- A, Link-local addresses are the equivalent to RFC1918 addresses and are non non-routable. Global unicast addresses are similar to IPv4 public IP4 addresses. 
An EUI-64 address is the host interface portion of the IPv6 address when its configured using the host MAC address. 

147. Which address is a link-local address? 

A. fe80:db80:db01:ada0:1112::1
B. 2005:acd:234:1132::43
C. fd00:ac34:34b:8064:234a::7
D. ff00:101:4ab0:3b3e::10

A:- A,

148. Which method is used to direct communications to the IP address that is closest to the source?
A. Unicast B. Broadcast C. Multicast D. Anycast

A:- D

149. Which command would configure a single anycast address on a router’s interface? text 

150. Which method is used to direct communications to a group of computers that subscribe to the transmission?
A. Unicast 
B. Broadcast
C. Multicast
D. Anycast

A:- C

151. Which address is a multicast address?
A. fe80:db80:db01:ada0:1112::1 
B. 2005:acd:234:1132::43
C. fd00:ac34:34b:8064:234a::7 
D. ff00::10

A:- D, The multicast address is defined as ff00::/8. Multicast addresses always start with ff. 

152. You are using the EUI-64 method of allocating the host portion of the IPv6 addresses. The MAC address of the host is f423:56 34:5623. 

Which is the correct IP address that will be calculated for a network ID of fd00:1:1::?
A. fd00:0001:0001:0000:f623:56ff:fe34:5623/64 
B. fd00:0001:0001:0000:f423:56ff:fe34:5623/64 
C. fd00:0001:0001:0000:fffe:f623:5634:5623/64 
D. fd00:0001:0001:0000:f623:56ff:ff34:5623/64

A:- A.

153. Which address is a EUI-64 generated address? 
A. 2001:db8:33::f629:58fe:ff35:5893/64
B. fd00:4:33::f680:45ca:ac3b:5a73/64
C. 2001:db8:aa::f654:56ff:fe34:a633/64
D. 2001:db8:17:fffe:f623::ff34:5623/64

A:- C

154. Which command would use the MAC address for the host portion of the IPv6 address on a router interface?
A. Router(config-if)#ip address eui-64 2001:db8:1234::/64
B. Router(config-if)#ip address 2001:db8:1234::/64 mac-
address
C. Router(config-if)#ipv6 address 2001:db8:1234::/64 eui-64
D. Router(config-if)#ipv6 address 2001:db8:1234::/64 mac

A:- C.

155. Which command on Windows will allow you to verify your IP address, subnet mask, default gateway, and MAC address?
```
A. C:\>ipconfig
B. C:\>ipstatus
C. C:\>ipconfig /all 
D. C:\>hostname 
```
A:- C.

156. Which command on Windows will allow you to verify the path a packet gets routed through on the network?
```
A. C:\>tracert 198.78.34.2
B. C:\>ping 198.78.34.2
C. C:\>traceroute 198.78.34.2 
D. C:\>route print
```

A:- A on windows, c on linux 

157. Your DNS administrator has changed the DNS entry for RouterB. You clear the DNS cache on RouterA and ping routerb.sybex.com from RouterA, but you still ping the original address prior to the change. All other DNS addresses work fine and the entry resolves correctly on your laptop. What is the problem?

A. The router is configured to the wrong DNS server. 
B. RouterA has a host entry configured.
C. The DNS administrator made an error.
D. The domain name of the router is incorrect.

A:- B.

158. You have configured a router to point to the DNS server with the IP address 10.2.2.2 and configured the domain name of sybex.com. However, you cannot resolve the host routerb.sybex.com. Which Windows command will help you verify DNS name resolution?
```
A. C:\>ping routerb.sybex.com
B. C:\>tracert routerb.sybex.com 
C. C:\>nslookup routerb.sybex.com 
D. C:\>dig routerb.sybex.com
```

A:- C.

159. Which Windows command will allow you to see the DHCP server that has configured the client computer with an IP address?
```
A. C:\>ipconfig
B. C:\>ipconfig /all
C. C:\>ipconfig /showclassid 
D. C:\>ipstatus
```

A:- B.

160. You have configured a DHCP server on a router interface. You test a Windows client and receive the address 169.254.24.56. What can you conclude?

A. You have successfully configured the scope of 169.254.24.0/24.
B. The client had a static IP address of 169.254.24.0/24 configured.
C. The DHCP server is not configured properly and the client has configured itself with a link-local address.
D. The DHCP server is configured for APIPA.

A:- C.

161. Which is the contention method 802.11 wireless uses?
A. CSMA/CA 
B. CSMA/CD 
C. DSSS
D. OFDM

A:- A, 802.11 uses a contention method of Carrier Sense Multiple Access/Collision Avoidance. Ethernet uses CSMA-CD


162. In the 2.4 GHz spectrum for 802.11, which channels are non- overlapping?
A. Channels 1, 3, and 11 
B. Channels 1, 3, and 6 
C. Channels 1, 6, and 11 
D. Channels 1 through 6

A:- C.

163. You are designing a wireless network for an office building. The building has a large number of tenants that utilize wireless already.
Which protocol will least likely overlap with wireless channels the tenants are currently using?
A. 802.11b B. 802.11g C. 802.11n D. 802.11ac

A:- D, 802.11ac is least likely to overlap the wireless channels. 802.11ac uses 5 GHz wireless frequency spectrum.

164. Which wireless encryption protocol uses a 24-bit initialization vector? A. WPA
B. WEP 
C. WPA2 
D. WPA3

A:- B, WEP uses a 24bit initialization vector to randomize each session.

165. Which wireless standard does not use a pre-shared key for authentication?
A. WPA
B. WPA2
C. WEP
D. WPA2 Enterprise

A:- WPA2 Enterprise does not use a PSK for authentication, WPA2 Enterprise uses certificates to authenticate users.


166. When designing a wireless network, which would be a compelling reason to use 5 GHz?
A. 5 GHz can go further.
B. 5 GHz allows for more clients.
C. There are 24 non-overlapping channels. 
D. There is less interference on 5 GHz.

A:- C, (same amount of interference)

167. Which wireless frequency spectrum is shared with Bluetooth? 
A. 900 MHz
B. 2.4 GHz 
C. 5 GHz
D. All of the above

A:- B.

168. Which 802.11 standard functions strictly on 2.4 GHz?
A. 802.11g B. 802.11n C. 802.11a D. 802.11ac

A:- A. 

169. Which allows for the distribution of computer resources such as CPU and RAM to be distributed over several operating systems?
A. Physical server 
B. Hypervisor
C. Virtual machine 
D. Virtual network

A:- B

170. Which option describes a VM best?
A. An operating system that is running directly on hardware
B. An operating system that is running with dedicated hardware
C. An operating system that is running on reduced hardware features 
D. An operating system that is decoupled from the hardware

A:- D.

171. What is the physical hardware used in virtualization called? 
A. Host
B. VM
C. Hypervisor 
D. Guest

A:- A

172. Which component connects the VM NIC to the physical network? 
A. vNIC
B. Trunk
C. Virtual switch
D. NX-OS

A:- C

173. Which of the following is a virtual network function (VNF) device?
A. Virtual switch B. Virtual firewall C. Database server D. File server

A:- B


174. You need to scale out some web servers to accommodate load. Which method would you use?
A. Add vCPUs. B. Add vRAM. C. Add DNS. D. Add SLBaaS.

A:- D, add server load balancing as a server (SLBaaS)

175. Which is a correct statement about MAC addresses?
A. Organizationally unique identifiers (OUIs) create a unique MAC address.
B. The first 24 bits of a MAC address are specified by the vendor.
C. The IEEE is responsible for MAC address uniqueness.
D. If the I/G bit is set to 1, then the frame identifies a broadcast or multicast.

A:- D, When the individual/group (I/G) high order bit is set to 1, the frame is a broadcast or a multicast transmission. 

176. Which command would you use to diagnose a problem with frames that are not getting forwarded to the destination node on a switch?
A. Switch#show route
B. Switch#show mac address-table 
C. Switch#show mac table
D. Switch#show interface

A:- B, when diagnosing frame forwarding on a switch, the MAC address table needs to be inspected to see if the switch has learned the destination MAC address. You can use the command show mac address-table to inspect the MAC address table. The command [show route] is incorrect, it only displays layer 3 route decision information.

177. Which mechanism does a switch employ to stop switching loops? 
A. Port channels
B. Spanning Tree Protocol (STP) 
C. Ether channels
D. Trunks

A:- B, 

178. Which is a consequence of not using loop avoidance with layer 2 switching?
A. Duplicate unicast frames 
B. Broadcast storms
C. MAC address thrashing 
D. All of the above

A:- D

179. Which switching method checks the CRC as the frame is received by the switch?
A. Cut-through mode
B. Frag-free mode
C. Store-and-forward mode 
D. Fast switching

A:- C, Store and forward is the default mode for mode edge switching equipment. Store-and-forward receives the frame, calculates the CRC and then makes a forwarding decision. Cut-through mode allows the switch to make a forward/filter decision immediately after the destination MAC address is received. Frag-free mode inspects the first 64 bytes of an incoming frame, before a forward filter decision is made. Fast switching is a method in which a caching table is created for MAC addresses received so that switching can be made faster.

180. Which switch mode operation reads only the first 64 bytes before making a switching decision?
A. Cut-through mode
B. Fragment-free mode
C. Store-and-forward mode 
D. Fast switching

A:- B fragment mode reads the first 64 bytes and deems the frame intact and forwardable. This is because most collisions that would create frame fragments happen within the first 64 bytes of a frame. 

181. D (image)

182. How are MAC addresses learned and associated with the port?
A. Destination MAC address learning
B. Source MAC address learning
C. Port listen/learning
D. Frame type learning

A:- B, Switches learn MAC addresses by inspecting the frames source MAC address in the incoming port. They then associate the source MAC address with the port it came in on. 

183.
184.

185. What is the default MAC address aging time for dynamic entries on most switches?
A. 30 seconds B. 60 seconds C. 300 seconds D. 500 seconds

A:- 300 seconds, or 5 minutes


187. What information is added to the MAC address table when a frame is received on an interface?
A. Destination MAC address of the frame and incoming port number 
B. Source MAC address of the frame and incoming port number
C. Destination MAC address of the frame and outgoing port number 
D. Source MAC address of the frame and outgoing port number

A:- B, When a frame is received on an incoming port, both the incoming port and the source mac address are added to the MAC address table and set with an aging timer. The destination MAC address in the incoming frame is used for forward/filter decisions only. The destination is never used to populate the table.

188. You need to change the default MAC address aging time on a switch to 400 seconds. Which command would you use?
A. Switch#set mac aging 400
B. Switch#mac aging-time 400 seconds
C. Switch#mac-address-table aging-time 400 
D. Switch#mac address-aging 400

A:- C.

189. How do switches forward frames only to the destination computer? 
A. Forward/filter decisions based on the MAC address table
B. Forward/filter decisions based on the routing table
C. Flooding ports for the destination MAC address
D. Broadcasting for the MAC address

A:- A, switches make forward/filter decisions based upon the MAC address to port association in the MAC address table. 

190.
191.
192.

193. Under which circumstance will a switch drop a frame?
A. If the destination MAC address of the frame is unknown in the MAC address table
B. If the source MAC address of the frame is unknown in the MAC address table
C. If the frame is deemed to be corrupt via the CRC
D. If the destination MAC address exists in another switch’s MAC address table

A:- C, the only time a frame is dropped is when the cyclic redundancy check calculated against the frames payload deems the frame corrupt. 

194. Which switch function reads the frame and uses the MAC address table to decide the egress interface for the frame?
A. Forward/filter
B. Address learning 
C. Loop avoidance 
D. Frame flooding

A:- A, The forward filter function of a switch is used to look up the destination MAC address in a MAC address table and decide the egress interface for the frame. If the MAC address is not in the table, the frame is forwarded out all the interfaces. 

195.
196.

197. Which statement is true of an ARP request entering into a switch?

A. The source MAC address of the frame will be all fs.
B. The destination MAC address of the frame will be all fs.
C. The switch will only forward the ARP request to the port for the destination computer.
D. The switch will respond directly back with an ARP reply.

A:- B.

198. Under what circumstance will a switch flood a frame to all ports on the switch?
A. When the source MAC address is unknown by the switch
B. When the destination MAC address is a multicast address
C. When the destination MAC address is unknown by the switch 
D. When the destination MAC address is 0000.0000.0000

A:- C

199. Where are MAC address tables stored? 
A. Flash
B. CPU registers 
C. RAM
D. NVRAM

A:- C, CAM tables are always built and stored temporarily in RAM. When the switch is turned off or the [clear] command is issued

200. Which command will allow you to see the MAC address table?
A. Switch#show mac
B. Switch#show mac address-table 
C. Switch#show cam table
D. Switch#show mac table

A:- B.

201. Which command will display all connected ports on a switch and include descriptions?
A. Switch#show ports
B. Switch#show counters interfaces 
C. Switch#show interfaces counters 
D. Switch#show interfaces status

A:- D.
