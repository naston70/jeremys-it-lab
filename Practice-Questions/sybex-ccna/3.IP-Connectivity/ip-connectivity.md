## IP Connectivity


3.0 IP Connectivity
**✓ 3.1 Interpret the components of a routing table**
* 3.1.a Routing protocol code
* 3.1.b Prefix
* 3.1.c Network mask
* 3.1.d Next hop
* 3.1.e Administrative distance 3.1.f Metric
* 3.1.g Gateway of last resort
**✓ 3.2 Determine how a router makes a forwarding decision by default**
* 3.2.a Longest match
* 3.2.b Administrative distance 3.2.c Routing protocol metric
**✓ 3.3 Configure and verify IPv4 and IPv6 static routing**
* 3.3.a Default route
* 3.3.b Network route
* 3.3.c Host route
* 3.3.d Floating static
**✓ 3.4 Configure and verify single area OSPFv2**
* 3.4.a Neighbor adjacencies
* 3.4.b Point-to-point
* 3.4.c Broadcast (DR/BDR selection) 3.4.d Router ID
**✓ 3.5 Describe the purpose of first hop redundancy protocol**


1. Which is a reason for using a dynamic routing protocol?
- A. You have a network with only a few routers and subnets per branch.
- B. You have a network with only a few VLANs and one router.
- C. You have a network with a large number of VLANs and only one router.
- D. You have a network with a few subnets and many routers.

A. D, the scalability of routes between routers should always be considered when choosing a static routing design vs a dynamic routing design. A few subnets over many routers creates a lot of work when a new subnet is created and static routing is being used.

2. How are routers managed with interior gateway protocols?
- A. Routers are grouped into autonomous systems.
- B. Routing protocols are redistributed between ASs.
- C. All routers use the same interior routing protocol.
- D. All network IDs are advertised with the same autonomous system number.

A. Routers are grouped into the same autonomous system (AS). When they are within the same AS, they can exchange information such as routes to destination networks and converge their routing tables. Routing protocols are not normally redistributed between ASs because the network is usually managed as one AS  

3. What is the maximum hop count for RIP? 
- A. 15 hops
- B. 100 hops 
- C. 255 hops 
- D. 16 hops

A. RIP max hop count is 15, above 15 is considered unreachable/ unroutable. 

4. Which statement is true about RIPv2 advertisements?
- A. RIPv2 allows for neighborship through hello packets.
- B. RIPv2 broadcasts only updates on all active interfaces.
- C. RIPv2 multicasts the full routing table every 30 seconds.
- D. RIPv2 multicasts the full routing table every 60 seconds

A. C, 30 seconds multicast of full routing table 

5. Which multicast address does RIPv2 use for advertising routes?
- A. 224.0.0.5 
- B. 224.0.0.9 
- C. 224.0.0.6 
- D. 224.0.0.2

A. B, 224.0.0.9 is used by RIPv2 to advertise routes
- 224.0.0.5 is used by OSPF for hello messages.
- 224.0.0.6 is used by OSPF for hello messages for designated routers
- 224.0.0.2 is a special multicast group for all routers

6. B, use a static route. 

7. Which routing protocol will not contain a topology of the network? 
- A. EIGRP
- B. RIP
- C. OSPF 
- D. BGP

A. B.

8. Which routing loop avoidance method is used by routers to prevent routing updates from exiting an interface in which they have been learned?
- A. Routing to infinity 
- B. Route poisoning 
- C. Holddowns
- D. Split horizon

A. D, the split horizon method prevents routing updates from exiting an interface in which they have been learned. This stops false information from propagating in the network, which can cause a routing loop. 

9. You are examining a routing table and see a route marked with S*. Which type of route is this?
- A. Static route
- B. Default route 
- C. Dynamic route 
- D. OSPF route

A. B, although this is a static route, it is a special static route called a default route, or gateway of last resort. The S signifies that it is static and the * signifies the default route. 

10. You are examining a routing table and see the entry in the following exhibit. What does the 4 in the underlined number represent?
- A. The 4 represents the administrative distance.
- B. The 4 represents the protocol.
- C. The 4 represents the metric.
- D. The 4 represents the position in the routing table.

A. C, the 4 represents the metric for the routing statement. Since the image is a RIP entry the metric is the number of hops for the particular route. 

11. Which command will allow you to verify routes line by line in a subset of the general route statement?
```
A. Router#show ip route 160.45.23.0 255.255.255.0 longer-prefixes
B. Router#show ip route 160.45.23.0 255.255.255.0
C. Router#show ip route bgp
D. Router#show ip route
```

A. A, the command with [longer-prefixes] will detail all of the specific routes contained in the route for the ip network given

12. Examining the show ip route statement in the exhibit, which will be the next hop for a destination address of 192.168.1.5?
- A. The gateway 172.16.1.200 
- B. The exit interface Serial 0/0 
- C. The gateway 172.16.1.100 
- D. The exit interface Ethernet 0

A. B. 

13. Which route statement is configured when an IP address of 203.80.53.22/19 is configured on an interface?
- A. S 203.80.16.0/19 is directly connected, Serial 0/0/0 
- B. S 203.80.32.0/19 is directly connected, Serial 0/0/0
- C. S 203.80.48.0/19 is directly connected, Serial 0/0/0
- D. S 203.80.53.22/19 is directly connected, Serial 0/0/0

A. B, the IP belongs to this network 

14. B. 
15. C. 
16. C. 
17. D. 

18. You need to create a route for 205.34.54.85/29 with the next hop being 205.34.55.2. Which command would create this route?
- A. Router(config)#ip route 205.34.54.85/24 205.34.55.2
- B. Router(config)#ip route 205.34.54.85 255.255.255.248 205.34.55.2
- C. Router(config)#ip route 205.34.54.85 255.255.255.240 205.34.55.2
- D. Router(config)#ip route 205.34.55.2 255.255.255.248 205.34.54.85

A. B.

19. When a static route is made, what is the default AD? 
- A. AD of 1
- B. AD of 0 
- C. AD of 2 
- D. AD of 255

A. static routes are highly trusted routes as an admin created them. Therefore they have the lowest AD of 1. AD of 0 is used for connected routes.

20. What is the AD of RIP? 
- A. AD of 90
- B. AD of 100 
- C. AD of 110 
- D. AD of 120

A. D

21. Why are ADs used with routing tables?
- A. ADs define protocol standards.
- B. ADs define reliability of routing protocols.
- C. ADs allow for the shortest distance between routes.
- D. ADs are programmed by the administrator for path selection.

A. B, AD is an order of reliability between dynamic routing protocols and static routes. Administrative Distances do not define protocol standards; they only reference them. they do not allow for the shortest distance between routers, they allow the router to choose the best path to the destination network.

22. What is the AD of a directly connected network? 
- A. The AD is 0.
- B. The AD is 1.
- C. The AD is 5.
- D. Directly connected networks do not have an AD.

A. A. 

23. What is the AD of internal EIGRP? 
- A. 90
- B. 100
- C. 110
- D. 120

A. A. 

24. What is the definition of route statement AD?
- A. The AD is a metric that routing protocols use to select the best route.
- B. The AD is a value assigned by network administrators for route selection.
- C. The AD is a rating of trust when multiple routes exist to the same destination.
- D. The AD is a value associated with the cost to the destination.

A. C. 

25. Which must be configured so that EIGRP can calculate the best route?
- A. Bandwidth 
- B. Delay
- C. Reliability 
- D. Load

A. A.

26. You perform a show ip route on the router and see several routes with an AD of 90. Which routing protocol has generated these route statements?
- A. IGRP 
- B. OSPF 
- C. EIGRP 
- D. RIP

A. C. 

27. Which statement is true when there are multiple route statements from different routing protocols for the same destination network?
- A. The route is chosen with the highest AD.
- B. The route chosen has the lowest metric. 
- C. The route is chosen with the lowest AD. 
- D. The route chosen has the highest metric.

A. C. 

28. You have a network with varied bandwidths and need to choose a dynamic routing protocol. Which would you choose for optimal performance?
- A. RIPv1 
- B. RIPv2 
- C. EIGRP 
- D. BGP

A. C.

29. What is the Cisco metric for OSPF? 
- A. 108/bandwidth
- B. Delay, bandwidth, reliability, load 
- C. K metrics
- D. Bandwidth

