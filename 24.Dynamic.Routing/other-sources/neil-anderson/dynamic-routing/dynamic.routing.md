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











