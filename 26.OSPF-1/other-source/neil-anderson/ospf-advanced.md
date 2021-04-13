## OSPF Advanced 

* OSPF routers identify themselves using an OSPF Router ID which is in the form of an IP address 
* This will default to being the highest IP address of any loopback interfaces configured on the router, or the highest other IP address if a loopback doesn't exist
* Loopback interfaces never go down so the router ID will not change
* You can manually specify the Router ID
* Best practice is to use a Loopback or manually set the Router ID 

- If a loopback or higher IP address is configured, the ROuter ID will only change on OSPF process restart.

#### Passive Interface Configuration

```
#router ospf 1
#passive-interface [loopback]
#passive-interface [interface]
```

The interface will be advertised but wont try to form any adjacencies or share any information.

Possible to make ```passive-interface default``` to make all interfaces passive

#### Default Route Injection

Create a default route out to the Internet:
```
#ip route 0.0.0.0 0.0.0.0 203.0.113.2
#router ospf 1
#default-information originate
```

It is undesirable to make static routes out to the Internet on every device so better to create a default static route and let it be learned dynamically

#### The 'speed' command

- The rate that Ethernet interfaces physically transmit at is set by the 'speed' command
- GigabitEthernet interfaces transmit at 1000 Mbps by default
- FastEthernet interfaces transmit at 100 Mbps by default
- If you use the 'speed 10' command on a FastEthernet interface it will physically transmit at 10 Mbps

#### The 'clock rate' command - serial interfaces

* The rate that serial interfaces physically transmit at is set by the 'clock rate' command
* serial interfaces transmit at 1.544 Mbps by default 
* If you use the 'clock rate 64000' command on s Serial Interface it will physically transmit at 64 Kbps

#### The 'bandwidth' command

* Interfaces also have a default bandwidth
* The bandwidth usually matches the physical transmission rate of the interface
* The 'bandwidth' setting on an interface does not affect th physical transmission rate -  that is set by the speed or clock rate
* If a bandwidth of 50 Mbps on a FastEthernet interface is set, it will still transmit at 100 Mbps

As the **bandwidth** command does not affect speed, what does it do?

- The command affects software policy on the router, such as which path will be selected by EIGRP or OSPF, or how much bandwidth will be guaranteed to a traffic type by QoS
- Software policy can be influenced by setting the bandwidth on an interface

## OSPF Cost Metric

* As OSPF is a Link State routing protocol, the router will learn about all destinations in its area, the links and their Cost
* The router will select routes based on its lowest cost to get to the destination

#### Reference Bandwidth 
- The cost is automatically derived from the interface bandwidth
- Cost = Reference Bandwidth / Interface Bandwidth 
- The default reference bandwidth is 100 Mbps 
- FastEthernet link cost defaults to 1 (100 / 100)
- T1 link cost defaults to 64 (100 / 1.544)

This leads to the problem of OSPF treating all interfaces of 100 Mbps or faster as equal. FastEthernet, GigabitEthernet, 10 GigabitEthernet etc all default to a cost of 1. This can cause undesirable routing in a modern network.

To avoid this the reference bandwidth should be changed on all routers. This is done by using the following command:
```
#auto-cost reference bandwidth 100000
```

OSPF takes the bandwidth of an interface into account when calculating the metric, so paths along higher bandwidth links will be preferred. The most desirable path will be typically automatically selected.
If the selected path is not what is required it is possible to manipulate the path by manually changing the bandwidth or OSPF cost on interfaces.
*It is recommended to use cost for this because the bandwidth setting can affect many features other than OSPF - such as QoS*

A manually configured OSPF cost overrides the value derived from bandwidth
 