A: Cisco uses a metric for OSPF that is calculated as 10**8/ bandwidth. This cost value is of 100 mbs (reference bandwidth) divided by the interface bandwidth.

30. You enter a show ip route command and see the following line. What does the [110/1] identify?
O 192.168.3.0/24 [110/1] via 192.168.10.6, 00:58:55, Serial0/3/1 
- A. AD of 110 and a 100 Mb/s link
- B. AD of 110 and a 10 Mb/s link
- C. AD of 1 and a 110 Mb/s link
- D. AD of 110 and a 1 Gb/s link

A. A. 

31. What type of route is the destination of 0.0.0.0/0?
- A. Local route
- B. Dynamic route 
- C. Default route 
- D. Loopback route

A. C.

32. What role does ICMP take in the routing of a packet? 
- A. ICMP populates the routing table.
- B. ICMP is used when routes are not reachable.
- C. ICMP maintains the routing table.
- D. ICMP performs continuous diagnosis of the network paths.

A. B.

33. How is a route selected when the route table contains overlapping destination prefixes?
- A. The route with the lowest cost is selected.
- B. The route with the longest matching prefix is selected. 
- C. The route with the highest AD is selected.
- D. The route with the lowest AD is selected.

A. B.

34. You are examining a router and discover that there is a static default route configured for a next hop of 192.168.1.2. You also notice that there is a default route being populated from RIP for a next hop of 192.168.2.2. Which default route will be selected?
A. The route with the lowest AD
B. The route with the highest AD
C. The route with the lowest metric
D. The route being populated from RIP

A. A, since both are default routes, the route with the lowest AD will be selected. 

35. Which is true of a host route in the routing table?
- A. The host route is the route a packet will take if no other route matches in the routing table.
- B. The routing table creates host routers for the destination hosts it discovers.
- C. A host route is a specific route with a netmask of /32 for a specific host.
- D. The host route is populated from HSRP.

A. C, a host route is used when you need a to route packets to a different next hop for a specific host 

36. Which element of a routing table will identify where the route was learned from?
- A. Prefix and network mask 
- B. Routing protocol code
- C. Metric
- D. Next hop

A. B, the routing code protocol is in the form of a single letter at the beginning of each statement. 

37. Which criteria are routing decisions based upon?
- A. Source IP
- B. Destination IP address
- C. TTL
- D. Destination MAC address

A. B.

38. Which type of routing requires network administrator intervention? 
- A. Link-state routing
- B. Distance-vector routing 
- C. Static routing
- D. Dynamic routing

A. C. 

39. Which is a correct statement about the subnet mask?
- A. The subnet mask is used by the host to determine the destination network.
- B. The subnet mask is used in routing to determine the destination network.
- C. The router uses its subnet mask when routing a packet.
- D. The destination computer checks the subnet mask on the packet to verify that it’s intended for that computer.

A. A, the subnet mask is used by the host to determine the immediate network and the destination network. It then decides to either route the packet or try to deliver the packet itself without the routers help. The subnet mask of the destination network is not used to determine routing decisions because the sending host does not know the destination subnet mask. 

40. What protocol does the router or host use to find a MAC address for the frame when it determines that the packet is on the local network?
- A. IGMP 
- B. RARP 
- C. ARP 
- D. ICMP

A. C.

41. When a packet is determined to be remote from the network of the sending host, what happens?
- A. The destination IP address is changed to the router’s IP address.
- B. The destination MAC address is changed to the destination host’s MAC address.
- C. The destination MAC address is changed to the router’s MAC address.
- D. The source IP address is changed to the router’s IP address.

A. C, the destination MAC address is changed to the routers MAC address and the destination IP address is untouched. The destination IP address is not changed throughout the routing process. The destination MAC address is only changed to the destination hosts MAC address if the traffic is deemed to be local. 

42. Which statement describes correctly what happens when a packet moves through a router?
- A. The destination IP address is changed to the original destination.
- B. The packet’s TTL is decremented.
- C. The source MAC address is changed to the original source MAC address.
- D. All of the above.

A. B.

43. When a packet is determined to be on the local network, what happens?
- A. The destination IP address is changed to the router IP address.
- B. The destination MAC address is changed to the destination host’s MAC address.
- C. The destination MAC address is changed to the router’s MAC address.
- D. The source IP address is changed to the router’s IP address.

A. B, when a packet is determined to be local to the sending host, ARP is used to resolve the MAC address for the IP address of the destination host, and the frame is sent directly to the host. 

44. How does the sending host know if the destination is local or remote
with respect to its immediate network?
- A. The host compares the IP address to its internal routing table.
- B. The host performs ANDing on its subnet mask and the destination IP address, comparing the result to its own network address.
- C. The host performs ANDing on the destination subnet mask and the destination IP address, comparing the result to its own network address.
- D. The IP address is verified to be local to its network via ICMP.

A. B, the sending host ANDs its subnet mask against the destination IP address, then against its IP address and this gives a frame of reference for where it needs to go and where it is.

45. What is the current method Cisco routers use for packet forwarding?
- A. Process switching
- B. Fast switching
- C. Intelligent packet forwarding 
- D. Cisco Express Forwarding

A. D, the current method of packet forwarding used by Cisco routers is Cisco Express Forwarding (CEF). CEF creates several cache tables used for determining the best route for the destination network.

46. What is the process called at layer 2 when a packet hops from router to router and eventually to the host?
- A. IP routing
- B. Frame rewrite 
- C. Packet hopping 
- D. Packet switching

A. B, the layer 2 process is called frame rewrite. When a packet hops from router to router, the destination frame is rewritten for the next destination MAC address. 

47. When a host sends an ARP request packet out, what is the destination address of the frame?
- A. The router’s MAC address
- B. The host’s MAC address
- C. The MAC address, in the form of a broadcast 
- D. The MAC address, in the form of a multicast

A. C. 

48. What does every network device use to limit the number of ARP packets?
- A. ARP cache
- B. IP multicasting 
- C. Frame casting 
- D. IP cache

A. A, every host contains an ARP cache. This cache allows for lookups of MAC addresses for destination IP addresses when the host frequently sends packets to the destination IP addresses

49. Which statement describes what happens when a packet enters a router?
- A. The router accepts all incoming frames regardless of their destination MAC address.
- B. The router decapsulates the packet and inspects the destination IP address.
- C. Routers do not need to decapsulate packets to inspect the destination IP address.
- D. Routers make routing decisions first by examining the source MAC address.

A. B, after the frame is verified to be addressed to the router and the FCS has been checked, the router decapsulates the packet and strips off the frame. 

50. Which command will display the router’s ARP cache? 
```
- A. Router#show arp
- B. Router#show arp table 
- C. Router#show arp cache 
- D. Router#show ip arp
```

A. D.

51. What is the default time an entry will live in the ARP cache?
- A. 180 seconds
- B. 240 seconds 
- C. 300 seconds 
- D. 600 seconds

A. By default all entries have a TTL of 240 seconds

52. Which type of routing allows for routers to share their routing tables with other routers in the network?
- A. Default routing 
- B. Stub routing
- C. Static routing
- D. Dynamic routing

A. Dynamic routing, EIGRP, RIP and OSPF

53. Which statement describes what happens during the routing process?
- A. As a packet travels through the routers, the TTL of the packet will increase by one.
- B. When a route to the destination network is found, the router will attach the destination MAC address for the next hop to the packet.
- C. When a packet travels through the router, the transport information will be checked for the destination network.
- D. When a route to the destination network is found, the router will attach the destination IP address for the next hop to the packet.

A. B, when a route is found in the routing table, the router will find the gateway for the next hop and change the packets destination MAC address for the next router. 

54. Which protocol allows for testing and connectivity of a route?
- A. IGMP
- B. RARP 
- C. ARP 
- D. ICMP

A. D.

55. Which routing protocol is a distance-vector routing protocol? 
- A. OSPF
- B. RIP
- C. EIGRP 
- D. BGP 

B, RIP is distance-vector, OSPF is link-state, BGP is a path-vector and EIGRP is a hybrid closely resembling a link state.

56. When an ICMP packet reaches a router for which it has no further route, what happens?
- A. The router will discard the packet without notification.
- B. The router will change the TTL of the packet to 0.
- C. The router will send the packet back to the originating host. 
- D. The router will send back a destination unreachable message.

A. D

