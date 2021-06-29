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
