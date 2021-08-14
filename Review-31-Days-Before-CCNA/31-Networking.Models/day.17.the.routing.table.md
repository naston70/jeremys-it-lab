## The Routing Table

#### Exam Topics
- Interpret the components of routing table
- Determine how a router makes a forwarding decision by default 

###### Key Topics
- Path determination
- Packet forwarding 

## Two Router Functions

When a router receives an IP packet on one interface, it determines which interface to use to forward the packet to the destination. The primary functions of a router are to:
- Determine the best path for forwarding packets, based on information in its routing table 
- Forward packets toward their destinations

#### Longest Match Determines Best Path

The best path in the routing table is also known as the longest match. The router uses the longest match process to fins a match between the destination IP address of the packet and a routing entry in the routing table. The prefix length of the route in the routing table us used to determine the minimum number of far-left bits that must match. The longest match is the route in the routing table that has the greatest number of far left bits matching the destination IP address of the packet. The route with the greatest number of equivalent far-left bit, or the longest match is always the preferred route.

#### Three Packet Forwarding Decisions

After a router has determined the best path based on the longest match in the routing table, it can do 1 of three things:
* Forward the packet to a device on a directly connected network
* Forward the packet to a next-hop router
* Drop the packet because there is no match in the routing table

The primary responsibility of the packet forwarding function is to encapsulate packets in the appropriate data link frame type for the outgoing interface. The

#### Components of a Routing Table

A router examines the destination IP address of a packet and searches its routing table to determine where to forward the packet. The routing table contains a list of all known network addresses and where to forward the packet. These entries are known as route entries or routes. The router forwards a packet using the best matching route entry. 

A routing table stores 3 types of routes:
* **Directly connected networks**: These network entries are active router interfaces
* **Remote networks**: These networks are connected to other routers.
* **Default route**: Used when there is no better match in the IP routing table. 

#### Routing Table Entries

At the beginning of each routing table entry is a code that is used to identify the type of route or how the route was learned. Common route sources include:
- L: directly connected local interfaces
- C: directly connected network 
- S: Static route manually configured 
- O: OSPF 
- D: EIGRP 

#### Routing Principles and Examples

* Every router makes its decision alone, based on information it has in its own routing table. A router can only forward packets using its own routing table. A router does not know what routes are in the routing tables of other routers.

* The information in the routing table of one router does not necessarily match the information in the routing table of another router. Just because a router has routed in its routing table to a network on the Internet through another router does not mean that router knows about that same network. 

* Routing information about a path does not provide provide return routing information - A router receives a packet with a destination IP and a source IP. Just because the router knows to forward the packet out a particular interface, does not mean that it knows how to forward packets back the other way 

#### Route Entry Structure