57. Which statement accurately describes a routing loop?
- A. Packets are routed out one interface but come back on a different interface.
- B. Packets are transmitted within a series of routers and never reach the destination.
- C. Packets reach the expiry TTL before reaching the destination network.
- D. Packets are routed via an inefficient path.

A. B, routing loops occur when packets are routed between two or more routers and never make it to there destination. 

58. Which routing protocol is a link-state routing protocol?
- A. OSPF
- B. RIP
- C. EIGRP 
- D. IGRP

A. A. 

59. Where are dynamic routes stored in a router? 
- A. RAM
- B. Flash
- C. Startup configuration
- D. Running configuration

A. A.

60. Which is a correct statement about SVI inter-VLAN routing (IVR)?
- A. Latency is low with SVI IVR because of ASICs.
- B. Latency is high with SVI inter-VLAN routing because of resource use.
- C. SVI inter-VLAN routing is a cheaper alternative to ROAS.
- D. Bandwidth is limited compared to ROAS.

A. A, latency is lower with SVI inter-VLAN routing because of the use of ASICs, this is usually why IVR switches are more expensive.

61. Which is a disadvantage of using ROAS?
- A. The lack of ISL support for VLANs.
- B. The number of VLANs you can route is tied to the number of physical ports.
- C. Scalability of ROAS for the number of VLANs.
- D. The lack of dynamic routing protocol support.

A. C.

62. Which is a correct statement about IVR?
- A. Each VLAN requires a unique IP network.
- B. IVR reduces the number of broadcast domains. 
- C. It does not support ACLs.
- D. IVR restricts the use of subnetting.

A. A.

63. What is the method of using a single router interface to route between VLANs called?
- A. Interface routing 
- B. ROAS routing 
- C. SVI routing
- D. Bridge routing

A. B.

64. What is a disadvantage of routing between VLANs on a router’s interface?
- A. Routers do not handle large amounts of traffic very well. 
- B. When using ROAS, bandwidth problems are encountered. 
- C. Security cannot be implemented with ROAS.
- D. Broadcast traffic is increased.

A. B.

65. What is the method of routing between VLANs on a layer 3 switch? 
- A. Interface routing
- B. ROAS routing 
- C. SVI routing 
- D. Bridge routing

A. C. 

66. Which routing technique requires no administrator intervention when a route goes down?
- A. Dynamic routing
- B. Directly connected routes 
- C. Default routing
- D. Static routing

A. A.

67. Which routing technique requires increased time for configuration as networks grow?
- A. RIP routing 
- B. OSPF routing
- C. Static routing
- D. Default routing

A. C.

68. Which routing technique requires the lowest amount of router RAM consumption?
- A. RIP routing 
- B. OSPF routing 
- C. Static routing 
- D. Default routing

A. D, default routing requires the least amount of RAM consumption because one routing statement is required for all of the upstream networks. Best used on stub network routers. 

69. Which dynamic routing protocol has the lowest overhead? 
- A. BGP
- B. OSPF 
- C. RIP
- D. EIGRP

A. C, but not scalable with max hops of 15.

70. Which is an advantage of dynamic routing protocols? 
- A. Resiliency when routes become unavailable
- B. Lower router RAM usage
- C. Lower router CPU usage
- D. Less bandwidth usage

A. A.

71. Which routing protocol broadcasts updates for routes?
- A. RIP
- B. OSPF 
- C. EIGRP 
- D. BGP

A. A, RIP broadcasts updates for routing tables. OSPF exclusively uses multicast to send updates. EIGRP uses multicast to send updates as well and has a backup of direct unicast. BGP uses unicast to retrieve updates on network paths.

72. What is an advantage of dynamic routing protocols?
- A. Centralized routing tables
- B. Optimized route selection
- C. Ease of configuration
- D. Lower bandwidth utilization

A. B.

73. Which routing protocol has a maximum of 15 hops?
- A. RIP
- B. OSPF 
- C. EIGRP 
- D. BGP

A: A.

74. Which protocol is considered a hybrid protocol? 
- A. RIP
- B. OSPF 
- C. EIGRP 
- D. BGP

A. C.

75. What is a characteristic of distance-vector protocols? 
- A. They track the status of routes learned.
- B. They re-advertise routes learned.
- C. Each router keeps its own topology database. 
- D. Each router checks the routes it learns.

A. B, protocols such as RIP, re-advertise routes learned. This can be problematic as it is the equivalent of gossip - routes learned through this method are never tracked for status or double checked for validity.

76. Which type of network are distance-vector protocols best suited for? 
- A. Networks containing fewer than 255 routes
- B. Networks containing fewer than 15 routers
- C. Networks containing more than 15 routers
- D. Networks containing more than 255 routers

A. B.

77. Which problem could arise from use of a distance-vector routing protocol?
- A. Routing loops
- B. Router incompatibility
- C. Complexity of configuration
- D. Default route advertisement

A. A, routing loops are the most common problem when you are using a distance-vector routing protocol. Although they can occur with any dynamic routing protocol, distance distance-vector protocols are most susceptible due to how they converge routes. 

78. Which dynamic routing protocol uses the Diffusing Update Algorithm as its routing algorithm?
- A. RIP
- B. EIGRP 
- C. OSPF 
- D. BGP

A. B, the diffusing update algorithm, or DUAL, is used by EIGRP to calculate the best route for the destination network.

79. Which is a disadvantage of distance-vector routing protocols? 
- A. Router incompatibility for RIP
- B. Slow convergence of routing tables
- C. Resource usage of CPU and RAM
- D. The complexity of RIP design

A. B, slow convergence of routing tables is a major disadvantage for distance-vector protocols like RIP. It could take several announcement cycles before the entire network registers a routing change.

80. Which dynamic routing protocol uses the Bellman-Ford routing algorithm?
- A. RIP
- B. EIGRP 
- C. OSPF 
- D. BGP

A. A, RIP uses Bellman-Ford, EIGRP use DUAL, OSPF uses the Dijkstra algorithm and BGP uses the best path algorithm that determines the best path between two networks.


81. Which is a design concept used to stop routing loops with distance-vector dynamic routing protocols?
- A. Use of a topology database
- B. Use of holddown timers
- C. Use of anti-flapping ACLs
- D. Use of counting-to-infinity conditions

A. B, the use of holddown timers allows the convergence of the network routing tables. This is used to hold down changes to the routing table before convergence can happen and a routing decision is hastily made by RIP.

82. Which is an exterior gateway routing protocol? 
- A. RIPv1
- B. OSPF 
- C. EIGRP 
- D. BGP

A. D. 


83. Which protocol is a Cisco proprietary interior gateway protocol? 
- A. RIPv1
- B. OSPF 
- C. EIGRP 
- D. BGP

A. C.

84. Which statement is correct about interior gateway protocols (IGPs) vs. exterior gateway protocols (EGPs)?
- A. IGPs are used to exchange information between autonomous systems.
- B. EGPs are used to exchange information between routers within an autonomous system.
- C. IGPs are used to exchange information between routers within an autonomous system.
- D. EGPs are used in the core of an internal network.

A. C. 
85. Which statement is correct about IGPs?
- A. IGPs require a small number of resources, such as CPU and RAM.
- B. IGPs function within an administrative domain.
- C. An EGP is an example of an IGP.
- D. IGPs use autonomous system numbers (ASNs) that have been assigned by ARIN.

A. B.

86. Why would you need to use an EGP?
- A. You need to connect your company to the Internet.
- B. You have been delegated a large number of IP addresses.
- C. You want to achieve fast routing to the Internet.
- D. You are dual-homed with two different ISPs.

A. D. 

87. When RIP is configured on a router, what must be configured to allow for classless routing?
```
A. Router(config)#ip classless
B. Router(config)#router rip v2
C. Router(config-router)#ip classless 
D. Router(config-router)#version 2
```

A. D.

88. You need to configure the advertisement of the network 192.168.1.0/24 for RIPv2. Which command will achieve this?
```
A. Router(config-router)#network 192.168.1.0
B. Router(config-router)#network 192.168.1.0 0.0.0.255
C. Router(config-router)#network 192.168.1.0/24
D. Router(config-router)#network 192.168.1.0 255.255.255.0
```

A. A.

89. What is the entry for the IP address in the routing table called in IOS 15 code when an interface is configured?
- A. IP address route 
- B. Local route
- C. Dynamic route 
- D. Static route

