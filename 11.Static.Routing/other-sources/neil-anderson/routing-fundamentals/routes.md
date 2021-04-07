## Routing Fundamentals

A router has two main functions:
    - Determine the best path to available networks
    - Forwarding traffic to those networks

Find and Forward

The best available path or paths to a destination network are listed in a routers routing table and will be used for forwarding traffic

A routing table consists of directly connected networks and routes configured statically by either the admin or dynamically learned through a routing protocol

IP addresses configured on a routers interface are automatically entered as connected routers in the routing table

```
interface fa0/0
ip address 10.0.0.1 255.255.255.0
```
Routing table:
```
#show ip route
C        10.0.0.0/24 is directly connected, FastEthernet0/0
```

Meaning if any traffic for th 10.0.0.0/24 network is received on any other interface, it will be sent out of fa0/0

Local routes are also added to the routing table since IOS15
Local routes have a /32 mask and show the IP address configured on the actual interface

## Static Routes

If a router receives traffic for a network which it is not directly attached to, it needs to know how to get there in order to forward the traffic

An administrator can manually add a static route to the destination or the router can learn it via a routing protocol

## Summarisation and Default Routes

example output of routes:
```
ip route 10.1.0.0 255.255.255.0 10.0.0.2
ip route 10.1.1.0 255.255.255.0 10.0.0.2
ip route 10.1.2.0 255.255.255.0 10.0.0.2
```

For static routing, summary routes lessen administrative overheard (less routes to manage) and memory usage on the routers

The above can be summarised to:
```
ip route 10.1.0.0 255.255.0.0 10.0.0.2
```

Matching on the last 2 octets.
However, summarisations don't have to be on classful boundaries. A tighter match for the example routes would be from 10.1.0.0 to 10.1.3.0

```
ip route 10.1.0.0 255.255.252.0 10.0.0.2
```

When there are overlapping routes, the longest prefix will be selected.
```
ip route 10.1.0.0 255.255.0.0 10.0.0.2
ip route 10.1.3.0 255.255.255.0 10.0.3.2
```

#### Load Balancing
When multiple equal length routes are added for the same destination the router will add them all to the routing table and load balance between them.
```
ip route 10.1.0.0 255.255.0.0 10.0.0.2
ip route 10.1.0.0 255.255.0.0 10.0.3.2
```

The router will send packets via both routes.

#### Default Route - (Gateway of Last Resort)

To add a route to reach anywhere else, not connected or not configured we use a default route. For example, one router connected to the internet:
```
ip route 0.0.0.0 0.0.0.0 [next-hop-ip]
```












