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