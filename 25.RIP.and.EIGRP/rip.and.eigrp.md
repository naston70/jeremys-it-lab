# RIP and EIGRP

## RIP

- Routing Information Protocol
- Distance Vector IGP
- Uses hop count as its metric
- Max hop count is 15
- Has Three versions RIPv1, RIPv2 and RIPng (next gen)
- Uses two message types:
	+ **Request:** To ask RIP-enabled neigbors to send their routing table
	+ **Response:** To send the local routers routing table to neighbouring routers
- By default shares routing table every 30 secs

####RIPv1 vs RIPv2

######RIPv1:
	- only advertises classful addresses
	- doesn't support VLSM, CIDR
	- doesn't include subnet mask information in advertisements
	- messages broadcast to 255.255.255.255

######RIPv2:
	* supports VLSM, CIDR
	* includes subnet mask information in advertisements
	* messages are multicast to 224.0.0.9


## RIP Configuration
```
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#no auto-summary
R1(config-router)#network 10.0.0.0
R1(config-router)#network 172.16.0.0
```

- The RIP 'network' command is classful, it will automatically convert to classful networks
- Ie, if you enter ```network 10.0.12.0``` its will be converted to ```network 10.0.0.0``
- There is no need for a network mask

#### The network command

* The network command tells the router to:
	- look for interfaces with an IP address that is in the specified range
	- active RIP on the interface that fall in the range
	- form adjacencies with connected RIP neighbors
	- advertise the network prefix of the interface (not the prefix in the network command)

* The OSPF and EIGRP commands operate in the same way
* The network command doesn't tell the router which networks to advertise. It tells the router which interfaces to activate RIP on, and then the router will advertise the network prefix of those interfaces	
* If there are no RIP neighbors connected to an interface (end hosts for example), the router will continuously send RIP advertisements out of the interface. This is unnecessary traffic so these type of interfaces should be configured as a passive interface
* ```R1(config-router)#passive-interface interface```

**The ```default-information originate``` command**

`R1(config-router)#default-information originate`  use to share default route information via RIP


#### ```show ip protocols```

Gives information on routing protocols running


## EIGRP

- Was Cisco proprietary
- Considered advanced/ hybrid distance vector routing protocol
- Much faster than RIP in reacting to changes in the network
- Does not have the 15 'hop-count' limit of RIP
- Sends messages using multicast address 224.0.0.10
- Is the only IGP that can perform unequal-cost-load-balancing

#### eigrp configuration

```
R1(config)#router eigrp 1
R1(config-router)#no auto-summary
R1(config-router)#passive-interface g2/0
R1(config-router)#network 10.0.0.0
R1(config-router)#network 172.16.1.0 0.0.0.15
```

- The 1 in the first command is the AS number (Autonomous System). This must match between routers or they will not form an adjacency and share route information

- Auto-summary may be enabled on EIGRP so of enabled, ensure to disable

- The network command will assume a classful address if the mask is not specified (using wildcard masks)

#### Wildcard Masks

* Basically an inverted subnet mask
* All 1s in the subnet are 0 in the wildcard mask, all 0s in the subnet are 1s in the wildcard mask
* 0 in a wildcard mask means it must match
* 1 in a wildcard mask means doesn't have to match
 

## EIGRP METRIC

By default EIGRP uses bandwidth and delay to calculate the metric, the formula can be simplified by using the metric bandwidth + delay

Metric = Bandwidth of the slowest link + delay of all the links

**Terminology:** 
	- Feasible Distance = The routers metric value to the routes destination
	- Reported Distance = The neighbors metric value to the routes destination
	* Successor = the route with the lowest metric to the destination (the best route)
	* Feasible Successor =  an alternate route to the destination (but not the best) but meets the feasibility condition

What us the feasibility condition?
	
A route is considered a Feasible Successor if its reported distance is lower than the Successor routes Feasible Distance. This is a loop prevention mechanism

#### EIGRP Unequal Cost Load Balancing 
```
#show ip protocols
```
This will reveal the variance setting. If variance is set to 1 only ECMP (equal cost load balancing) will ever occur. WIth default settings eigrp wont perform unequal cost load balancing.

EIGRP will only perform unequal cost load balancing over feasible successor routes. If a route doesn't meet the feasibility condition, it will NEVER be selected for load balancing regardless of the variance.