A. B.

90. Which metric does RIPv2 use to calculate routes?
- A. Delay
- B. Bandwidth
- C. Hop count
- D. Bandwidth and delay

A. C.

91. Which command will allow you to inspect RIPv2 calculations for routes discovered?
```
A. Router#show ip protocols rip
B. Router#show ip rip database 
C. Router#show ip interface
D. Router#show ip rip topology
```

A. B.

92. Which command would allow you to see the next hop information for CEF?
```
A. Router#show cef
B. Router#show ip cef
C. Router#show cef nop 
D. Router#show cef route
```

A. B.

93. Which component of a network transmission changes during the routing process?
- A. Destination MAC address 
- B. Destination IP address
- C. Source IP address
- D. Internal routes

A. B. 

94. What will a router do if a matching route is not present in the router table?
- A. Flood the packet to all active interfaces
- B. Multicast the packet to other routers
- C. Drop the packet
- D. Send the original packet back to the source

A. C.

95. By default, which type of routing is used automatically on a router? 
- A. Default routing
- B. Dynamic routes 
- C. Static routes
- D. Connected routes

A. D, by default, directly connected routes are used automatically on routers to create routes in the route table. 

96. Which command would set the IPv6 default route for a router to interface s0/0?
```
A. Router(config)#ip route 0.0.0.0/0 s0/0
B. Router(config)#ipv6 route 0.0.0.0/0 s0/0
C. Router(config)#ipv6 unicast-route ::0/0 s0/0 
D. Router(config)#ipv6 route ::0/0 s0/0
```

A. D.

97. Which dynamic routing protocol(s) can be used with IPv6? 

A. RIPng
B. OSPFv3
C. EIGRPv6
D. All of the above

A. D. 


98. You need to see all routes in the routing table for only IPv6. Which command will achieve this?
```
A. Router#show route
B. Router#show ip route 
C. Router#show ipv6 route 
D. Router#show route ipv6
```

A. C.

99. What is the relevance of the default gateway address on a host that is transmitting to a destination for the first time?
- A. The destination IP address is replaced with the default gateway when the destination is remote.
- B. The host sends the default gateway packets that are deemed remote via a broadcast.
- C. The host sends an ARP packet for the default gateway when the destination is remote.
- D. The host creates a dedicated connection with the default gateway for remote traffic.

A. C, when traffic is remote to the immediate network, the host sends an ARP packet for the IP address of the default gateway. This determines the destination MAC address for the frame. The destination IP address is never replaced throughout the entire routing process. 

100. Which command will display the router’s routing table?
- A. Router#show ip route
- B. Router#show route
- C. Router#show route table 
- D. Router#show routes

A. A.

101. Which protocol is used by TCP/IP to help facilitate the routing of packets?
- A. IGMP 
- B. RARP 
- C. ARP 
- D. ICMP

A. C, ARP is used by TCP/IP to resolve a MAC address from a known IP address. This in turn allows TCP/IP to packet switch from router to router by sending the packet to the next destination MAC address

102. What uses ICMP to directly check the status of a router? 
- A. SNMP traps
- B. Notifications 
- C. Ping
- D. ARP

A. C:

103. You have just used the ping command for a distant router. You received back five exclamation marks. What do these mean?
- A. The distant router is not responding.
- B. The distant router has a high response time. 
- C. The distant router is responding.
- D. The distant router has a low response time.

A. C.

104. You need to create a route for a network of 192.168.4.0/24 through the gateway of serial 0/1 on a 2621 router. Which is the proper command?
```
A. Router(config)#ip route 192.168.4.0/24 serial 0/1
B. Router(config)#ip route 192.168.4.0 255.255.255.0
serial 0/1
C. Router(config)#ip route 192.168.4.0/24 interface serial 0/1
D. Router(config)#ip route Router(config- rtr)#192.168.4.0/24 serial 0/1
```

A. B.

105. You type into the router ip default-gateway 192.168.11.2. Why will traffic not route out the default gateway?
- A. The ip default-network needs to be used in conjunction with ip default-gateway 192.168.11.2.
- B. The command is only used for the management plane of the router itself.
- C. The command is used for dynamic routing only.
- D. The specified gateway is wrong.

A. B, the command allows the management plane of the router to egress the network the router is configured upon though a different gateway. It is not used for dynamic routing, it is strictly used for the management traffic of a router.

106. C.

107. When you configure an IP address on a router interface, what happens to the routing table?
- A. The router creates a /32 route for the IP address.
- B. The router creates a summary address for the network.
- C. The router creates a routing update if dynamic routing is configured.
- D. All of the above.

A. D.

108. You want to verify the IP addresses configured on the router. Which command will you use?
```
- A. Router#show ip
- B. Router#show ip interfaces brief 
- C. Router#show interfaces
- D. Router#show ip brief
```
A. B.

109. You configure a brand-new IP address on a new router’s interface. However, when you look at the routing table, it does not show up. You see a link light on the interface. What is wrong?
- A. The interface is administratively shut down.
- B. The interface speed is incorrect.
- C. The interface bandwidth is not set.
- D. The route will not show up until you save the config.

A. A. 

110. What is a benefit of static routing?
- A. Adding networks is an easy task for network administrators.
- B. It is suited for large networks because changes will not disturb routing.
- C. It reduces bandwidth used by router-to-router communications.
- D. It allows for configuration by any network admin in the network.

A. C, static routing is suited for small networks, where the central admin has a good understanding of the network layout.

111. Where are static routes stored?
- A. RAM
- B. Flash
- C. Startup configuration 
- D. Routing database

A. C, when you configure a static route it is temporarily stored in the runing-configuration. After it is saved by using [copy runing-configuration startup-config], it is stored in the startup configuration and can survive reboots. 

112. You want to route 192.168.1.0/24, 192.168.2.0/24 to a destination address of 198.43.23.2. How can you accomplish this with one route statement so that other networks are not affected?
```
A. Router(config)#ip route 192.168.0.0 255.255.0.0 198.43.23.2
B. Router(config)#ip route 192.168.0.0 255.255.255.0 198.43.23.2
C. Router(config)#ip route 192.168.0.0 255.255.240.0 198.43.23.2
D. Router(config)#ip route 192.168.0.0 255.255.0.240 198.43.23.2
```

A. C, super-net the addresses together.

113. Why would you create a second route statement to the same network using a different AD and different interface?
- A. If the first one fails to route to the destination, the second route will succeed.
- B. If the first interface goes down, the second route will become active.
- C. If there is a high amount of traffic on the first interface, the second route will become active.
- D. If there is a routing loop on the first interface, the second will overcome the loop.

A. B


114. Which route statement is configured when an IP address of 208.43.34.17/29 is configured on an interface?
- A. S 208.43.34.17/32 is directly connected, Serial 0/0/0 
- B. S 208.43.34.24/29 is directly connected, Serial 0/0/0 
- C. S 208.43.34.8/29 is directly connected, Serial 0/0/0 
- D. S 208.43.34.17/29 is directly connected, Serial 0/0/0

A. A.

115. D.
116. D.

117. Which route statement is configured when an IP address of 194.22.34.54/28 is configured on an interface?
- A. S 194.22.34.48/28 is directly connected, Serial 0/0/0 
- B. S 194.22.34.64/28 is directly connected, Serial 0/0/0 
- C. S 194.22.34.54/28 is directly connected, Serial 0/0/0 
- D. S 194.22.34.32/28 is directly connected, Serial 0/0/0

118. Which command will create a default route through Serial 0/0 for IPv6?
```
A. Router(config)# ip route 0.0.0.0 0.0.0.0 serial 0/0 
B. Router(config)# ipv6 route 0.0.0.0 0.0.0.0 serial 0/0 
C. Router(config)# ipv6 route ::/0 serial 0/0
D. Router(config)# ip route ::/0 serial 0/0
```

A. C.

119. Which command would configure the route for an IPv6 network of FC00:0:0:1 with the exit interface of serial 0/0/0?
```
A. Router(config)#ip route fc00:0:0:1 serial 0/0/0
B. Router(config)#ipv6 route fc00:0:0:1/64 serial 0/0/0 
C. Router(config)#ip route fc00:0:0:1/64 serial 0/0
D. Router(config)#ipv6 route fc00:0:0:1 serial 0/0/0
```

A. B.

120. A.

