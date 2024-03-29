## HSRP - Hot Standby Router Protocol

Redundancy is a key factor in networks. As all devices point to a default gateway if that fails they will stop communicating outside. HSRP allows a secondary router to take over the role of the default gateway in case the first fails.

When a device powers on it either has a static IP or queries a DHCP server for a dynamic one. The device will have an IP, subnet and the address of the default gateway. Most devices can only store one IP for a default gateway, as a result if that gateway fails there wont be communication outside of their subnet. The router is a Single Point of Failure. Ideally, no network should have a SPOF and HSRP can help, with the introduction of a second router, and by configuring the two routers to use HSRP. A secondary gateway is prepared to mask itself as the primary, if the primary fails. 
To achieve this a **Virtual IP Address (VIP)** is added on both routers. By default, only the primary router will use it but if it fails the secondary will start using that address. The VIP is a dedicated address.

#### The First Hop Redundancy Protocol Family

HSRP is the first of the FHRP family. It is Cisco proprietary, easy to configure and troubleshoot. In the FHRP group there is also VRRP (Virtual Router Redundancy Protocol), an open standard and GLBP (Gateway Load Balancing Protocol) another Cisco implementation.

These protocols all have the final goal of default gateway redundancy, with differences in features and implementation.
    - HSRP and VRRP work almost identically, except that VRRP is standard
    - GLBP adds some load balancing features. It puts in place the ability to allow some clients to use a physical router and some other clients to use another. This enables load balancing over the LAN, depending on STP.

#### Components of HSRP 

You can configure multiple routers to share the same HSRP Virtual IP. However, only one of them will be active in a given moment. They must all understand they are sharing a Virtual IP and must talk to each other, to do so they communicate using the multicast IP 224.0.0.2 (HSRPv1) or 224.0.0.102 (HSRPv2).

During this communication, routers evaluate some key elements to define who should host the VIP. The router that is forwarding traffic for the VIP is called **active** while the others are **standby**

* HSRP GROUP NUMBER: the identifier of the HSRP Configuration. All HSRP settings can be associated with that group and there can be multiple groups per interface.
* VIRTUAL IP ADDRESS: they all must know which is the VIP to do HSRP, there is one VIP per HSRP Group
* PRIORITY OF THE ROUTER: default is 100 and ranges between 0 - 255. The higher, the most likely the router will be active. 
* PREEMPTION: allows a router with a better priority to take over the active role even if the other router (with a lower priority) is active. 

With this information the routers create a Virtual IP and Virtual MAC.

#### Virtual IP and Mac Addresses

HSRP faces some challenges in its process. One major obstacle is ARP. After the DHCP request, clients will only know the VIP of the default gateway. To communicate over Ethernet links, they need to use ARP to get MAC addresses. If as usual the client gets the **physical address of the primary router,** there will be an issue if it fails. Traffic will be sent to a non-working mac address until their MAC address table times out. Only then will a new ARP request be made and hopefully it will get the MAC of whichever router has taken over the VIP - this is not acceptable.
    
HSRP overcomes this limitation by creating a virtual MAC address. This MAC is shared among routers in the group and will be used from the active gateway only. All routers need to know it and be ready to use it if the active one fails. HSRP defines this as the **Standby Mac Address**

- 0000.0c07.acXX

XX represents the HSRP group number, so for a group 1 the mac would be 0000.0c07.ac01. Secondary routers monitor the primary one, when the primary fails the routers that are going to be active immediately send out frames with the Standby MAC as source. This way the MAC address table on a switch is immediately updated


#### Joining an HSRP Group

Routers in a group must talk with each other and understand their parameters. If they don't inter-operate there could be two routers believing they are the active one at the same time. If switches see the MAC in two places they believe it to be duplicate, interfaces start to flap creating high instability. 
HSRP's use of keep-alive messages is not just to verify availability of neighbors, but also to understand which neighbors are participating in the HSRP group. Two routers are in the same group if they have the same: *group number,* *standby IP address,* and *authentication settings.*

As HSRP allows the default gateway to dynamically move in the network, this creates some security issues. If a new router was attached to the network there is the possibility of moving the default gateway which can lead to man-in-the-middle attacks. To prevent this HSRP supports authentication of peers. Implementation of a password will lead to HSPR routers challenging before trusting another device.

#### HSRP and STP

When designing HSRP deployment, STP configuration needs to be considered. This becomes more evident in a Three-Tier System. ie: two routers connected to two distribution switches. If the primary router is connected to the non-root switch, all traffic will go to the root switch first. Then, the root switch will send it to the non-root distribution switch and then to the router. This is a suboptimal path. 
To avoid that the HSRP active router should be connected to the STP root switch so packets will take the most straightforward path.

#### Convergence Times

The convergence for HSRP is defined by timers. In fact, HSRP routers send keep-alive timers. If three keep-alive messages are lost, the routers assume the active gateway is down. By default hello packets are sent every 3 seconds and active dead is after 10 seconds. These can be configured.

#### Summary
* HSRP is a FHRP that creates a virtual IP and MAC. Routers working in the HSRP group know about them and if the primary router fils they take over the virtual addresses
* Routers must agree on a group number, virtual IP and authentication settings to join a group
* The active HSRP router should be connected to the stp root otherwise traffic can take a suboptimal route.
* MAC address 0000.0c07.acXX 








