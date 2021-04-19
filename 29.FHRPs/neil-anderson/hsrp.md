## HSRP 

Network redundancy, FHRP and HSRP.

#### Network Redundancy

- Common in small networks / office branches for there to be a single point of fail. The cost of adding redundant devices cannot be justified 
- The point of redundancy is to eliminate single points of failure
- Larger networks can justify the cost
- Internet should be reachable if any core/ distribution switch, router or link fails
- Typically there is no redundancy at the access layer and end hosts only have one network card
- Servers with redundant NICs are an exception

#### Redundancy at Layer 3

Add a static route to the SP router, A backup default static route via the second router if the link to SP1 goes down.
ie: ```ip route 0.0.0.0 0.0.0.0 ip_address 5``` this adds the backup route with a higher administrative distance of 5. Not for load balancing. 
A backup route to go downstream would also need to be added for the interface on the router still up.

## FHRP's - First Hop Redundancy Protocols

A FHRP is a protocol which is designed to protect the default gateway used on a subnetwork by allowing two or more routers to provide backup for that address. In the event of a failure of an active router, the backup router will take over the address, usually within seconds.

EG: HSRP (hot standby router protocol), VRRP (virtual routing redundancy protocol), GLBP (gateway load balancing protocol)


