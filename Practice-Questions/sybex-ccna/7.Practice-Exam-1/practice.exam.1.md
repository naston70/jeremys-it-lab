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

A. C.

52. Which command will need to be configured for support of discontinuous networks?
- A. Router(config-router)#network discontiguous 
- B. Router(config)#network discontiguous
- C. Router(config)#no auto-summary
- D. Router(config-router)#no auto-summary

A. D.

53. Which command configures RIPv2 on a router and advertises a network of 192.168.20.0/24?

- A. Router(config)#ip router ripv2
     Router(config-router)#network 192.168.20.0

- B. Router(config)#router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0

- C. Router(config)#router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0 0.0.0.255

- D. Router(config)#ip router rip
     Router(config-router)#version 2
     Router(config-router)#network 192.168.20.0 0.0.0.255

A. B.

54. Which routing technique is best suited for small networks in which the administrator wants control of routing?
- A. OSPF routing 
- B. EIGRP routing 
- C. Static routing 
- D. RIP routing

A. C.

55. Which command will allow you to verify the IPv6 addresses configured on a router?
- A. Router#show ipv6
- B. Router#show ip interfaces brief 
- C. Router#show ipv6 interfaces brief 
- D. Router#show ipv6 brief

A. C.

56. Which command will show you the IPv6 routes in the routing table? 
- A. Router#show ipv6 route
- B. Router#show ip route
- C. Router#show ipv6 route summary
- D. Router#show ipv6 route brief

A. B

57. IMG
A. C.

58. Which command will only show you all of the directly connected routes for IPv6?
- A. Router#show ipv6 interface summary 
- B. Router#show ipv6 route connected
- C. Router#show ipv6 interface brief
- D. Router#show ipv6 summary

A. B.

59. IMG
A. C.

60. IMG
A. D. 

61. Which command will allow you to check basic connectivity at layer 3? 
- A. Router#show ip route
- B. Router#ping 192.168.4.1
- C. Router#pathping 192.168.4.1
- D. Router#ip ping 192.168.4.1

A. B.

62. Which command will allow you to see the path on which a packet gets routed to its destination?
- A. Router#show ip route
- B. Router#tracert 192.168.7.56
- C. Router#pathping 192.168.7.56 
- D. Router#traceroute 192.168.7.56

A. D

63. IMG
A. C, both routers have passive interfaces for OSPF. To fix this the command [no passive-interface serial 0/0] would need to be entered. Process ID's are only locally significant

64. Which command will allow you to see the networks the current router is advertising for OSPF?
- A. Router#show ip protocols
- B. Router#show ip ospf
- C. Router#show ip ospf database 
- D. Router#show ip ospf neighbors

A. A. 

65. A client has an IP address of 192.168.1.5/24 and a default gateway of 192.168.1.1. HSRP is in use in the network. Which type of router is the default gateway?
- A. Active router
- B. Standby router 
- C. Virtual router 
- D. Support router

A. C. 

66. Which of the following is an advantage to using Port Address Translation?
- A. Lower levels of jitter
- B. Lower levels of packet loss
- C. Flexibility of Internet connections
- D. Lower memory usage than other NAT types

A. C.

67. Which command would you configure on the private network interface for NAT?
- A. Router(config-if)#ip nat outside 
- B. Router(config)#ip nat inside gi0/0 
- C. Router(config-if)#ip nat private 
- D. Router(config-if)#ip nat inside

A. D.

68. Why is time synchronization important for routers and switches? 
- A. It is important for serialized communication frame alignment. 
- B. It is important for quality of service queuing.
- C. It is important for logging accuracy.
- D. It helps delivery of packets via timed queues.

A. C.

69. Which statement describes FQDNs?
- A. A DNS server always processes the entire FQDN.
- B. FQDNs are always registered with a registrar.
- C. FQDNs are significant from left to right, starting with a period for the root.
- D. FQDNs are significant from right to left, starting with a period for the root.

A. FQDN's are significant from right to left, starting with a period to signify the root. 

