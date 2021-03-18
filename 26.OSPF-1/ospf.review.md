# OSPF - review




OSPF Router ID Selection Priority:
	1. Manual Configuration
	2. Highest IP on a loopback interface
	3. Highest IP on a physical interface

- Formula to calculate OSPF interface cost - Reference Bandwidth / interface bandwidth (default ref = 100 mbps)
- SPF algorithm is also known as Dijkstra's algorithm
- Multicast address for OSPF = 224.0.0.5
- Default Hello timer = 10 seconds
- Default Dead timer  = 40 seconds
- LSAs are organized in structure called the LSDB
- ABR = Area Border Router
- ASBR = Autonomous System Boundary Router
- ASBR's connect the OSPF network to an external network
- An inter-area route is a route to a destination in a different OSPF area
- Routers with all interfaces in the same area are called 'internal' routers

#### OSPF Neighbor States:

1  Down
2. Init
3. 2-Way
4. Exstart
5. Exchange
6. Loading
7. Full

#### Election of BR / BDR


OSPF BR/BDR election order of priority:
	- Highest OSPF interface priority
	- Highest OSFP router ID


- Default priority on all interfaces = 1
- Messages to OSPF DR/BDR are multicast using 224.0.0.6

#### OPSF Commands

Enter OSPF configuration mode:
```
R1(config-router)#router ospf [process-id]
```

Manually configure the OSPF router ID
```
R1(config-router)#router-id [x.x.x.x]
```

Reset OSPF process:
```
R1(config-router)#clear ip ospf process
```

Enable OSPF on interfaces in the specified range:
```
R1(config-router)# network [ip-address] [wc-mask] area [area]
```

Prevent an OSPF router from sending OSPF messages out of an OSPF-enabled interface:
```
R1(config-router)# passive-interface [interface-id]
```

Configure an OSPF router to advertise its default route into the OSPF domain:
```
R1(config-router)# default-information originate
```

Modify the OSPF AD on the local router:
```
R1(config-router)#distance [value]
```

Configure max paths an OSPF router will use to perform ECMP load-balancing:
```
R1(config-router)# maximum-paths [number]
```

Configure OSPF reference bandwidth:
```
R1(config-router)#auto-cost reference-bandwidth [Mbps]
```

Configure cost of an interface:
```
R1(config-router)#ip ospf cost [cost]
```

Down-init-2Way-exstart-exchange-loading-full
