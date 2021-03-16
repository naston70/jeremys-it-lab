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
