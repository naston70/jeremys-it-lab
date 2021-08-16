## Single-Area OSPF Implementation

Exam Topics:

- Configure and verify single area OSPFv2

------------------------------------------
**R1**
G0/0: 172.16.1.1 255.255.255.0

S0/0/0: 172.16.3.1 255.255.255.252

S0/0/1: 192.168.10.5 255.255.255.252

**R2**
G0/0: 172.16.2.1 255.255.255.0

S0/0/0: 172.16.3.2 255.255.255.252

S0/0/1: 192.168.10.9 255.255.255.252

**R3**
G0/0: 192.168.1.1 255.255.255.0 

S0/0/0: 192.168.10.6 255.255.255.252

S0/0/1: 192.168.10.10 255.255.255.252
------------------------------------------

#### The **router ospf** command

OSPF is enabled with the ```router ospf process-id``` global configuration command:
```
R1(config)# router ospf process-id

```

*process-id* is a number between 1 and 65535 and is chosen by the network administrator. The process-id is locally significant. It does not have to match other OSPF routers to establish adjacencies with those neighbors. This differs from EIGRP as the EIGRP process ID and autonomous system number must match before two EIGRP neighbors can become adjacent. 

#### Router ID 

The router ID plays an important role in OSPF, uniquely identifying each router in the OSPF routing domain. Cisco routers derive the router ID as follows:

1. The router uses the IP address configured with the OSPF ```router-id``` cmd
2. If the router ID is not configured, the router chooses the highest IP address of any of its loopback interfaces
3. If no loopback interfaces are configured, the router chooses the highest active IP address of any of its physical interfaces

The router ID can be viewed with several commands;
```
show ip ospf interfaces, show ip protocols, show ip ospf 
```
It is best practice to configure the ```router-id``` command. The command accepts an IPv4 address as its only argument.

The Router ID is selected when OSPF is configured with its first OSPF **network** command, so the **router-id** command should already be configured. 
```
R1(config-router)# router-id 1.1.1.1
```

However, you can force OSPF to release its current ID and use the configured ID by clearing the OSPF routing process
```
# clear ip ospf process
```

#### The ```network``` Command 

The ```network``` command is used in router configuration mode:
```
Router(config-router)# network [network-address][wildcard-mask] area [area-id]
```

The OSPF **network** command uses a combination of network-address and wildcard-mask. The network-address along with the wildcard-mask, specifies the interface or range of interfaces that will be enabled for OSPF using this network command 

The wildcard-mask is customarily configured as the inverse of a subnet mask.

**area area-id** refers to the OSPF area. An OSPF area is a group of routers that share link-state information. All OSPF routers in the same area must have the same link-state information in their link-state databases. Therefore, all the routers within the same OSPF area must be configured with the same area ID on all routers. By convention, area 0. 

#### Configuring OSPF Networks 


