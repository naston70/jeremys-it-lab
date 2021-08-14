## Inter VLAN Routing

## Exam Topics
* Configure and verify IPv4 addressing and subnetting
* Configure and verify interswitch connectivity

Concepts:

Inter-VLAN communications cannot occur without a layer 4 device. Three options are available while implementing inter-vlan routing.

- Traditional or legacy inter-VLAN routing 
- Router on a Stick
- Multilayer switching 

## Legacy Inter-VLAN Routing 

Legacy Inter-VLAN routing requires multiple physical interfaces on both the router and the switch. When using a router to facilitate inter-VLAN routing, the router interfaces can be connected to seperate VLANs. Devices on those VLANs send traffic through the router to reach other VLANs. 

#### Router on a Stick

Today router software makes it possible to configure one router interface as multiple trunks by using subinterfaces. 

A physical interface can be logically subdivided into two logical interfaces. The one switch is configured to trunk multiple VLANs and each subinterface on the router is assigned a seperate VLAN. The router performs inter-VLAN routing by accepting VLAN-tagged traffic on the trunk interface coming from the adjacent switch. The router then forwards the routed traffic, VLAN-tagged for the destination VLAN, out the same physical interface that it used to receive the traffic. 

#### Multilayer Switching 

 Router on a stick works fine in a small business with one or two routers. But for the most scalable solution in enterprise networks today is to use a multilayer switch to replace both the router and switch. A Multilayer Layer switch performs both functions; switching traffic within the same VLAN and routing traffic between VLANs

 Multilayer switching is more scalable than any other routing implementation for two main reasons:
 
 - Routers have a limited number of available interface to connect to networks
 - Limited amounts of traffic can be accommodated on the physical line at one time 

With a multilayer switch, packets are forwarded down a single trunk line to obtain new VLAN tagging information. A multilayer switch does not completely replace the functionality of a router but can be thought of as a layer 2 device that is upgraded to have some routing capabilities. 

## Router on a Stick Configuration and Verification


