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
