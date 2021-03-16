# OSPF - 2
Exam topic 3.4 - Configure and verify single area ospf - neighbour adjacencies - point to point - Broadcast - Router ID

## OSPF Cost

* OSPFs metric is called cost
* It is automatically calculated based on the bandwidth of the interface (speed)
* It is calculated by dividing a reference bandwidth value by the interfaces bandwidth
* The default reference bandwidth is 100 mbps

* All values less than 1 will be converted to 1
* Therefore FastEthernet, Gigabit and 10 Gig Ethernet are equal and all have a cost of 1 by default
* You can and should change the reference bandwidth with the following command:
```R1(config-router)# auto-cost reference-bandwidth mbps```

* The command is entered in megabits per second (default of 100)
```R1(config-router)# auto-cost reference-bandwidth 100000```

* 100000 is a good number to use for the new default:
	- 100000 / 100 = cost of 1000 for FastEthernet
	- 100000 / 1000 = cost of 100 for GigabitEthernet
* A reference bandwidth should be configured to be greater than the fastest links in the network to allow for fuure upgrades
* The same reference bandwidth should be configured on all OSPF routers in the network

- Three ways to modify the OSPF cost:
	1) Change the reference bandwidth:
	```R1(config-router)# auto-cost reference-bandwidth mbps
	```

	2) Manual configuration
	```R1(config-if)# ip ospf cost cost
	```


	3) Change the interface bandwidth (not recommended)
	```R1(config-if)# bandwidth kbps
	```
- As the bandwidth value is used in other calculations, it is not recommended to change this value to alter an interfaces OSPF cost
- It is recommended that the reference bandwidth is changed and then use the ip ospf cpst command to change the cost of individual interfaces if needed

- ```#show ip ospf interface brief``` gives an overview of all OSPF interfaces activate


## OSPF Neighbors

* Making sure that routers successfully become OSPF neighbors is the main task in configuring and troubleshooting OSPF
* Once routers become neighbors, they automatically do the work of sharing network information, calculating routes, etc
* When OSPF is activated in an interface, the router starts sending OSPF **hello** messages out of the interface at regular intervals (determined by the **hello timer**). These are used to introduce the router to potential OSPF neighbors
* The default hello timer is 10 seconds on an Ethernet connection
* Hello messages are multicast to 224.0.0.4 (multicast address for all OSPF routers)
* OSPF messages are encapsulated in an IP header, with a value of 89 in the protocol field


#### OSPF Neighbors - Down State

[R1]G0/0 -|-------------- 10.0.12.0/30 ---------------|- G0/0[R2]
	  .1 												   .2

- OSPF is activated on R1's G0/0 interface
- It sends an OSPF hello message to 224.0.0.5

Hello message
	 My RID : 1.1.1.1
Neigbour RID: 0.0.0.0


The hello contains R1's ID but R2's is unknown, it doesn't know about any OSPF neighbors so the current neighbor state is **down**

#### OSPF neighbors - Init State

* When R2 receives the Hello packet, it will add an entry for R1 to its OSPF neighbor table.
* In R2's neighbor table, the relationship is now in the **init** state.
* **Init** state = Hello packets received, but own router ID is not in the Hello packet.

#### OSPF neighbors - 2-way State

* R2 will send a Hello packet containing the RID of both routers.
* R1 will insert R2 into its OSPF neighbor table in the **2-way** state.

* R1 will send another Hello message, this time containing R2's RID. Now both routers are in the 2-way state.

- The 2-way state means the router has received a Hello packet with its own RID in it.
- If both routers reach the 2-way state, it means that all of the conditions have been met for them to become OSPF neighbors. They are now ready to share LSAs to build a common LSDB
- In some networks a DR (designated router) and BDR (backup designated router) will be elected at this point.

#### OSPF neighbors - Exstart State

* The two routers will now prepare to exchange information about their LSDB
* Before that, they have to choose which one will start the exchange.
* They do this in the Exstart state
* The router with the higher RIS will become the Master (Origin) and initiate the exchange. The router with the lower RID will become the receiver
* To decide the sender and receiver, they exchange DBD packets.

#### OSPF neighbors - Exchange State

- In the exchange state, the routers exchange DBDs (database descriptor) which contain a list of the LSAs in their LSDB
- The DBDs do not include detailed information about the LSAs, just basic information
- The routers compare the information in the DBD they receive to the information in their own LSDB to determine which LSAs they must receive from their neighbor

#### OSPF neighbors - Loading State

- In the Loading state, routers send Link State Request messages to request that their neighbors send them any LSAs they dont have.
- LSAs are sent in Link State Updates (LSUs)
- The routers then send LSAck messages to acknowledge that they received the LSAs

#### OSPF Neighbors - Full State

* In the Full state, the routers have a full OSPF adjacency and identical LSDB
* They continue to send and listen for Hello packets (every 10 secs by default) to maintain the neighbor adjacency
* Every time a Hello packet is received, the 'Dead' timer is reset (40 secs by default)
* If the Dead timer counts down to 0 and no Hello message is received, the neighbor is removed.
* The routers will continue to share LSAs as the network changes to make sure each router has a complete and accurate map of the network

OSPF NEIGHBOR STATES -----> DOWN + INIT + 2-WAY + EXSTART + EXCHANGE + LOADING + FULL

