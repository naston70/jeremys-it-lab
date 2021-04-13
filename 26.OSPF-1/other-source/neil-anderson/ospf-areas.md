## OSPF Areas

- Every router learns the full picture of its part of the network including every router, its interfaces and what its connected to 
- This can cause issues in large networks:
    * Too many routes can use up too much memory
    * Network changes cause all the routers to reconverge which takes time and CPU 
To combat this:
- OSPF supports a hierarchical design which segments large networks into smaller areas to solve this problem
- Each router maintains full information about its own area, but only summary information about other areas - less routes and changes don't affect 

A two level hierarchy is used: 
    - Transit area (backbone or area 0) - does not generally contain end users
    - Regular areas (nonbackbone areas) - Used to connect end users to the transit area. By default all transit traffic goes through the Transit area 
- Small networks do not require a hierarchical design and all routers can be in area 0

The area is configured at the interface level with the network command, for a router to form an adjacency, its neighbor must be configured to be in the same area.
```
#network 10.0.0.0 0.0.255.255 area 0
```

#### Backbone routers
- Routers which have all their interfaces in area 0 are backbone routers
- Routers maintain a full LSDB of other routers and links in their own area

#### ABRs -  Area Border Routers
- Routers which have interfaces in multiple areas are ABRs

An ABR has the following characteristics:
* It seperates LSA flooding zones
* It becomes the primary point for area address summarization
* It functions regularly as the source for default routes
* It maintains the LSDB for each area with which it is connected

Ideal design is to have each ABR connected to two areas only, the backbone and another area, with three being the limit.

* ABRs do not automatically summarize
* If summarization is not configured, all routes are flooded everywhere
To get the benefit of the summarization need to configure the range command:
```
area 0 range 10.1.0.0 255.255.0.0
```

The effect being the router has a single summary route and therefore less routes and resources used.
Also if the link goes down the summary route means the effect is only felt in that one area - this is another reason for multi areas when using large networks.

IA - inter area routes, a route learned from an ABR 

#### Normal Area Routers


