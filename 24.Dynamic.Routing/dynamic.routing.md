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
