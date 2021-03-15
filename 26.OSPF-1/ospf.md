# OSPF

Link State routing protocol.

* When using a link state routing protocol, every router creates a connectivity map of the network
* To allow this each router advertises information about its interfaces (connected networks) to it neighbours. These advertisements are passed along to other routers, until all routers in the network develop the same map 
* Then each router independently uses this map to calculate the best routes to each destination
* Link state protocols use more resources (CPU) on the router as more information is shared
* However, link state protocols tend to be faster in reacting to changes in the network than distance vector protocols

#### Open Shortest Path First

- Uses the Shortest Path First algorithm
- Three Versions:
	+ OSPFv1 (not used anymore)
	+ OSPFv2 (used for IPv4)
	+ OSPFv3 (used for IPv6, but can be used for IPv4)

- Routers store information about the network in LSAs (link state advertisements), which are organized in a structure called the LSDB (link state database)
- Router will flood LSAs until all routers in the OSPF area develop the same map of the network. (same LSDB)

**LSA Flooding**: 
	* OSPF is enabled on an interface
	* The router creates an LSA to tell its neighbors about the network on the interface
	* The LSA is flooded throughout the network until all routers have received it.
	* This results in all routers sharing the same LSDB
	* Each router then uses the SPF algorithm to calculate its best route to the new network

#### OSPF Steps

* In OSPF there are three main steps in the process of sharing LSAa and determining the best route to each destination in the network

1) **Become Neighbors** with other routers connected to the same segment
2) **Exchange LSAs** with neighbor routers
3) **Calculate the best routes** to each destination, and insert them into the routing table

#### OSPF Areas

- OSPF uses areas to divide up the network
- Small networks can be single area without any negative effects on performance
- In larger networks, a single area design can have negative effects:
	* the SPF algo takes more time to calculate routes
	* the SPF algo requires exponentially more processing power on the routers
	* the larger LSDB takes up more memory on the routers
	* any small change in the network causes every router to flood LSAs and run the SPF algorithm again
- Dividing a large OSPF network into several smaller areas, these problems can be avoided

What is an area?

- An area is a set of routers and links that share the same LSDB
- The **backbone area** (area 0) is an area that all other areas must connect to
- Routers with all interfaces in the same area are called **internal routers**
- Routers with interfaces in multiple areas are called **area border routers (ABRs)**
- Routers connected to the backbone area (area 0) are called **backbone routers**
- An **intra-area route** is a route to a destination inside the same OSPF area
- An **interarea route** is a route to a destination in a different OSPF area

**ABRs maintain a seperate LSDB for each area they are connected to. It is recommended that you connect an ABR to a maximum of 2 areas. Connecting to an ABR to 3+ areas can overburden the router**

- OSPF areas should be contiguous
- All OSPF areas must have at least one ABR connected to the backbone area 
- OSPF interfaces in the same subnet must be in the same area

#### Basic OSPF Configuration
```
R1(config)#router ospf 1
R1(config)#network 10.0.12.0 0.0.0.3 area 0
```

* The OSPF process ID is locally significant. Routers with different process IDs can become OSPF neighbors
* The OSFP ```network``` command requires you to specify the ```area```
* The ```network``` command tells OSPF to:
	- look for any interfaces with an IP address contained in the range specified in the ```network``` command
	- activate OSPF on the interface in the specified area
	- the router will then try to become OSPF neighbors with other OSPF-activated neighbor routers

#### The ```passive-interface``` command
```
R1(config-router)#passive interface g2/0
```
- The passive-interface command tells the router to stop sending OSPF 'hello' messages out of the interface
- However, the router will continue to send LSAs informing its neighbors about the subnet configured on the interface
- This command should always be used on interfaces which don't have any OSPF neighbors

#### Advertise a default route into OSPF
```
R1(config)#ip route 0.0.0.0 0.0.0.0 net-hop
R1(config-router)#default-information originate

```




