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