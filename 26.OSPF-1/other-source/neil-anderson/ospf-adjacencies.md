## OSPF Packet Types

- **Hello:** A router will send out and listen for Hello packets when OSPF is enabled on an interface and form adjacencies with other OSPF routers on the link 
- DBD Database Description: Adjacent routers will tell each other the networks they know about with the DBD packet
- LSR Link State Request: If a router is missing information about any of the networks in the received DBD, it will send the neighbor an LSR

#### Hello Packets:

* OSPF routers discover each other and form adjacencies via Hello packets
* They send Hello packets out each interface where OSPF is enabled (except passive interfaces)
* Multicast to 224.0.0.5 - 'all ospf routers'
* Sent every 10 seconds by default

###### Hello Packet Contents
- Router ID: 32 bit number that uniquely identifies each OSPF router 
- Hello Interval: How often the router sends Hello Packets (10 secs)
- Dead Interval: How long a router waits to hear from a neighbor before declaring it out of service. (4 x Hello Interval)
- Neighbors: A list of adjacent OSPF routers that the router has already received a Hello packet from
- Area ID: Area configured for that interface
- Router Priority: An 8 bit number used to select the DR and BDR
- DR and BDR IPv4 Address: If known
- Authentication Flag: Authentication details
- Stub Area Flag: If the area is a stub area, stub areas have a default route to their ABR rather than learning routes outside the area. 

These settings must match for a pair of OSPF routers to form an adjacency with each other:

* Must be in each other's Neighbors list
* Hello and Dead Intervals 
* Area ID
* IP subnet
* Authentication Flag
* Stub Area Flag


## OSPF DR and BDR
- In point to point links, OSPF router pairs for a full adjacency.
- On multi access segments, where there can be multiple routers, it is inefficient for all routers to form a FULL OSPF adjacency with each other.

* A DR (designated router) and BDR (backup designated router) are elected
* The router with the highest priority becomes DR and the router with 2nd highest priority becomes the BDR
* Default priority is 1, the higher the better 0-255
* Highest Router ID us used in case of a tie 

#### Neighbor States - "2-Way"

1. Down state >> 2. Init/attempt State >> 3. Two Way State >> 4. Exstart state >> 5. Exchange State >> 6. Loading State >> 7. Full State

- On multiaccess segments such as Ethernet, the routers elect the DR and BDR at the 2-Way Stage
- There is no election on point to point links

#### Setting OSPF Priority
```
#interface FastEthernet 0/0
#ip ospf priority 100
```
To make sure a router is never the BR:
```
ip ospf priority 0
```

To have the changes take effect OSPF must be restarted 

#### multiaccess segment neighbor states:
- The DR and BDR establish FULL neighbor state with all routers on the network segment
- The neighbor state of other neighbors remains in 2-Way and they do not directly exchange routes with each other

#### multiaccess segment LSA updates
* When a link state changes on a router connected to a multiaccess segment, it send a multicast LSU packet to 224.0.0.6 'all designated routers'
* The DR multicasts the update to 224.0.0.5 'all OSPF routers' 









