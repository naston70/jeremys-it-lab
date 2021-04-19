## HSRP 

Network redundancy, FHRP and HSRP.

#### Network Redundancy

- Common in small networks / office branches for there to be a single point of fail. The cost of adding redundant devices cannot be justified 
- The point of redundancy is to eliminate single points of failure
- Larger networks can justify the cost
- Internet should be reachable if any core/ distribution switch, router or link fails
- Typically there is no redundancy at the access layer and end hosts only have one network card
- Servers with redundant NICs are an exception

#### Redundancy at Layer 3

Add a static route to the SP router, A backup default static route via the second router if the link to SP1 goes down.
ie: ```ip route 0.0.0.0 0.0.0.0 ip_address 5``` this adds the backup route with a higher administrative distance of 5. Not for load balancing. 
A backup route to go downstream would also need to be added for the interface on the router still up.

## FHRP's - First Hop Redundancy Protocols

A FHRP is a protocol which is designed to protect the default gateway used on a subnetwork by allowing two or more routers to provide backup for that address. In the event of a failure of an active router, the backup router will take over the address, usually within seconds.

EG: HSRP (hot standby router protocol), VRRP (virtual routing redundancy protocol), GLBP (gateway load balancing protocol)

IP routing redundancy is designed to allow for transparent fail-over at the first-hop IP router.

(Cisco)
Both HSRP and VRRP enable two or more devices to work together in a group, sharing a single IP address. The virtual IP is configured in each end users workstation as a default gateway address and is cached in the hosts ARP cache.
In an HSRP or VRRP group, one router is elected to handle all requests sent to the virtual IP address. With HSRP this is the active router. HSRP groups have one active router and at least one standby router. A VVRP group has one acive router and one or more backup routers.

* FHRP's use a virtual IP and MAC address to allow for automated gateway fail-over
* The hosts use the VIP as their default gateway address
* If the physical gateway fails, another gateway will take over

- HSRP: Cisco proprietary, active/standby pair
- VRRP: Open standard, active/standby pair
- GLBP: Cisco proprietary, supports active/active load balancing across multiple routers

#### HSRP - Hot Standby Router Protocol Operations

* Both routers have a normal physical IP address and MAC address on their HSRP interface. Unique addresses are used on both routers.
* They both have the HSRP virtual IP and MAC address configured on the interface. The same addresses are used on both routers.
* When they come online, one is elected the HSRP active router, the other is the standby 
* The active router owns the virtual IP and MAC address and responds to ARP requests
* All traffic for the VIP goes through the active router
* The routers send hello messages to each other over their HSRP interface
* If the standby router stops receiving hellos from the active it will transition to be the active router
* It will take ownership of the virtual IP and MAC address and respond to ARP requests

#### HSRP Configuration

```
#int g0/1
#ip address 10.10.10.2 255.255.255.0
#no shutdown
#standby 1 10.10.10.1
```
Use the same ```standby``` address on two routers, to verify it:```show standby```

#### Priority and Pre-emption

* You can choose which router will be active by setting priority on the router when doing configuration
* The router with the higher priority will be preferred
* In the event of a tie the highest IP address wins
* If pre-emption is also enabled, when a higher priority router comes back online after a failure it will transition back to active
* If pre-emption is not enabled, the lower priority router will remain active when the failed router comes back online
* This can be more stable if a higher priority router is flapping

```
#int g0/1
#ip address 10.10.10.2 255.255.255.0
#no shutdown
#standby 1 priority 110
#standby 1 pre-empt 
```


#### HSRP Version

- HSRP version 2 introduced some improvements
- version 1 is default
- Both routers must be running the same version

**Version 2 configuration:**
example from udemy:
```
#int g0/1
#ip address 10.10.10.2 255.255.255.0
#no shutdown
#standby 1 ip 10.10.10.1
#standby version 2
```

This must be configured on both routers, only difference being the IP address of the interfaces on different routers.
Verification is done via ```show standby``` (shows active router, pre-emption enabled etc)

Possible to have different interfaces active on different subnets. 