70. Which protocol and port number does SNMP use for polling from the NMS?
- A. UDP/161 
- B. TCP/162 
- C. UDP/162 
- D. UDP/514

A. A, SNMP uses UDP port 161 for communication from an SNMP NMS to a network device for information requests. UDP 162 for traps and polling.

71. Which command will allow you to verify the syslog server set for logging and the logging level set?
- A. Router#show logging
- B. Router#show syslog
- C. Router#show log-server 
- D. Router#show ip logging

A. A. 

72. Which command will allow you to verify the IP addresses assigned to a router’s interface?
- A. Router#show ip dhcp bindings 
- B. Router#show ip interface
- C. Router#show ip lease
- D. Router#show ip dhcp lease

A. B.

73. Where should QoS marking be performed? 
- A. Closest to the source of the traffic
- B. Closest to the Internet router
- C. On every device in the network
- D. On the core router in the network

A. A.

74. Which is a correct statement about device trust boundary for QoS?
- A. The trust boundary should always be an asset IT controls. 
- B. The switch should always be set as the trust boundary.
- C. Only routers can create trust boundaries.
- D. Only IP phones can become trust boundaries.

A. A.

75. Which command needs to be configured to enable the SSH Copy Protocol (SCP)?
- A. Switch(config)#ip ssh server enable  
- B. Switch(config)#ip scp server enable 
- C. Switch(config)#service scp enable 
- D. Switch(config)#service scp-server

A. B. 

76. What is the attack in which DTP is exploited by a malicious user? 
- A. Native VLAN
- B. VLAN hopping 
- C. VLAN traversal 
- D. Trunk popping

A. B, VLAN hopping is an attack in which DTP is exploited. The attacker negotiates a trunk with the switch via DTP and can hop from VLAN to VLAN.

77. Which layer 2 protocol has built-in security for WAN connections?
- A. HDLC
- B. PPP
- C. IPsec
- D. Metro Ethernet

A. B, PPP is a layer-2 wan protocol. PPP supports CHAP, which secures connections.

78. Chelsea is worried about the threat of malware on the network. She wants to install software that will detect worms and Trojan horses on every workstation. Which type of software should she install?
- A. Malware
- B. Antivirus
- C. Software firewalls 
- D. Spyware

A. B.

79. Which command will configure the login banner to read “CCNA Routing and Switching”?
- A. Router(config)#login banner CCNA Routing and Switching
- B. Router(config)#banner login CCNA Routing and Switching
- C. Router(config)#banner login ^CCNA Routing and
Switching^
- D. Router(config-line)#banner login ^CCNA Routing and Switching^

A. C

80. You have configured a message of the day (MOTD) banner, but it only shows up after you have logged into the router. What is the problem?
- A. You are connecting via SSH.
- B. You are connecting via Telnet.
- C. You are connecting via the console.
- D. You do not have an enable password set.

A. A, when connecting via SSH, the MOTD banner is not displayed until after the user has authenticated to the router or switch. 

81. Which mechanism is used to authenticate EAP-TLS during the 802.1x authentication process?
- A. MD5
- B. Certificates 
- C. SSH
- D. Passwords

A. B.

82. You have been asked to recommend a private WAN technology. All of the remote offices have varied physical connectivity paths. Which private WAN technology should you recommend?
- A. MPLS
- B. Metro Ethernet 
- C. PPPoE
- D. GRE tunnels

A. A, MPLS allows for varied access links such as serial leased lines, frame relay, metro ethernet and so on.

83. Which protocol does IPsec use to check integrity of data packets? 
- A. AH
- B. ESP
- C. IKE
- D. ISAKMP

A. A, IPsec uses the authentication header (AH) protocol to check data integrity. This is done by creating a numerical hash of the data via SHA1 SHA2 or MD5.

84. If a router has two interfaces and you only use IPv4, how many ACLs can be configured on the router’s interfaces?
- A. One 
- B. Two 
- C. Four 
- D. Eight

A. C.

85. Which command will achieve the same goal as the command:
```access- list 2 permit host 192.168.2.3``` ?

