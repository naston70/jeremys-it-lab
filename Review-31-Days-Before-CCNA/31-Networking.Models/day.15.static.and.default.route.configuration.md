## Static and Default Route Configuration

#### Exam Topics

- Configure and verify IPv4 and IPv6 static routing

#### Static and Default Routing Overview

When a router configured with a dynamic routing protocol can learn routes from other routers without additional input from the network administration, what use is there for static routing?
There can be various situations but in general, static routing is used in these cases:
* In a small network that requires only simple routing
* In a hub and spoke network topology
* When you want to create a quick ad hoc route
* As a backup when the primary route fails

In general static routes are not used:
* In a large network
* When the network is expected to scale

Static routes are commonly used when you are routing from a larger network to a stub network. Static routes can also be useful for specifying a default route or gateway of last resort. 

#### IPv4 Static Route Configuration

To configure a static route, use the ```ip route``` command with the following relevant syntax. 
```
Router(config)# ip route [network-address][subnet-mask]{ip|exit-interface}[AD]
```

- **network-address**: The destination of the remote network to be added to the routing table
- **subnet-mask**: The subnet mask of the remote network to be added to the routing table. Static

One or both of the following parameters are used:

-**ip address/ next-hop**: next routers IP address 
-**exit-interface**: the outgoing interface used in forwarding packets to the destination network.

In addition the optional AD parameter is used when configuring a floating static route. 

#### IPv4 Static Routes Using the Next Hop Parameter 

Using the next-hop parameter example:
R1 does not know about these remote networks:
*172.16.1.0/24: The LAN on R2
*192.168.0.0/24: The serial network between R2 and R3
*192.168.1.0/24: The LAN on R3
*10.10.10.0/24: The serial network between R2 and HQ
*0.0.0.0/0: All other networks accessible through HQ

The router can be configured with three static routes, one for each network it does not yet know about.

The interface that routes to the next hop must be up/up before static routes can be entered in the routing table.

When using the next-hop parameter, the router must have a route in the table to the network that the next-hop address belongs to.
Configuring a next-hop address requires the router to perform a recursive lookup to find the exit interface before it can send the packet out the interface.

#### IPv4 Static Routes using the Exit Interface Parameter

To avoid a recursive lookup and have a router immediately send packet to the exit interface, configure the static route using the exit-interface parameter instead of the ip-address next-hop parameter.

Any previous static routes to this network should be removed

#### IPv4 Default Route Configuration 

A default route is a special kind of static route used to represent all routes with 0 or no bits matching. When no routes have a more specific match in the routing table, the default is a match.

The destination IP address of a packet can match multiple routes in the routing table.
```
     172.16.0.0/24 is subnetted, 3 subnets
S    172.16.1.0 is directly connected, Serial0/0/0
S    172.16.0.0/16 is directly connected, Serial0/0/1”
```

A packet destined for 172.16.1.10, the packets destination IP address, matches both routes. However, the 172.16.1.0 route is the more specific route because the destination matches the first 24 bits, whereas the destination matches only the first 16 bits of the 172.16.0.0 route. Therefore the router uses the route with the most specific match.

A default route is a route that matches all packets. Commonly called a quad-zero route, a default route uses 0.0.0.0 for both the network address and subnet mask.