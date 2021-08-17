## Fine Tuning and Troubleshooting OSPF

Exam Topics

- Configure and verify single area ospf

## OSPFv2 Configuration
```
R1(config)# router ospf 10
R1(config-router)# router-id 1.1.1.1
R1(config-router)# network 172.16.1.0 0.0.0.3 area 0 
R1(config-router)# network 172.16.3.0 0.0.0.3 area 0
R1(config-router)# network 192.168.10.4 0.0.0.3 area 0
R1(config-router)# passive-interface g0/0
R1(config-router)# auto-cost reference-bandwidth 10000
R1(config-router)# interface s0/0/1
R1(config-router)# bandwidth 64 
```

## Modifying OSPFv2

#### Redistributing a Default Route 

(Example R1 has a link to the Internet, that makes R1 an autonomous system boundary router).
Therefore a default route to the Internet is configured and redistribute the default static route with the ```default-information originate```command. 
```
R1(config)# ip route 0.0.0.0 0.0.0.0 Serial 0/1/0
R1(config)# router ospf 10
R1(config-router)# default-information originate
```

Any other routers in the area should now have default routes identified with the O*E2 code.

#### Modifying Hello and Dead Intervals

The default hello interval on multiaccess and point-to-point networks is 10 seconds. Non-broadcast multiaccess networks default to a 30-second hello interval. The default dead interval is for times the hello interval. It might be desirable to change the OSPF timers so that routers detect network failures in less time. Doing this increases the traffic, but sometimes a need for quick convergence outweighs the extra traffic. The OSPF hello and dead intervals can be manually modified using the following commands:
```
R1(config-if)# ip ospf hello-interval [seconds]
R1(config-if)# ip ospf dead-interval [seconds]
```

Although the dead interval defaults to four times the hello interval and does not have to be explicitly configured, it is a good practice to document the new dead interval in the configuration

#### OSPF Network Types

OSPF defines five network types:
- **Point-to-point:** Two routers interconnected over a common link. No other routers are on the link. This is often the configuration in WAN links.
- **Broadcast multiaccess:** Multiple routers interconnected over an Ethernet network
- **NBMA:** Multiple routers interconnected in a network that does not allow broadcasts, such as Frame Relay.
- **Point-to-multipoint:** Multiple routers interconnected in a hub-and-spoke topology over an NMBA network. Often used to connect branch sites (spokes) to a central site (hub)
- **Virtual links:** Special OSPF network used to interconnect distant OSPF areas to the backbone area

Multiaccess networks create two challenges for OSPF regarding the flooding of LSAs:

- **Creation of multiple adjacencies:** Ethernet networks can potentially interconnect many OSPF routers over a common link. 
- **Extensive flooding of LSAs:** Link-state routers flood their link-state packets when OSPF is initialized or when the topology changes. This flooding can become excessive without a mechanism to reduce the number of adjacencies

## DR/BDR Election

The solution to managing the number of adjacencies and the flooding of LSAs on a multiaccess network is the designated router. To reduce the amount of OSPF traffic on multiaccess networks, OSPF elects a DR and backup DR. The DR is responsible for updating all other OSPF routers when a change occurs in the multiaccess network. The BDR monitors the DR and takes over as DR if the current DR fails.

The following criteria are used to elect the DR and BDR:
- The DR is the router with the highest OSPF interface priority
- The BDR is the router with the 2nd highest OPSF interface priority
- If OSPF interface priorities are equal, the highest router ID breaks the tie 

WHen the DR is elected, it remains the DR until one of the following conditions occurs:
- The DR fails 
- The OSPF process on the DR fails 
- The multiaccess interface on the DR fails 
If the DR fails, the BDR assumes the role of DR, and an election is held to choose the new BDR. If a new router enters the network after the DR and BDR have been elected, it will not become the DR or BDR even if it has a higher  OSPF interface priority or router ID than the current. The new router can be elected the BDR if the current DR or BDR fails. If the current DR fails, the BDR becomes the DR and the new router can be elected the new BDR. With additional configuration, you can control the routers that win the DR and BDR elections by doing either of the following:

- Boot the DR first, followed by the BDR, and then all other routers.
- Shut down the interface on all routers and then issue the no shutdown on the DR, then BDR, then all other routers. 

The recommended way to control BR/BDR elections is to change the interface priority.

#### Controlling the DR/BDR Election 

As the DR becomes the focal point for the collection and distribution of LSAs in a multiaccess network, this router must have sufficient CPU and memory capacity to handle the responsibility. Instead of relying on the router ID to decide which routers are elected the DR and BDR, it is better to control the election of these routers with the ```ip ospf priority```interface command:
```
Router(config-if)# ip ospf priority {0-255}
```

The priority value defaults to 1 for all router interface, which means the router ID determines the DR and BDR. If you change the default value from 1 to a higher value, however, the router with the highest priority becomes the DR and the router with the next highest priority becomes the BDR. A value of 0 makes a router ineligible to become a DR or BDR. The

#### Modifying the OSPF Interface Priority
```
R1(config)# interface gigabitethernet 0/0
R1(config-if)# ip ospf priority 200
```

## Troubleshooting OSPF 

#### OSPF states

When troubleshooting OSPF neighbors, be aware that the FULL and TWO-WAY states are normal. All other states are transitory.

###### Establish Neighbor adjacencies:
Down state -> Init State -> Two-Way State -> 
###### Synchronize OPSF Databases:
ExStart State -> Exchange State -> Loading State -> Full State 

#### OSPF adjacency:

Lack of adjacency is a common issue in OSPF troubleshooting because the two OSPF neighbors must agree on several settings. OSPF adjacencies do not form for several reasons:
- Interfaces are not on the same networks
- OSPF network types do not match
- OSPF hello or dead timers do not match
- The interface to the neighbor is incorrectly configured as passive 
- An OSPF network command is missing or incorrect 
- Authentication is misconfigured 

#### OSPF Troubleshooting Commands
