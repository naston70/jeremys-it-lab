# Dynamic Routing

Dynamic routes are routes learned by using dynamic routing protocols. 
Routing protocols are configured on routers for the purpose of exchanging router information.

* A network gains from the fact you do not need to manually configure every route on every router in a network and if links fail, routers can advertise some routes have failed and select a new path to that network. 

* Costs more in CPU and bandwidth plus adds complexity to the network 

**Network route** eg 10.0.12.0/30 - A route to a network or subnet with a mask length less than < 32

**Host route** 10.0.12.1/32 - A route to a specific host with a /32 mask


- Routers can use dynamic routing protocols to advertise information about the routes they know to other routers
- They form adjacencies / neighbor relationships / neighborships with adjacent routers to exchange this information
- If multiple routes to a destination are learned, the router determines which route is superior and adds it to the routing table

#### Types of Dynamic Routing Protocols
* Dynamic routing protocols can be divided into two main categories:
	- IGP (Interior Gateway Protocol)
	- EGP (Exterior Gateway Protocol)

* IGP = used to share routes in a single autonomous system (AS), which is a single organization

* EGP = used to share routes between different autonomous systems

			Algorithm Type

IGP ---->	Distance Vector	1) -----> Routing Information Protocol (RIP)
	\						2) -----> Enhanced Interior Gateway Routing Protocol (EIGRP)
	 \	
	  \->	Link State		1) -----> Open Shortest Path First (OSPF)
	  						2) -----> Intermediate System to Intermediate System (IS-IS)	

BGP ---->	Path Vector  ----------> Border Gateway Protocol

The alogrithm type is in relation to the processes each algorithm uses to share routing information and choose the best route to each destination.

RIP & EIGRP = Distance Vector	OSPF & IS-IS = Link State	BGP = Path Vector

#### Distance Vector Protocols

* Distance Vector protocols were invented before link state protocols
* Early examples are RIPv1 and Cisco's proprietary IGRP (later updated to EIGRP)
* Distance vector protocols operate by sending the following to their directly connected neighbors:
	- their known destination networks
	- their metric to reach their known destinations
* This method of sharing route information is often called 'routing by rumor'
* This is because the router does not know about the network beyond its neighbors. It only knows the information that its neighbor tells it	
* This is different than Link State Protocols which develop a more complete picture of the network
* It is called 'Distance Vector' because the routers only learn the 'distance' (metric) and 'vector' (direction, next-hop router) of each route

#### Link State Protocols

- When using a link state routing protocol, every router creates a 'connectivity map' of the network
- To allow this, each router advertises information about its interfaces (connected networks) to its neighbors. These advertisements are passed along to other routers, until all routers in the network develop the same map of the network.
- Each router independently uses this map to calculate the best routes to each destination
- Link state protocols use more resources on the router as more information is used (CPU)
- Link state protocols tend to be faster in reacting to changes in the network that Distance Vector protocols


#### Dynamic Routing Protocol Metrics

* A routers route table contains the best route to each destination network it knows about
* If a router using a dynamic routing protocol learns two different routes to the same destination, how does it determine which is 'best'?
* It uses the metric value of the routes to determine which is best. Lower metric = better route
* Each routing protocol uses a different metric to determine which route is best

**If a router learns two (or more) routes via the same routing protocol to the same destination (net address and subnet mask) with the same metric both will be added to the routing table. Traffic will be load balanced over both routes**
This is known as **ECMP** Equal Cost Multi-Path.

###### RIP
- Metric = Hop Count
- Explanation = Each router in the path counts as one 'hop'. The total metric is the total number of hops to the destination. **Links of all speeds are equal**

###### EIGRP
- Metric = Bandwidth & Delay
- Explanation = Complex formula that can take into account many values. By default the bandwidth of the **slowest link in the route** and the total delay of all links in the route are used

###### OSPF
- Metric = Cost
- Explanation = The cost of each link is calculated based on the bandwidth. The total metric is the total cost of each link in the route

###### IS-IS
- Metric = Cost
- Explanation = Total metric is the total cost of each link in the route. The cost of each link is not automatically calculated by default. All links have a cost of 10 by default


#### Administrative Distance

- In most cases a company will only use a single IGP - Usually OSPF or EIGRP
- However, in some rare cases they may use two. eg: two companies connect their networks to share information.
- Metric is used to compare routes learned via the same routing protocol
- Different routing protocols use different metric so the cannot be compared
- The **Administrative Distance** (AD) is used to determine which routing protocol is preferred
- A lower AD is preferred and indicates that the routing protocol is considered more 'trustworthy' in selecting the best routes


###### Administrative Distances:

| ROUTE PROTOCOL/TYPE | AD  |
|---------------------|-----|
|                     |     |
| Directly Connected  | 0   |
| Static              | 1   |
| External BGP        | 20  |
| EIGRP               | 90  |
| IGRP                | 100 |
| OSPF                | 110 |

| ROUTE PROTOCOL/TYPE | AD  |
|---------------------|-----|
| IS-IS               | 115 |
| RIP                 | 120 |
| EIGRP (external)    | 170 |
| Internal BGP (iBGP) | 200 |
| Unusable route      | 255 |

The AD and Metric can be found in the routing table:
```
#show ip route
...
...

O 		10.0.34.0/30 	[110/2] via 10.0.12.0
```

In the square brackets is the AD of 110 with a metric of 2 (OSPF in this case)

You can change the AD of a routing protocol to favour one over the other
You can also change the AD of a static route:

#### Floating Static Routes