# OSPF - review

OSPF Router ID Selection Priority:
	1. Manual Configuration
	2. Highest IP on a loopback interface
	3. Highest IP on a physical interface
- SPF algorithm is also known as Dijkstra's algorithm
- LSAs are organized in structure called the LSDB
- ABR = Area Border Router

#### OPSF Commands

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


