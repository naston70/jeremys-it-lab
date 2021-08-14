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