121. What is the purpose of issuing the command no switchport on a layer 3 switch?
- A. It configures an SVI.
- B. It configures an access port.
- C. It configures a trunk port.
- D. It configures a port as a routed interface.

A. D.

122. You need to configure a router that has three interfaces to route five VLANs. What is the best way to accomplish this task?
- A. Purchase another router with additional interfaces. 
- B. Configure the router as a ROAS.
- C. Purchase a new router with five interfaces.
- D. Configure a dynamic routing protocol.

A. B.

123. Which command do you need to enter on a switch to allow routing between VLANs?
- A. Switch(config)#routing 
- B. Switch(config)#ip router
- C. Switch(config)#ip routing
- D. Switch(config)#ip route

A. C.

124. When routing between VLANs with a router’s interface, which
trunking protocol is always supported? 
- A. 802.1x
- B. 802.1Q
- C. ISL
- D. VTP

A. B.

125. Which command would configure the interface on the ROAS configuration as the native VLAN?
- A. Router(config-subif)#switchport native vlan 2
- B. Router(config-if)#interface gi 0/1.2 native
- C. Router(config-subif)#native vlan 2
- D. Router(config-subif)#encapsulation dot1q 2 native

A. D, [encapsulation dot1q 2] will associate the subinterface with VLAN 2. If you specify the native tag after the command, it will make the subinterface native VLAN for the trunk.

126. Which commands would you use to configure an IP address on an SVI?
```
A. 
Switch(config)#interface vlan 10
Switch(config-if)#ip address 192.168.10.1 255.255.255.0 
Switch(config-if)#no shutdown

B. 
Switch(config)#interface vlan 10 
Switch(config-if)#ip address 192.168.10.1/24

C. 
Switch(config)#interface vlan 10 
Switch(config-if)#ip address 192.168.10.1/24 
Switch(config-if)#no shutdown

D. 
Switch(config)#vlan 10
Switch(config-vlan)#ip address 192.168.10.1 255.255.255.0
Switch(config-vlan)#no shutdown
```

A. A.

127. When configuring ROAS, which mode must be configured for the switch port on the switch?
- A. Trunk mode
- B. Access mode 
- C. Routed mode 
- D. Switched mode

A. A.

128. When configuring the subinterfaces on a router for ROAS, what is a best practice when naming the subinterface?
- A. Always name the subinterface the same as the VLAN name.
- B. Always name the subinterface the same as the VLAN number.
- C. Always name the subinterface the same as the default gateway address.
- D. Always name the subinterface the same as the switch’s interface number.

A. B.

129. Which command enables the routers to direct the frames for a particular VLAN to the subinterface?
- A. Router(config-if)#interface gi 0/1.5
- B. Router(config-subif)#vlan 5
- C. Router(config-subif)#encapsulation dot1q 5
- D. Router(config-subif)#switchport access vlan 5

A. C, when configured inside of the sub interface to accept frames for VLAN 5

130. Which command must be entered on 2960-XR switches to enable IP routing?
- A. Switch(config)#ip lanbase
- B. Switch(config)#sdm prefer lanbase-routing 
- C. Switch(config)#sdm lanbase-routing
- D. Switch(config)#sdm routing

A. B, on 2960-XR switches, you must enable the SDM for LAN Base routing to enable routing. The switch then requires a reload before you can configure routable SVIs.

131. You want to verify the configured SVI VLAN interfaces. Which command will show you the configured IP addresses on each of the SVI VLAN interfaces?
```
A. Switch#show ip interface brief 
B. Switch#show interfaces status 
C. Switch#show svi
D. Switch#show switchports ip
```

A. A, the same command used to verify physical interfaces on a router is used to verify SVI interfaces on a switch.

132. You enter the command ip address 192.168.2.0 255.255.255.0 on interface VLAN 2. When you enter the command, you receive a “Bad mask /24 for address” error. What is the problem?
- A. The subnet mask is incorrect.
- B. The subnet of 192.168.2.0 cannot be used for this interface. 
- C. The IP address is invalid.
- D. The VLAN has not been configured yet.

A. C.

133. You have purchased a layer 3 switch with the LAN Base feature. When you enter ip routing in global configuration mode, you receive an “Invalid input detected” error. What is the problem?
- A. There are no IP addresses configured on the switch. 
- B. The SDM of LAN Base routing has not been enabled. 
- C. There is not enough memory for routing tables.
- D. The IP Base feature is required.

A. B, The LAN base feature supports IP routing between SVIs. However it must first be enabled via the Switching Database Manager

134. You have a 3560 switch that supports layer 3 routing. You need to configure a physical interface to route a subnet. Which command needs to be used?
A. Switch(config-if)#switchport routed
B. Switch(config-if)#no ip-routing
C. Switch(config-if)#no switchport
D. Switch(config-if)#ip address 192.168.2.1 255.255.255.0

A. C.

135. Which command will allow you to examine a switch’s port to see if it is routed or switched?
```
A. Switch#show interface gi 0/2 switchport 
B. Switch#show interface gi 0/2 state
C. Switch#show switchport interface gi 0/2 
D. Switch#show status interface gi 0/2
```

A. A.

136. You need to configure ROAS on a router’s interface to route VLAN 5 with ISL. Which command will specify the encapsulation and achieve this?
```
A. Router(config-if)#encapsulation 5
B. Router(config-if)#encapsulation isl 5
C. Router(config-subif)#switchport encapsulation isl 5 
D. Router(config-subif)#encapsulation isl 5
```

A. D.

137. You have just configured a new VLAN and have configured the SVI with an IP address and no shutdown command on the interface. However, when you perform a show ip route, it does not show a valid directly connected route for the SVI. What is the problem?
- A. The VLAN is in a shutdown state.
- B. No interfaces have been configured with the new VLAN yet.
- C. The show ip route command will not display SVI directly connected routes.
- D. No dynamic routing protocols have been configured.

A. B, after configuring a VLAN and the respective SVI interface, a route will not show until at least one port is configured with the new VLAN and it is in an up status.

138. Which of the following is a correct statement about ROAS?
- A. Using a ROAS is a highly efficient alternative to routed SVIs.
- B. Using a ROAS is a cheaper alternative to inter-VLAN routing on a switch.
- C. A ROAS can only be used with 802.1Q.
- D. A ROAS is limited to a maximum of 16 routes.

A. B, ROAS is a cheaper alternative to IVR if the current switch does not support layer 3 routing.  

139. Before configuring ROAS, which command should be entered in the interface connecting to the switch?
```
A. Router(config-if)#ip routing
B. Router(config-if)#no ip address
C. Router(config-if)#ip encapsulation dot1q 
D. Router(config-if)#sdm routing
```

A. When configuring ROAS on a routers interface, you should always issue the [no ip address] command. No IPs can be configured on the main interface.

140. You have configured a ROAS and set up the switch to connect to the router. However, you cannot route between VLANs. Which command would you use on the switch to verify operations?
```
A. Switch#show ip route
B. Switch#show interface status 
C. Switch#show interface trunk 
D. Switch#show switchport
```

A. C, verifying the proper operation of the switch would start with verifying that the port is correctly set as a trunk to the router. If it is not set as a trunk it wont be able to tag frames for the router to direct to the proper interfaces.

141. When configuring a router in a ROAS configuration, which command will enable the interface to accept frames tagged for VLAN 10?
```
A. Switch(config-subif)#encapsulation vlan 10 dot1q
B. Switch(config-if)#interface Fa 0/0.10
C. Switch(config-subif)#encapsulation dot1q 10
D. Switch(config-subif)#ip address 192.168.10.1 255.255.255.0
```

A. C. 

142. Which statement is correct about ARP in relation to ROAS?
- A. Each physical interface has a unique MAC address, which responds to ARP requests.
- B. Each subinterface has a unique MAC address, which responds to ARP requests.
- C. Each IP address has a unique MAC address, which responds to ARP requests.
- D. All of the above.

A. A, when ROAS is implemented, only the physical interface has a unique MAC address. All ARP requests for the IP addresses configured on the subinterfaces respond with the same MAC address. They are not unique, but on each VLAN they are unique in the sense that no other machines on the VLAN share the same MAC address.

143. Which statement is correct about implementing ROAS?
- A. Each IP address is configured on the subinterface as the gateway for the VLAN.
- B. The main interface must be configured with the summary IP address for all VLANs.
- C. You must configure at least one native VLAN.
- D. All of the above.

