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
- Multicast Ip 224.0.0.18
- Virtual MAC adress 0000.5e00.01XX (XX = VRRP group number)
- In a situation with multiple subnets/VLANs, you can configure a different master router in each subnet/ VALN to load balance
