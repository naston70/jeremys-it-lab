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
```
R1(config)# router ospf 10
R1(config-router)# network 172.16.1.1 0.0.0.0 area 0
R1(config-router)# network 172.16.3.1 0.0.0.0 area 0
R1(config-router)# network 192.168.10.5 0.0.0.0 area 0

R2(config)# router ospf 10 
R2(config-router)# network 172.16.2.0 0.0.0.255 area 0
R2(config-router)# network 172.16.3.0 0.0.0.3 area 0
R2(config-router)# 192.168.10.8 0.0.0.3 area 0

R3(config)# router ospf 10
R3(config-router)# network 192.168.1.0 0.0.0.255 area 0
R3(config-router)# network 192.168.10.4 0.0.0.3 area 0
R3(config-router)# network 192.168.10.8 0.0.0.3 area 0”
```

#### Passive Interfaces 

By default, OSPF messages are forwarded out all OSPF enabled interfaces. However, these messages really need to be sent out only interfaces that connect to other OSPF enabled routers. Sending out unneeded messages on a LAN affects the network in three ways:
**Inefficient use of bandwidth:** Available bandwidth is consumed by transporting unnecessary messages
**Inefficient use of resources:** All devices on the LAN must process the message 
**Increased security risk:** OSPF messages can be intercepted and routing updates can be modified, corrupting th routing table. Cisco

Use the ```passive-interface``` command to prevent OSPF updates from being sent out unnecessary interfaces.

As an alternative, all interfaces can be made passive using ```passive-interface default``` command. Then can be re-enabled by using ```no passive-interface``` interface command 

#### Modifying the OSPF Metric

Cisco IOS Software uses the cumulative bandwidths of the outgoing interfaces from the router to the destination network as the cost value. At each router, the cost for an interface is calculated using the following formula. 
```
Cisco IOS Cost for OSPF = 108/bandwidth in bps
```

In this calculation, 10**8 is known as the reference bandwidth. 

10Gig, Gigabit Ethernet and Fast Ethernet all have the same cost. That is because the OSPF cost value must be an integer. This was not an issue before the introduction of gigabit and higher data rates. 

However, today's networks run at Gigabit speeds. Therefore, as a matter of policy, the reference bandwidth should be changed to accommodate networks with links faster than 100,000,000 bps (100 Mbps)

The following command changes reference bandwidth:
```
Router(config-router)# auto-cost reference-bandwidth [Mbps]
```

Because the value entered is in megabits per second, changing the reference-bandwidth to 10000 ensures that all OSPF routers are ready to accurately calculate the cost for 10GigE networks. When used, this command should be entered on all routers so that the OSPF routing metric remains consistent. 

#### Changing the OSPF Reference Bandwidth
```
R1(config-router)# auto-cost reference-bandwidth 10000
```

###### OSPF Cost Values with Modified Reference Bandwidth = 10000

10 Gigabit Ethernet = Cost 1
1 Gigabit Ethernet  = Cost 10
Fast Ethernet (100) = Cost 100
Ethernet (100 Mbps) = Cost 1000
T1                  = Cost 6477
128 Kbps            = Cost 78125

There is still another adjustment to ensure OSFP is using accurate costs. On Cisco routers, the default bandwidth on most serial interfaces is set to T1. However, this may be different to actual speeds.

 