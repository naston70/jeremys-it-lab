## Interior Routing Protocols

#### RIP

Type			 : Distance Vector
Algo			 : Bellman-Ford
AD   			 : 120
Multicast Address: 224.0.0.9

**RIP Implementations:**

RIPv1 - Original, limited to classful routing, now obsolete

RIPv2 - Introduced for classless routing, triggered updates and multicast

RIPng - Supports IPv6, functions similarly to v2 

**Terminology:**
*Split Horizon:* Mitigates routing loops by ensuring a route is never advertised back to the neighbor from which it was learned.

*Poison Reverse:* Learned routes are advertised back to their originator as explicitly invalid

**RIP CONFIG**
```
-----------------------------------------

## Enable ripv2

router rip
 version 2
-----------------------------------------

## Disable RIPv2 auto-summary

no auto-summary
-----------------------------------------

## Designate RIPv2 interfaces by network

network [ipv4-network]
-----------------------------------------

## Originate a default routes

default-information originate
-----------------------------------------

## Designate passive interfaces

passive-interface { [interface] | default }
-----------------------------------------

## Modify equal-cost load balancing

maximum-paths [1-16]
-----------------------------------------

## TROUBLESHOOTING

show ip[v6] protocols
show ip[v6] rip database
debug ip rip {database|events}
debug ipv6 rip [interface]
```



#### EIGRP

Type			 : Distance Vector
Algo			 : DUAL
AD  			 : 90
Multicast Address: 224.0.0.10

#### OSPF

Type			 : Link-State
Algo			 : Dijkstra
AD      		 : 110
Multicast Address: 224.0.0.5-6

#### IS-IS

Type			 : Link-State
Algo			 : Dijkstra
AD      		 : 115
Multicast Address: N/A 

#### BGP

Type			 : Path Vector
Algo			 : Path selection
AD      		 : 20
Multicast Address: 224.0.0.9++