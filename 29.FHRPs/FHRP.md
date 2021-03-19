# First Hop Redundancy Protocols

A first hop redundancy protocol FHRP is a computer networking protocol which is designed to protect the default gateway used on a subnetwork by allowing two or more routers to provide backup for that address. In the event of failure of an active router, the backup router will take over the address, usually within seconds.

* A **virtual IP** is configured on the two routers and a virtual MAC is generated for the virtual IP 
* An active and stand-by router are elected
* End hosts in the network are configured to use the virtual IP as their default gateway
* The active router replies to ARP requests using the virtual MAC address, so traffic destined for other networks will be sent to it.
* If the active router fails, the standby becomes the next active router. The new active router will send **gratuitous ARP** messages so that switches will update their MAC address tables. It now functions as the default gateway
* If the old router comes back online, by default it wont take back the role as active router so will become the standby router
* 'preemption' can be configured so that the old active router does take back its role.