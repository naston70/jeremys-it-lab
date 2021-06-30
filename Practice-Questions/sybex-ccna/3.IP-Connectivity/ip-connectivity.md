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
