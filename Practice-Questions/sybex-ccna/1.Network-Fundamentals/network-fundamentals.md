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

A. There are three potential collision domains. - A collision domain is a network segment in which collision can occure and the colliding frame is created.

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