A. Each IP address on a subinterface is the routed gateway for the VLAN on that subinterface. 

144. Which routing technique is a type of static routing?
- A. OSPF routing 
- B. EIGRP routing 
- C. Default routing 
- D. RIP routing

A. Default routing is a form of static routing. It is used on the edge of a network to direct all traffic to the inner core of the network.

145. Which is an advantage of using static routing? 
- A. There is less administrative overhead.
- B. It is extremely secure.
- C. It can create resiliency in a network.
- D. It is extremely scalable without issues.

A. B, static routing is extremely secure because it does not need to broadcast or multicast routing updates. Updates can be intercepted or injected into a network to create problems.

146. Which routing technique has the lowest bandwidth overhead?
- A. RIP routing
- B. OSPF routing 
- C. EIGRP routing 
- D. Static routing

A. D, static routing has the lowest bandwidth overhead because there is no bandwidth required to maintain static routes. 

147. Which type of routing technique allows for route summarization to be computed automatically by routers?
- A. Dynamic routing
- B. Directly connected routes 
- C. Default routing
- D. Static routing

A. A, most dynamic routing protocols will summarize routes. They do this for efficiency, so the least number of route statements will need to exist in the routing table. 

148. Which routing technique requires administrator intervention when a route goes down?
- A. Dynamic routing
- B. Directly connected routes 
- C. Default routing
- D. Static routing

A. D.

149. You have several routes configured on a router. Which command will show only the static routes?
```
A. Router#show static routes
B. Router#show ip static routes 
C. Router#show ip routes static 
D. Router#show ip routes
```

A. C, [show ip routes static] will display all of the routes that are configured as static routes.

150. On interface Serial 0/1, you type ipv6 address 2000:db8:4400:2300::1234/64. Which statement is true?
- A. The router will calculate a network ID of 2000:0db8::.
- B. The IPv6 address of 2000:0db8:4400:2300:1234:0000:0000:0000/128 will be assigned to Serial 0/0.
- C. The router will calculate a network ID of 2000:0db8:4400:2300::/64 for Serial 0/0.
- D. The router will calculate a network ID of 2000:db8:4400:2300:0000/64 for Serial 0/0.

A. C. 

151. When you check the IPv6 addresses configured on the interfaces, you find two IPv6 addresses: One address is a 2001:db8::/64 address, and the other is an ff80::/64 address. However, you do not see a route statement for the ff80::/64 address in the routing table. Why?
- A. Multicast addresses do not get added to the routing tables. 
- B. Link-local addresses do not get added to the routing tables.
- C. Only one route statement can be in the routing table at a time for an interface.
- D. Broadcast addresses do not get added to the routing tables.

A. B, ff80 is a Link-local address for Duplicate Address Detection (DAD) and Stateless Address Autoconfiguration. 

152. B.
153. C.

154. You have RIPv2 configured on an Internet-facing router. Which command will propagate the default route to all other RIPv2 routers?
```
A. Router(config-router)#network 0.0.0.0
B. Router(config-router)#default-route advertise
C. Router(config-router)#network 0.0.0.0 default
D. Router(config-router)#default-information originate
```

A. D.

155. You need to implement default routing. Which command will help you achieve this?
```
A. RouterA(config)#ip default-network 192.168.2.6
B. RouterA(config)#ip route default-gateway 192.168.2.6
C. RouterA(config)#ip route 0.0.0.0 0.0.0.0 192.168.2.6
D. RouterA(config)#ip route 0.0.0.0 255.255.255.255 192.168.2.6
```

A. C. 

156. You ping a distant router in your network and find that the TTL returned in 252. What can you conclude?
- A. The ping took 252 milliseconds.
- B. The ping has a delay of 252 milliseconds. 
- C. The ping moved through 252 routers.
- D. The ping moved through 3 routers.

A. D.

157. Which command would you use so that you can view only the RIP route entries in the route table?
```
A. RouterA#show ip rip
B. RouterA#show ip route
C. RouterA#show ip rip route 
D. RouterA#show ip route rip
```

C. A.

158. Which protocol is a true link-state protocol? 
- A. RIP
- B. OSPF 
- C. EIGRP 
- D. BGP

A. B.

159. Which dynamic routing protocol uses the Dijkstra routing algorithm? 
- A. RIP
- B. EIGRP 
- C. OSPF 
- D. BGP

A. C

160. Why don’t link-state protocols suffer from routing loops as distance- vector protocols do?
- A. Link-state protocols require routers to maintain their own topology database of the network.
- B. Link-state protocols share the topology database among all routers.
- C. Link-state protocols allow routers to maintain a link-state database of all routers.
- D. Link-state protocols use multiple routes to the same destination.

A. A, link state protocols such as ospf require all routers to maintain their own topology database of the network. This topology database is why routing loops are less likely to occur. 

161. What is an advantage of a link-state dynamic routing protocol?
- A. The only metric needed is hop count.
- B. Link-state dynamic routing protocols support CIDR and VLSM.
- C. OSPF requires only a small amount of resources such as CPU and RAM.
- D. Link-state dynamic routing protocols use triggered updates for recalculation of routing tables.

A. D, OSPF employs link-state advertisement (LSA) flooding and triggered updates. When these occur, every participating router will recalculate its routing table. 

162. What type of network is best suited for a link-state routing protocol such as OSPF?
- A. Extremely small networks of three routers
- B. Networks with routers that have a limited amount of RAM and CPU
- C. Large hierarchical networks like global networks
- D. Networks within organizations with limited training of network admins

A. C, they can seperate out the participating routers with areas and border area routers.

163. Which is an example of an interior gateway protocol that is non proprietary?
- A. EGP 
- B. OSPF 
- C. EIGRP 
- D. BGP

A. B, OSPF is an interior gateway protocol and a non proprietary standard. 

164. You have several sites, each with a different administrative unit, in your company. Which routing protocol should you choose?
- A. BGP 
- B. OSPF
- C. RIPv2
- D. EGP

A. B

165. Which area must be present when using the OSPF routing protocol with multiple areas?
- A. Area 0 
- B. Area 1 
- C. Area 10 
- D. Area 4

A. A

166. C.

167. Which multicast address is used by OSPF for neighbor discovery?
- A. 224.0.0.9
- B. 224.0.0.5 
- C. 224.0.0.6 
- D. 224.0.0.7

A. B