- A. Router(config)#access-list 2 permit 192.168.2.3 255.255.255.255
- B. Router(config)#access-list 2 permit 192.168.2.3 0.0.0.0
- C. Router(config)#ip access-list 2 permit host 192.168.2.3
- D. Router(config)#access-list 2 permit 192.168.2.3

A. B, access-list uses a bit mask

86. You have just configured DHCP snooping. Which ports should be trusted?
- A. Ports connecting to clients
- B. Ports connecting to web servers
- C. Ports connecting to other switches 
- D. Ports connecting to the DNS server

A. C, Ports connecting to trusted infrastructure devices such as routers and switches should be trusted. This is because legitimate DHCP traffic could originate from these ports. 

87. Which is a correct statement about how DHCP snooping works?
- A. Untrusted ports allow Discover and Offer messages to be switched.
- B. Untrusted ports drop Discover and Offer messages.
- C. Untrusted ports drop Offer and Acknowledgment messages.
- D. Untrusted ports allow Offer and Acknowledgment messages to be switched.

A. C, the Untrusted ports drop Offer and Acknowledgment DHCP messages. The only device that should offer and acknowledge IP addresses is the DHCP server on a trusted port. 

88. Which command will configure the RADIUS server 192.168.1.5 with a secret of aaaauth?
- A. Router(config)#radius host 192.168.1.5 key aaaauth
- B. Router(config)#radius-server host 192.168.1.5 key aaaauth
- C. Router(config)#radius-server 192.168.1.5 key aaaauth
- D. Router(config)#radius-server host 192.168.1.5 secret aaaauth

A. B.

89. Which protocol was released to fix WEP? 
- A. WPA
- B. WPA2
- C. WPA3
- D. RC4-TKIP

A. A

90. You are configuring a WLAN and you need to use WPA PSK, but you also need to restrict certain devices. What should you implement to achieve this goal?
- A. Captive portal
- B. RADIUS
- C. MAC filtering
- D. Disable broadcast SSID

A. C.

91. An employee has left, and you are required to change the password of 50 routers. What is the quickest way to complete this task?
- A. Creating a script with Python
- B. Creating a script with JSON
- C. Applying a YAML template to the routers 
- D. Applying a JSON template to the routers

A. A.

92. Which is a negative outcome from automating a configuration change across the enterprise?
- A. Increased odds of typographical errors
- B. Increased odds of configuration conflicts
- C. Increased time spent building configurations 
- D. Decreased time spent building configurations

A. B. 

93. You have been given the task of mapping a network. You have several routers and switches that are interconnected. Which Cisco tool will help you map the network?
- A. CDP
- B. Running configuration 
- C. OSPF neighbor table 
- D. EIGRP neighbor table

A. A.

94. Which protocol is used with the Southbound interface in the SDN controller?
- A. Python
- B. OpenFlow
- C. REST
- D. JSON

A. B, OpenFlow is an open standard used to configure network devices via the SBI of the SDN.

95. On which layer does the fabric of software defined network switch packets?
- A. Layer 2 
- B. Layer 3 
- C. Layer 6 
- D. Layer 7

A. B

96. Where inside of the Cisco DNA Center can you configure the upgrade of IOS for network devices?
- A. Provision 
- B. Design 
- C. Policy
- D. Assurance

A. A.

97. You are testing a POST function on a REST-based API and a 401 status code was returned. What does that mean?
- A. The POST was accepted. 
- B. The POST was redirected to another URI. 
- C. The POST was unauthorized.
- D. The POST was not in the right format.

A. C. status code of 401 is the method unauthorized. 

98. Which configuration management mechanism uses Python and YAML as a configuration language?
- A. DSC
- B. Chef 
- C. Puppet 
- D. Ansible

A. D. 

99. Which is a requirement for using Ansible for configuration management?
- A. Internet access
- B. Root SSH
- C. Unrestricted firewall 
- D. Ruby

A. B. 

100. Which command is used to output JSON from the execution of a command on a Cisco router or switch?
- A. show interface status | json-pretty native 
- B. json interface status
- C. show interface status | json
- D. show interface status json

A. A. 
