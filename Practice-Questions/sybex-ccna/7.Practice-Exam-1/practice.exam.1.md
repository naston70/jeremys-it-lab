## Practice Exam 1

1. Which device acts like a multiport repeater? 
- A. Firewall
- B. Hub 
- C. Router 
- D. Switch

A. B. 

2. Which benefit does a switch provide to a LAN? 
- A. Breaks up broadcast domains
- B. Breaks up collision domains
- C. Forces full-duplex on all ports
- D. Allows for a fast uplink port

A. B, switches break up collision domains by allowing micro-segmentation.  

3. When a firewall matches a URI, it is operating at which layer?
- A. Layer 7 
- B. Layer 5 
- C. Layer 4
- D. Layer 3

A. A. 

4. Which topology does an autonomous WAP use?
- A. Star topology
- B. Full mesh topology 
- C. Partial mesh topology 
- D. Hybrid topology

A. A. 

5. Which is the default encapsulation on a serial connection for Cisco? 
- A. MPLS
- B. HDLC 
- C. PPP 
- D. PPPoE

A. B.

6. You are connecting a Cisco router to a leased line serial connection. The other side of the connection has non-Cisco equipment. Which protocol should you choose for compatibility?
- A. HDLC 
- B. PPP
- C. PPPoE 
- D. X.25

A. B, PPP is an open standard. Cisco routers default to HDLC however it is proprietary so PPP should be used for compatibility.  

7. What is the term used to describe the telephone company’s switching office?
- A. Demarcation point 
- B. Network edge
- C. Central office
- D. Main data frame

A. C, the central office, sometimes referred to as the CO, is the local switching office. The CO is where data lines meet the public network for voice and data. 

8. What is the term that defines the access point for the service provider’s services?
- A. Demarcation point
- B. Point of presence 
- C. Customer edge 
- D. Network edge

A. B.

9. You have several VMs in a public cloud. What is a benefit of creating NTP VNF in the public cloud for the VMs?
- A. Better time synchronization
- B. Better response time from the VMs
- C. Lower bandwidth utilization from your premises 
- D. Overcoming different time zones

A. C, lowering bandwidth between the premises and your virtual machines on the public cloud is a direct benefit of locating a NTP virtual network function on the public cloud for VM time synchronization. 

10. When deciding to move DNS into the cloud for an application on the public cloud, what is the primary decision factor?
- A. Bandwidth
- B. Response time
- C. Proper DNS resolution
- D. The cloud provider’s requirements

A. A.

11. Which protocol is connectionless and contains no flow control? 
- A. IP
- B. TCP 
- C. UDP 
- D. ICMP

A. C.

12. You plug a laptop into a network jack. When you examine the IP address, you see 10.23.2.3, which was not originally configured when you checked prior to plugging it in. What can you conclude?
- A. The network jack is not working.
- B. Your laptop has a static IP address configured. 
- C. The network is configured properly.
- D. The DHCP server is down.

A. C. 

13. Which network does the IP address 192.168.4.38/27 belong to? 
- A. 192.168.4.8/27 network
- B. 192.168.4.16/27 network
- C. 192.168.4.32/27 network
- D. 192.168.4.64/27 network

A. C.

14. What are stateless DHCPv6 servers used for?
- A. Configuring the default gateway
- B. Configuring the IPv6 address
- C. Configuring the IPv6 prefix length 
- D. Configuring the DNS server address

A. D.

15. Which mechanism in IPv6 allows for SLAAC to avoid duplicating an IPv6 address?
- A. NDP (NS/NA) 
- B. DAD (NS/NA) 
- C. SLAAC (RS/RA) 
- D. ARPv6 (NS/NA)

A. B, duplicate address detection, or DAD uses NS and NA messages to avoid duplicate addresses when SLAAC is being used. 

16. Which term best describes the IPv6 address of 2202:0ff8:0002:2344:3533:8eff:fe22:ae4c?
- A. Multicast address 
- B. EUI-64 address 
- C. Anycast address 
- D. Link-local address

A. B, note the ffee in middle of address.

17. If a switch uses the store and forward method of switching and receives a frame in which its CRC is invalid, what will happen?
- A. The switch will re-create the frame with a new CRC and correct the missing information.
- B. The switch will drop the frame and wait for retransmission of a new frame.
- C. The switch will send back a frame for retransmission of the frame.
- D. The switch will store the frame until a new frame with a matching CRC is received.

A. B.

18. IMG 
A. A.

19. IMG
A. B.

20. When a switch receives a frame, what does it use to make a forwarding decision?
- A. Destination MAC address in the frame 
- B. Source MAC address in the frame
- C. Source IP address in the frame
- D. Destination IP address in the frame

A. A.

21. IMG 
A. C.

22. Which type of switch port strips all VLAN information from the frame before it egresses the interface on the switch?
- A. Trunk port 
- B. Access port 
- C. Voice port 
- D. DTP port

A. B. 

23. IMG 
A. B.

24. IMG 
A. C.

25. IMG 
A. A.

26. IMG 
A. D.

27. IMG 
A. B.

28. IMG 
A. A.

29. IMG 
A. C.

30. IMG 
A. B.

31. IMG 
A. D. 

32. IMG 
A. C.

33. When you’re using 802.1w, which switch port state will always forward traffic?
- A. Disabled 
- B. Backup
- C. Designated 
- D. Alternate

A. C.

