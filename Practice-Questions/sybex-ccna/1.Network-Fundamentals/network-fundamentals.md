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