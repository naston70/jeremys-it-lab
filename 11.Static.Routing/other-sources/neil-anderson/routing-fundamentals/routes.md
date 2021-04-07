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









