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








