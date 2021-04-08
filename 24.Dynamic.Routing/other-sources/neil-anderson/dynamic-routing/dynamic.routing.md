## Dynamic Routing Protocols

* When a routing protocol is used, routers automatically advertise their best paths to known networks, to each other
* Routers use this information to determine their own best path to the known destinations
* When the state of the network changes, such as a link going down or a new subnet being added, the routers update each other
* Routers will automatically calculate a new best path and update the routing table if the network changes

#### Summary Routes
- Summary routes lead to less memory usage in routers as the table contains less routes
- Less CPU as changes in the network only affect routers in the same area

#### Dynamic Routing Protocols vs Static Routes

* Routing protocols are more scalable than administrator defined static routes
* Using only static routes is only feasible in a small environment

#### Advantages of Dynamic Routing Protocols 
- The routers automatically advertise available subnets to each other without the administrator having to manually enter every route on every router
- If a subnet is added or removed the routers will automatically discover that and update their routing tables
- If the best path to a subnet goes down routers automatically discover that and will calculate a new best path

* Using a combination of both methods is very common in real world applications
* The routing protocol does most of the work, with a few static routes as needed - eg backup routes

## Routing Protocol Types

Routing protocols can split into two main types:
    - IGPs
    - EGPs

IGP for routing within an organisation
EGP for routing over the Internet -  the only BGP in use today is BGP

IGPs can be split into two main types: Distance Vector and Link State

*Distance Vector*
- In Distance Vector protocols each router sends its directly connected neighbors a list of all its known networks along with its own distance to each of those networks.
- Distance vector routing protocols do not advertise the entire network topology
- A router only knows its directly connected neighbors and the lists of networks those neighbors have advertised. It doesn't have detailed topology information beyond its directly connected neighbors.
- AKA routing by rumor


*Link State*
* Link State routing protocols have a router describe itself and its interfaces to its directly connected neighbors
* This information is passed unchanged from one router to another
* Every router learns the full picture of the network including every router, its interfaces and what they can connect to

## Routing Protocol Metrics

- A router can receive multiple possible paths to get to a destination
- Only the best path will go into the routing table to be used
- The different IGPs use different methods to calculate the best path to a destination network

#### Metric
* Each possible path will be assigned a 'metric' value by the routing protocol which indicates how preferred the path is
* The lowest metric value is preferred
* Distance Vector routers advertise to each other the networks they know about, and their metric to get to each of them
* Link State routers advertise all the links in their are of the network to each other
* Each router will take this information and then make an independent calculation of its own best path to get to each destination
* If the best path to a destination is lost (ie a link goes down) it will be removed from the routing table and replaced with the next best route

#### RIP Metric - Hop Count

- RIP uses Hop Count as the metric
- Max hop count is 15, anything over is deemed unreachable
- Doesn't consider link speed
- RIP is typically used only in test or small environments

#### OSPF Metric - Cost
* OSPF uses 'Cost' as the metric, which is automatically derived from interface bandwidth
* It is possible to manually configure the cost of links if required

#### IS-IS Metric - Cost
- IS-IS also uses 'Cost' as the metric, but is not automatically derived from interface bandwidth. All links have an equal cost by default
- You can manually configure the cost of links to manipulate the path
- If the link costs are not set manually, then the path with the lowest hop count will be used

#### EIGRP Metric 
* EIGRP uses the bandwidth and delay of links to calculate the metric
* Also load and reliability can be configured
* A fixed delay value is used based on the interface bandwidth, the protocol does not dynamically measure current delay
* The delay can be fixed manually if wanting to manipulate the path

#### Choosing a Routing Protocol
- RIP uses hop count and has a default max metric of 15. Not usually used in production due to scalability limitations
- EIGRP is simple to maintain, calculates changes quickly and its metric calculation will normally choose the best path by default. Typically only supported on Cisco
- OSPF's metric calculation will typically choose the best path by default. It is an open standard, support by all vendors and most commonly used IGP. More complicated to maintain than EIGRP
- IS-IS links need to be manually configured or it will use hop count to determine best path. Typically used in Service Provider networks or large organizations with their own MPLS network who choose it for scalability


## Equal Cost Multi Path - ECMP

