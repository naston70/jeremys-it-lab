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
- 
