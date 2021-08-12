## Basic Routing Concepts

Exam Topics:

- Explain the role and function of network components
- Determine how a router makes a forwarding decision by default

#### Packet Forwarding

Packet forwarding by routers is accomplished through path determination and switching functions. The path determination function is the process the router uses to determine which path to use when forwarding a packet. To determine the best path, the router searches its routing table for a network address that matches the packets destination IP address.

This search results in one of three path determinations:

- **Directly connected network:** If the destination IP address of the packet belongs to a device on a network that is directly connected to one of the routers interfaces, the packet is forwarded directly to that device. This means the destination IP address of the packet is a host address on the same network as this routers interface
- **Remote network:** If the destination IP address of the packet belongs to a remote network, the packet is forwarded to another router. Remote networks can be reached only by forwarding packets to another router. 
- **No route determined:** If the destination IP address of the packet does not belong to a connected or remote network and the router does not have a default route, the packet is discarded. The router sends an ICMP Unreachable messages  to the source IP of the packet.

In the first two result, the router completes the process by switching the packet out the correct interface. It does this by reencapsulating the IP packet into the appropriate Layer 2 data-link frame format for the exit interface. This type of interface determines the type of Layer 2 encapsulation. ie if the exit interface is Fast Ethernet, the packet is encapsulated in an Ethernet frame. If the exit interface is a serial interface configured for PPP, the IP packet is encapsulated in a PPP frame.

## Routing Methods

A router can learn routes from three basic sources:
- **Directly connected routes:** Automatically entered in the routing table when an interface is activated with an IP address
- **Static routes:** Manually configured by the network administrator and entered in the routing table if the exit interface for the static route is active
- **Dynamic routes:** Learned by the routers through sharing routes with other routers that use the same routing protocol

In many cases, the complexity of the network topology, the number of networks, and the need for the network to automatically adjust to changes require the use of a dynamic routing protocol. Dynamic routing certainly has several advantages over static routing; however, networks still use static routing. In fact, networks typically use a combination of static and dynamic routing. 

| Parameter       | Description                                                   |
|-----------------|---------------------------------------------------------------|
| static          | enable aging for statically configured secure addresses       |
| time            | Specify again. 0-1440 mins. 0 = disabled                      |
| type absolute   | Set absolute aging time. All address age out after set time   |
| type inactivity | Set inactivity aging time. Address age out if no data in time |


## Classifying Dynamic Routing Protocols

Routing Protocols are classified into different groups according to their characteristics: 
* IGP or EGP
* Distance vector or link state 
* Classful or classless 

#### IGP and EGP

An autonomous system (AS) is a collection of routers under a common administration that presents a common, clearly defined routing policy to the internet. Typical examples are a large companies internal network and an ISPs network. Most company networks are not autonomous systems; in most cases, a company network is a network within its ISPs autonomous system. Because the Internet is based on the AS concept, two types of routing protocols are required

- IGP: Used for intra-AS routing, routing inside an AS concept
- EGP: Used for inter-AS routing, routing between AS's

#### Distance Vector Routing Protocols

*Distance Vector* means that routes are advertised as vectors of distance an direction. Distance is defined in terms of a metric such as hop count and direction is the next-hop router or exit interface. Distance vector protocols typically uses the Bellman-Ford algorithm for the best-path route determination.

Some distance vector protocols periodically send complete routing tables to all connected neighbors. In large networks, these routing updates can become enormous, causing significant traffic on the links. 

Although the Bellman-Ford algorithm eventually accumulates enough knowledge to maintain a database of reachable networks, the algorithm does not allow a router to know the exact topology of an internetwork. The router knows only the routing information received from its neighbors.

Distance vector protocols use routers as signposts along the path tho the final destination. The only information a router knows about a remote network is the distance or metric to reach that network and which path or interface to use to get there. A distance vector routing protocol does not have a map of the network topology. 

Distance protocols work best in these situations:

* When the network is simple and flat and does not require hierarchical design
* When the administrator does not have enough knowledge to configure and troubleshoot link-state protocols
* When specific types of networks, such as hub-and-spoke networks, are being implemented
* When worst-case convergence times in a network are not a concern

#### Link-State Routing Protocols

In contrast to distance vector routing protocol operation, a router configured with a link-state routing protocol can create a complete view, or topology, of the network by gathering information from all the other routers. A link-state routing protocol is a complete map of the network topology. The signposts along the way from source to destination are not necessary because all link-state routers are using an identical map of the network. A link-state router uses the link-state information to create a topology map and to select the best path to each destination network in the topology. 

With some distance vector routing protocols, routers periodically send updates of their routing information to their neighbors. Link-State routing protocols do not use periodic updates. After the network has converged, a link-state update s sent only when the topology changes.

Link-State protocols work best in these situations:

* When the network design is hierarchical, which is typically in large networks
* When the administrators have good knowledge of the implemented link-state routing protocol
* When fast convergence of the network is crucial

#### Classful Routing Protocols 

Classful routing protocols do not send subnet mask information in routing updates. The first routing protocols, such as RIP, were classful. When those protocols were created, network addresses were allocated based on class, A,B,C.
A routing protocol did not need to include the subnet mask in the routing update because the network mask could be determined based on the first octet of the network address. 

Classful routing protocols can still be used in some of today's networks, but because they do not include the subnet mask, they cannot be used in all situations. Classful routing protocols cannot be used when a network is subnetted using more than one subnet mask. In other words, classful routing protocols do not support VLSM

Other limitations come into play with classful routing protocols, including their inability to support discontiguous networks and supernets. Classful routing protocols include RIPv1 and IGRP (Not in CCNA)

#### 
Classless Routing Protocols include the subnet mask with the network address in routing updates. today's networks are no longer allocated based on class, and the subnet mask cannot be determined by the value of the first octet. Classless routing protocols are required in most networks today because of their support for VLSM and discontiguous networks and supernets. Classless routing protocols include RIPv2, EIGRP, OSPF, IS-IS and BGP 

## Dynamic Routing Metrics 

In some cases, a routing protocol learns of more than one route to the same destination from the same routing source. To select the best path, the routing protocol must be capable of evaluating and differentiating among the available paths. A metric is used for this purpose. Two different routing protocols might choose different paths to the same destination because they use different metrics. Metrics used in IP routing protocols include the following:

* **RIP - hop count:** The best path is chosen by the route with the lowest hop count
* **IGRP and EIGRP - Bandwidth, delay, reliability and load:** The best path is chosen by the route with the smallest composite metric value calculated from these multiple parameters. By default, only bandwidth and delay are used.
* **IS-IS and OSPF - Cost:** The best path is chosen by the route with the lowest cost. The cisco implementation of OSPF uses bandwidth to determine the cost 

The metric associated with a certain route can be best viewed using the **show ip route** command. The metric value is the second value is the second value in the brackets for a routing table entry. 

## Administrative Distance 