- If multiple paths to a destination have an equal metric, the router will enter all of the paths into the routing table
- ECMP will load balance the outbound traffic to the destination over different paths
- All IGP routing protocols will perform ECMP by default
- EIGRP is the only routing protocol which is capable of UnEqual Cost Multi Path but must be configured manually

You can achieve load balancing with static routes.

The same flow will stay on one path.

## Administrative Distance

* A router will typically only learn routes to a particular destination from a single routing protocol
* When multiple routes to a destination are learned through a routing protocol the router will install the path with the best metric to the routing table
* Different routing protocols use different methods to calculate metric 

If paths to the same destination are received from different routing protocols, their metrics cannot be compared. A RIP hop count of 5 cannot be compared to an OSPF cost of 60. **The router must use a different method to choose when routes to the same destination are received from different routing protocols.** This is what administrative distance is used for.

The Administrative Distance is a measure of how trusted the routing protocol is, if routes to the same destination are received from different routing protocols, the protocol with the best (lowest) AD wins.

**AD VALUES:**

| Route Source | AD Value |
|--------------|----------|
| Connected Int| 0        |
| Static       | 1        |
| BGP          | 20       |
| EIGRP        | 90       |
| OSPF         | 110      |
| IS-IS        | 115      |
| RIP          | 120      |

- AD is used to choose between multiple path learned via different routing protocols
- Metric is used to choose between multiple paths learned by the same protocol
- The AD is considered first to narrow the choice to the best protocol
- The metric is then considered to choose the best paths to make it into the routing table

#### Floating Static Routes

* If the best path to a destination is lost (ie a link goes down) it will be removed from the routing table and replaced with the next best path
* It can be desirable to configure a static route as a backup for the route learned via the routing protocol
* Problem being that static routes have an AD of 1 so will be preferred over an IGP route
* To combat this it is possible to change the AD of a static route to make it act as a backup route
* This is a floating static route:
```
#ip route 10.0.0.0 255.255.255.0 10.0.0.1 115
```
At the end of the command the AD is set to 115, which is higher than an OSPF learned route AD.
Floating static routes can also be used to backup a normal static route:
```
#ip route 10.0.0.0 255.255.255.0 10.0.0.2 5
```
The AD is set to 5, above the static route AD of 1

If other routers exist along the path set as a backup care should be taken to avoid sending traffic down a path where other routers could possibly be down

## LoopBack Interfaces

- Loopback interfaces are logical interfaces
- They allow you to assign an IP address to a router or L3 switch, which is not tied to a physical interface
- As they don't have any physical attributes which can fail, loopback interfaces never go down
- Loopback addresses are logical so they cannot be physically in the same subnet as other device so they are usually assigned a /32 subnet mask to avoid wasting IP addresses

* It is best practice to assign a loopback to all routers
* The loopback is commonly used for traffic terminating at the router itself, such as management traffic, VOIP, BGP peering etc
* This provides redundancy if there are multiple paths to the router
* The loopback is also used to identify the router in OSPF - The Router ID

- The same loopback interface is usually used for multiple tasks
- Multiple loopbacks can be configured but is not common and only usually done where another seperate loopback is required for a special use case

#### Adjacencies

* IGP routing protocols are configured under global config mode and then enabled on individual interfaces
* When the routing protocol is enabled on an interface the router will look for other devices on the link which are also running the routing protocol
* The router does this by sending out and listening for hello packets
* When a matching peer is found, the routers form an adjacency with each other
* They then can exchange routing information
* Modern routing protocols use multicast for hello packets
* This is more efficient than broadcast which was used by earlier protocols
* Only routers running the same protocol will process the packet

#### Passive Interfaces
Passive interfaces allow for an IP subnet to be included in the routing protocol without sending updates out of the interface. Other devices can learn routes to it but no internal network information will be sent.

- It is best practice to configure loopback interfaces as passive interfaces
- It is impossible to form an adjacency on a loopback interface because they are not physical interfaces
- Making the loopback passive means that it will be advertised by the routing protocol but wont waste resources by sending and listening for hello packets

**Passive interfaces are used on:**
    * Loopback interfaces
    * Physical interfaces where the device on the other side belongs to another organisation and not routing information should be sent




