168. A, OSPF uses 224.0.0.5 for neighbor discovery via link-state advertisements (LSA's). OSPF uses 224.0.0.6 for DRs and BDRs.
- EIGRP uses 224.0.0.7 for neighbor routers 
- RIPv2 uses 224.0.0.9 for routing updates.

169. Which statement is true about OSPF?
- A. OSPF is a distance-vector protocol.
- B. OSPF performs default auto-summarization.
- C. OSPF broadcasts changes to the routing tables. 
- D. OSPF updates are event triggered.

A. D

170. How do Cisco routers determine their router ID (RID)?
- A. The lowest IP address configured on the loopback interfaces 
- B. The highest IP address configured on the router
- C. The lowest IP address configured on the router
- D. The highest MAC address configured on the router

A. B, highest IP address on all of the Loopback interfaces is chosen first. 

171. What is the definition of an OSPF link?
- A. Two routers participating in OSPF routing
- B. Two routers that share the same area ID
- C. A routed interface added to the OSPF process 
- D. Two routers that share the same AS number

A. C, an OSPF link is a routed interface that is assigned to a network and participates in the OSPF process. This link will be tracked by the OSPF process for up/down information as well as the network it is associated with.

172. Which statement is correct about adjacency with OSPF on a broadcast network (LAN)?
- A. An adjacency is formed between routers on the same link.
- B. An adjacency is formed between the designated router (DR) and every neighbor router on the same area.
- C. An adjacency is formed between the DR and every router in the same autonomous system.
- D. An adjacency is formed between the DR and every router in the same OSPF area.

A. B, adjacencies are formed between the designated router and its neighbors on the same area. This is done to ensure that all neighbor routers have the same Link State Database. 

173. How is a DR elected for OSPF?
- A. The DR is elected by the highest priority and highest RID in the same autonomous system.
- B. The DR is elected by the lowest priority and highest RID in the same area.
- C. The DR is elected by the lowest priority and lowest RID.
- D. The DR is elected by the highest priority and highest RID in the same area.

A. D.

174. In which database can you see all of the routers discovered in the OSPF network in which hello packets were sent and acknowledged?
- A. The routing table database 
- B. The neighborship database 
- C. The topological database 
- D. The link-state database

A. B, the neighborship database is where all of the routers can be found that have responded to hello packets. The neighborship database contains all of the routers by RID, and each router participating in OSPF manages its own neighborship database.

175. Which is a correct statement about OSPF?
- A. OSPF uses autonomous systems for scalability. 
- B. OSPF uses process IDs for scalability.
- C. OSPF uses areas for scalability.
- D. OSPF uses RID for scalability.

A. C, OSPF uses areas to create a hierarchal structure for routing. This structure begins with the backbone of area 0. All the other areas connect to it to form a complete AS. This enables scalability with OSPF since each area works independently. 

176. Which is an example of a broadcast (multi-access) network? 
- A. An X.25 network
- B. Frame Relay 
- C. ATM network 
- D. A LAN

A. D, A LAN is an example of a broadcast multi access network. All nodes in a network segment can hear a broadcast and have common access to the LAN.

177. Which multicast address is used by OSPF for communication between the DR and adjacencies formed?
- A. 224.0.0.9 
- B. 224.0.0.5 
- C. 224.0.0.6 
- D. 224.0.0.7

A. C.

178. What does the command router ospf 20 configure? 
- A. An OSPF router process ID of 20
- B. An OSPF router area of 20
- C. An OSPF router autonomous system of 20
- D. An OSPF cost of 20

A. A.

179. Which command will verify the bandwidth of an interface participating in OSPF?
- A. Router#show ospf
- B. Router#show interface
- C. Router#show running-config 
- D. Router#show ospf interface

A. B.

180. Which command will tune the cost of the OSPF metrics for integration with non-Cisco routers to participate in OSPF?
- A. Router(config-if)#ip cost 20000
- B. Router(config)#ip ospf cost 20000
- C. Router(config)#ip cost 20000
- D. Router(config-if)#ip ospf cost 20000

A. D.

181. Which command will configure a network of 192.168.1.0/24 for OSPF area 0?
```
A. Router(config)#router ospf 0 
Router(config-router)#network 192.168.1.0 0.0.0.255

B. Router(config)#ospf 0 
Router(config-router)#network 192.168.1.0 0.0.0.255

C. Router(config)#router ospf 0 
Router(config-router)#network 192.168.1.0 255.255.255.0

D. Router(config)#router ospf 1 
Router(config-router)#network 192.168.1.0 0.0.0.255 area 0
```

A. D.

182. What is the default number of equal-cost routes for OSPF on Cisco routers?
- A. 4 routes 
- B. 8 routes 
- C. 16 routes 
- D. 32 routes

A. A.

183. You want to advertise a network of 131.40.32.0/27 with OSPF. Which wildcard mask will you need to use?
- A. 255.255.224.0 
- B. 0.0.32.255
- C. 0.0.0.31
- D. 0.0.224.255

A. C.

184. Which command will allow changing the number of equal-cost routes for OSPF?
```
A. Router(config)#ospf equal-cost 10
B. Router(config-router)#ospf equal-cost 10 
C. Router(config)#ospf maximum-paths 10
D. Router(config-router)#maximum-paths 10
```

A. D, [maximum-paths 10] will configure a maximum of 10 routes of equal-cost for load balancing. This command must be entered under the OSPF router process.

185. What is the maximum number of equal-cost routes that can be configured for OSPF on Cisco routers?
- A. 4 routes 
- B. 8 routes 
- C. 16 routes 
- D. 32 routes

A. D.

186. Which command will allow you to verify the router’s RID for OSPF?
```
A. Router#show ip ospf
B. Router#show ip interface
C. Router#show ip ospf rid
D. Router#show ip ospf neighbor
```

A. A.

187. You want to advertise a network of 192.168.1.16/28 with OSPF. Which wildcard mask will you need to use?
- A. 0.0.0.16
- B. 255.255.255.240
- C. 0.0.0.15
- D. 0.0.0.240

A. C

188. Which command will allow you to verify if a remote router has formed an adjacency with the current router?
```
A. Router#show ip ospf neighbor 
B. Router#show router adjacency 
C. Router#show ip ospf
D. Router#show ip ospf router
```

A. A.

189. What is the default OSPF hello interval in which hello packets are sent out on a broadcast (multi-access) network?
- A. 5 seconds 
- B. 10 seconds 
- C. 30 seconds 
- D. 60 seconds

A. B

190. You are running OSPF on a router. One of the interfaces, Gi0/1, connects to your ISP. You want to make sure you do not forward any OSPF packets to your ISP. How can you achieve this?
``` 
A. Router(config-if)#passive-interface
B. Router(config-router)#passive-interface gigabitethernet
0/1
C. Router(config)#passive-interface gigabitethernet 0/1
D. Router(config-if)#passive-interface default
```

A. B, the command [passive-interface gigabitethernet 0/1] must be configured under the router process. This command will suppress hello packets from exiting the g0/1 interface

191. Which command will allow you to verify the interfaces that hello packets are being sent out for OSPF?
```
A. Router#show interfaces
B. Router#show ip routes
C. Router#show ip ospf interface 
D. Router#show ip ospf brief
```

A. C.

192. Which command will statically set the RID for OSPF and override all others?
```
A. Router(config)#interface fa 0/1
Router(config-if)#ip address 192.168.1.5 255.255.255.0

B. Router(config)#interface loopback 0 
Router(config-if)#ip address 192.168.1.5 255.255.255.0

C. Router(config-router)#rid 192.168.1.5

D. Router(config-router)#router-id 192.168.1.5
```

A. D.

193. Which command(s) will only allow interface Gi0/2 to send hello
packets for OSPF?
```
A. 
Router(config-router)#active-interface gigabitethernet 0/2

B. 
Router(config-router)#passive-interface default
Router(config-router)#active-interface gigabitethernet 0/2

C. 
Router(config-router)#passive-interface default 
Router(config-router)#no passive-interface gigabitethernet 0/2

D. Router(config-router)#passive-interface gigabitethernet 0/2
```

A. C, the command [passive-interface default] configured under the OSPF process will cease hello packets by default on all interfaces. 

194. After changing the router’s RID for OSPF, which command needs to be entered?
```
A. Router#clear ip ospf

B. Router(config-router)#shutdown
Router(config-router)#no shutdown

C. Router(config-router)#clear ip ospf

D. Router#clear ospf
```

A. A.

195. Which statement about OSPF area border routers is correct?

- A. ABRs sit between an autonomous system and OSPF.
- B. ABRs exchange Type 1 link-state advertisements between areas. 
- C. ABRs exchange Type 2 link-state advertisements between areas. 
- D. ABRs exchange Type 3 link-state advertisements between areas.

A. D, ABRs exchange Type 3 link-state advertisements (LSAs) containing summary information about networks on the other side of the area border router (ABR). These LSA announcements are called summary link advertisements, or SLAs. ABRs sit between areas within OSPF. 
- ABRs listen to Type 1 link-state advertisements but do not exchange
- ABRs listen to Type 2 link-state but do not exchange link-state advertisement messages.

196. B.

197. Which command will allow you to see the summary of OSPF link-
state advertisements?
```
A. Router#show ip ospf database 
B. Router#show ip ospf states
C. Router#show ip ospf neighbors 
D. Router#show ip ospf topology
```

A. A

198. D.

199. Two routers, called Router A and Router B, are configured in the same area and share a common LAN. However, they cannot form an adjacency. What could the problem be?
- A. There is a static route configured between the two routers. 
- B. Router A is configured with multiple area IDs.
- C. Router A is configured with a hello timer of 30.
- D. Router B is configured with a hello timer of 10.

A. C, if a router is configured with a hello timer of 30 seconds the hello/dead interval will not match. In order to form an adjacency, the hello/dead intervals must match. 

200. Which is a direct benefit of a hierarchical OSPF design? 
- A. Fast convergence
- B. Reduction of configuration complexity 
- C. Increased bandwidth
- D. Better security

A. A, Fast convergence of the the Link State Database (LSDB) that feeds the routing tables is a direct result of hierarchical OSPF design. The use of areas allows for routers within an area to converge and send summary link advertisements (LSAs) to other areas. 

201. B.
202. B.

203. You have configured a router with the following command. However, when you enter show ip routes you do not see any routes for OSPF. What is the problem?
```
    Router(config)#router ospf 255
    Router(config-router)#network 10.0.0.0 0.0.0.0 area 255
```
- A. The process ID is incorrect. 
- B. The area number is incorrect. 
- C. The subnet mask is incorrect. 
- D. The network ID is incorrect.

A. C.

204. A.

205. Which state in the neighbor table indicates that the router has successfully downloaded the LSA information from a neighboring router?
- A. FULL state
- B. EXSTART state 
- C. INIT state
- D. EXCHANGE state

A. A.

206. D.

207. You have two links that enter the same OSPF router with the same bandwidth. You want to prefer one route over the other yet allow the second as a backup route. Which command would you use to achieve this?
```
A. Router(config-router)#ip ospf priority 25
B. Router(config-if)#ip ospf route primary
C. Router(config-if)#ip ospf cost 25
D. Router(config-router)#passive interface gi 0/0
```

A. C.

208. D.
209. B.

210. Which command will display the DR for a LAN? 
- A. Router#show ip ospf neighbor
- B. Router#show ip ospf database
- C. Router#show ip ospf dr
- D. Router#show ip ospf interface

A. A. 

211. D. 
212. C. 

213. Which command will set the bandwidth of an interface to 2.048 Mb/s? 
```
A. Router(config-if)#bandwidth 2048
B. Router(config-if)#bandwidth 2048000000
C. Router(config-if)#bandwidth 2.048
D. Router(config-if)#bandwidth 2048000
```

A. A. 

214. Which command would you use to make sure Router A never becomes
a DR?

```
A. Router(config)#no ospf designated
B. Router(config-router)#no ospf designated
C. Router(config-router)#passive interface gi 0/0 
D. Router(config-if)#ip ospf priority 0
```

A. D, all routers have an OSPF priority of 1, if the priority is set to 0, the router will never become a designated router. 

215. Which command will configure a loopback interface with an address of 192.168.1.2/24?
```
A. Router(config)#interface loopback 0 
Router(config-if)#ip address 192.168.1.2/24

B. Router(config)#interface loopback 0 
Router(config-if)#ip address 192.168.1.2 255.255.255.0

C. Router(config)#interface loopback 
Router(config-if)#ip address 192.168.1.2/24

D. Router(config)#interface loopback 
Router(config-if)#ip address 192.168.1.2 255.255.255.0
```

A. B. 

216. Which is a correct statement about support for OSPF on an MPLS network?
- A. The provider edge (PE) routers can only host area 0.
- B. The customer edge (CE) routers can only host area 0.
- C. The customer edge (CE) routers must use GRE for OSPF.
- D. Both the customer edge (CE) routers and the provider edge (PE) routers can participate in area 0.

A. D.

217. What is the default priority for Open Shortest Path First (OSPF) routers?
- A. 1
- B. 100
- C. 255
- D. 32,768

A. OSPF priority for a router is a value of 1. This priority is used when electing a designated router (DR) and backup designated router (BDR). The higher the value, the higher chances of the router becoming a DR or BDR.


218. You have changed the router’s priority for OSPF to make the router the DR, but the router has not become a DR. What must be done to force the election?
- A. You must use the shutdown and no shutdown commands on the interface with the highest IP address.
- B. In global config mode, you must enter the command ospf election force.
- C. In privileged exec mode,  enter the command clear ip ospf process x.
- D. In privileged exec mode on the DR, you must enter the command clear ip ospf process x.

A. D.

219. Two routers, called Router A and Router B, are configured in the same area on Frame Relay. However, they cannot form an adjacency. What could the problem be?
- A. The two routers do not have the same hello timer of 30 seconds. 
- B. Router A is configured with multiple area IDs.
- C. Router A is configured with a hello timer of 10.
- D. Router B is configured with a hello timer of 10.

A. A.

220. What is the AD for OSPF? 
- A. 90
- B. 110 
- C. 120 
- D. 200

A. B, OSPF is 110.
- EIGRP is 90
- OSPF  is 110
- RIP   is 120
- BGP   is 200

221. Which protocol is an IEEE standard that is supported openly as a first hop redundancy protocol (FHRP)?
- A. Proxy ARP 
- B. VRRP
- C. GLBP
- D. HSRP

A. B, Virtual Router Redundancy Protocol (VRRP) is an IEEE open standard that is supported freely on many router products. HSRP is cisco proprietary

222. In the MAC address 0000.0c07.ac0a, what is the well-known Hot Standby Router Protocol (HSRP) ID?
- A. 0000.0c 
- B. oc07
- C. 0a
- D. 07.ac

A. D, the well know HSRP ID is 07.ac. Anytime 07.ac is in the second part of the MAC address along with the cisco oui, you can identify HSRP is being employed. 

223. Which protocol is a Cisco Proprietary protocol for load-balancing routers?
- A. Proxy ARP 
- B. VRRP
- C. GLBP
- D. HSRP

A. C, Gateway Load Balancing Protocol (GLBP) is a Cisco proprietary protocol that supports redundancy and per-subnet load balancing.

224. In the MAC address 0000.0c07.ac01, what is the HSRPv1 group number?
- A. 0000.0c 
- B. 0c07
- C. 01
- D. 07.ac

A. C. Last two digits are HSRP ID

225. What is the default priority of HSRP? 
- A. 100
- B. 110 
- C. 200 
- D. 10

A. 100

226. What is the maximum number of HSRPv1 groups that can be created? 
- A. 8
- B. 16 
- C. 255 
- D. 256

A. D, 0 to 255 = 256

227. Which port and protocol are used by HSRP for communications? 
- A. UDP/1935
- B. UDP/1985
- C. UDP/1895
- D. UCP/3222

A. B, HSRP routers communicate with each other on port 1985 using UDP.

228. Which statement is correct about HSRP?
- A. All routers in an HSRP group are active.
- B. Only one router in an HSRP group can be active.
- C. The virtual router sends hello packets to the HSRP group. 
- D. HSRP allows for per-packet load balancing.

A. B.

229. What type of communication is used between HSRP members?
- A. Unicast
- B. Broadcast
- C. Multicast
- D. Layer 2 flooding

A. C, HSRP uses multicasting to communicate among HSRP group members. For HSRPv1 the address is 224.0.0.2, for HSRPv2 the address is 224.0.0.102.

230. When a host sends an outgoing packet to an HSRP group, which router provides the destination address for the default gateway?
- A. Virtual router 
- B. Active router 
- C. Standby router 
- D. Monitor router

A. A, the virtual router is responsible for host communications such as an arp request for the hosts default gateway. 

231. Which timer must expire for a standby router in an HSRP group to become the active router?
- A. Hello timer 
- B. Standby timer 
- C. Hold timer
- D. Virtual timer

A. C, the hold timer must expire for the standby router to become an active router. The hold timer is 3 times the hello timer, so three hello packets myst be missed before the standby router becomes active.


232. Which port and protocol are used by Gateway Load Balancing Protocol (GLBP) for communications?
- A. UDP/1935
- B. UDP/1985 
- C. UDP/1895 
- D. UDP/3222

A. D, UDP port 3222

233. Which is a difference between HSRPv1 and HSRPv2?
- A. HSRPv2 does not use hello packets.
- B. HSRPv1 uses broadcasts, and HSRPv2 uses multicasts. 
- C. HSRPv1 supports IPv6.
- D. HSRPv2 uses milliseconds.

A. D, HSRPv2 allows for timers to be configured in milliseconds in lieu of seconds. This allows for quicker failover between active and standby routers.

234. Which statement is correct about GLBP?
- A. The active router is responsible for responding to clients with the virtual router’s MAC address.
- B. The active virtual gateway will respond with a MAC address of the active router.
- C. The active virtual gateway will respond with a MAC address of an active virtual forwarder.
- D. The virtual router is responsible for responding to tracking requests.

A. C, the active virtual gateway (AVG) is responsible for responding to ARP requests from hosts. The AVG will reply with the MAC address of any one of the active virtual forwarder (AVFs)

235. Which router is elected to become the GLBP active virtual gateway?
- A. The router with the lowest priority
- B. The router with the highest priority
- C. The router with the lowest priority and lowest IP address
- D. The router with the highest priority and highest IP address

A. D. 
