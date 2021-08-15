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

