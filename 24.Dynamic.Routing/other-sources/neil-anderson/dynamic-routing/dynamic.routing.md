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










