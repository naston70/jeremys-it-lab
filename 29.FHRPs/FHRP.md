# First Hop Redundancy Protocols

A first hop redundancy protocol FHRP is a computer networking protocol which is designed to protect the default gateway used on a subnetwork by allowing two or more routers to provide backup for that address. In the event of failure of an active router, the backup router will take over the address, usually within seconds.

* A **virtual IP** is configured on the two routers and a virtual MAC is generated for the virtual IP 
* An active and stand-by router are elected
* End hosts in the network are configured to use the virtual IP as their default gateway
* The active router replies to ARP requests using the virtual MAC address, so traffic destined for other networks will be sent to it.
* If the active router fails, the standby becomes the next active router. The new active router will send **gratuitous ARP** messages so that switches will update their MAC address tables. It now functions as the default gateway
* If the old router comes back online, by default it wont take back the role as active router so will become the standby router
* 'preemption' can be configured so that the old active router does take back its role.

## HSRP - Hot Standby Router Protocol
- Cisco Proprietary 
- An active and standby router are elected
- There are two version: version 1 and version 2
- Version 2 adds IPv6 support and increases the number of groups that can be configured
- Multicast IPv4 address: v1 = 224.0.0.2, v2 = 224.0.0.102
- Virtual MAC address: v1 = 0000.0c07.acXX, v2 = 000.0c9f.fXXX
- In a situation with multiple subnets/VLANs, you can configure a different active router in each subnet/VLAN to load balance

## VRRP - Virtual Router Redundancy Protocol
- Open standard
- A master and backup router are elected
- Multicast IP 224.0.0.18
- Virtual MAC address 0000.5e00.01XX (XX = VRRP group number)
- In a situation with multiple subnets/VLANs, you can configure a different master router in each subnet/ VALN to load balance

## GLBP Gateway Load Balancing Protocol
- Cisco Proprietary 
- Load balances among multiple routers within a single subnet
- AN **AVG (Active Virtual Gateway)** is elected
- Up to four **AVFs (Active Virtual Forwarders)** are assigned by the AVG (The AVG can itself be an AVF, too)
- Each AVF acts as the default gateway for a portion of the hosts in the subnet
- Multicast IPv4 address: 224.0.0.102
- Virtual MAC address 0007.b400.XXYY (XX= GLBP number, YY = AVF Number)

| FHRP | Terminology    | 224.0.0.X | Virtual MAC    | Cisco |
|------|----------------|-----------|----------------|-------|
| HSRP | Active/Standby | .2 .102   | 0000.00c7.acXX | Yes   |
|      |                |           | 0000.0c9f.fXXX |       |
| VRRP | Master/Standby | .18       | 0000.5e00.01XX | No    |
| GLBP | AVG/AVF        | .102      | 0007.b400.XXYY | Yes   |





