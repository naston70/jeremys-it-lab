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



Excerpt From: Allan Johnson. “31 Days Before your CCNA Exam: A Day-By-Day Review Guide for the CCNA 200-301 Certification Exam”. Apple Books. 