34. You want to quickly configure an edge switch so all access ports are in PortFast mode. Which command will achieve this?
```
A. SwitchA(config)#spanning-tree portfast default
B. SwitchA(config)#switchport spanning-tree portfast 
C. SwitchA(config)#spanning-tree portfast enable
D. SwitchA(config)#spanning-tree portfast
```

A. A.

35. Which AP mode allows for RF analysis of the 802.11ac radio spectrum?
- A. Monitor mode
- B. Analysis mode
- C. FlexConnect mode 
- D. Local mode

A. A. 

36. You have a small area in a warehouse in which you need wired connectivity to the network. However, wiring cannot be run easily, but there is a direct line of sight for wireless. Which AP feature can be used to connect the area?
- A. Wireless mesh
- B. LightWeight mode 
- C. Local mode
- D. WorkGroup Bridge

A. D, Workgroup Bridgemode allows you to connect an AP to another AP via an SSID. The Ethernet connection is then bridged over to allow other wired connections to share the wireless bridge.  

37. You need to configure a LAG for a Cisco wireless controller. What should be configured on the EtherChannel to establish a link?
- A. Auto mode
- B. On mode
- C. Desirable mode 
- D. Passive mode

A. B, when an EtherChannel is configured to an 'on mode' it means that no negotiation protocol will be used to build the EtherChannel.

38. Which is a benefit of using TACACS+ for authentication of users? 
- A. It is an open standard.
- B. It sends the passwords of users in clear text.
- C. It supports authenticating a user to a subset of commands. 
- D. It supports authenticating a user to a length of time.

A. C.

39. Why should you always provide a second method of local when setting up AAA remote authentication with a router or switch?
- A. To allow for a backdoor.
- B. To provide a backup if the TACACS+ server is down or unreachable.
- C. The local second method is required.
- D. All of the above.

A. B.

40. You want all guests to register for wireless Internet access before granting them access. What should you implement?
- A. Captive portal 
- B. AAA server 
- C. ESS
- D. RRM

A. A.

41. When an IP address is configured on the router’s interface, what happens in the routing table?
- A. A route entry is created for the network attached to the IP address on the interface.
- B. A route entry is created for the IP address attached to the interface.
- C. Dynamic routing protocols update all other routers.
- D. All of the above.

A. D.

42. IMG 
A. A.

43. IMG 
A. C.

44. What is the administrative distance of OSPF?
- A. 90 
- B. 100 
- C. 110 
- D. 120

A. C. 90 = EIGRP, 100 = IGRP, 110 = OSPF, 120 = RIP 

45. Which command will allow you to see the next advertisement interval for RIPv2?
- A. Router#show ip protocols
- B. Router#show ip rip database 
- C. Router#show ip rip
- D. Router#show ip interface

A. A.

46. Which command will allow you to inspect RIPv2 advertisements? 
- A. Router#show ip protocols
- B. Router#debug rip
- C. Router#show ip rip
- D. Router#debug ip rip

A. D.

47. You need to advertise the routes 192.168.1.0/24, 192.168.2.0/24, and 192.168.3.0/24. Assuming RIPv2 is configured, which configuration will achieve this?
- A. Router(config-router)#network 192.168.0.0
- B. Router(config-router)#network 192.168.1.0 
     Router(config-router)#network 192.168.2.0 
     Router(config-router)#network 192.168.3.0
- C. Router(config-router)#network 192.168.0.0/16
- D. Router(config-router)#network 192.168.0.0 0.0.255.255

A. B, RIPv2 needs to advertise the routes separately

48. You have RIPv2 configured on an Internet-facing router. Which
command will suppress RIPv2 advertisements on the interface link? 
- A. Router(config-if)#ip rip passive-interface
- B. Router(config-if)#rip passive-interface
- C. Router(config-router)#passive-interface serial 0/0 
- D. Router(config-if)#ip rip suppress-advertisement

A. C, the command from inside the config onto the interface will suppress advertisements

49. Which is a problem with using RIPv2 in a network? 
- A. Complex configuration
- B. Slow convergence
- C. The use of broadcasts
- D. Routing support for classless networks

A. B.

50. Which technique is used to stop routing loops with RIPv2?
- A. Split horizons
- B. Advertisement intervals 
- C. Zoning
- D. Invalid timers

A. Split horizons are used to stop routing loops with RIPv2. Split horizons prevent a router from advertising a route to a router in which the original route was discovered. 

51. Which algorithm does RIPv2 use to calculate routes? 
- A. Shortest Path First
- B. Dijkstra
- C. Bellman-Ford 
- D. DUAL

A.

52. Which command will need to be configured for support of discontinuous networks?
- A. Router(config-router)#network discontiguous 
- B. Router(config)#network discontiguous
- C. Router(config)#no auto-summary
- D. Router(config-router)#no auto-summary

A.

53. Which command configures RIPv2 on a router and advertises a network of 192.168.20.0/24?
- A. Router(config)#ip router ripv2
     Router(config-router)#network 192.168.20.0

- B. Router(config)#router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0

- C. Router(config)#router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0 0.0.0.255

D.   Router(config)#ip router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0 0.0.0.255

A. 

54. Which routing technique is best suited for small networks in which the administrator wants control of routing?
- A. OSPF routing 
- B. EIGRP routing 
- C. Static routing 
- D. RIP routing

A. 

55. Which command will allow you to verify the IPv6 addresses configured on a router?
- A. Router#show ipv6
- B. Router#show ip interfaces brief 
- C. Router#show ipv6 interfaces brief 
- D. Router#show ipv6 brief

A. 