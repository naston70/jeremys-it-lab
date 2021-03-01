# Static Routes

Switches forward traffic in a LAN, routers forward traffic between LANs

WAN - Wide Area Network - A network that extends over a large geographical area

When forwarding a packet: Is the destination in the same network? If no, send the packet to the **default gateway.**

When the router receives a packet in compares the packets destination IP address to the **routing table**. Assuming it is found it will forward the packet to the next hop. 

#### Routing Table

```
R1> show ip route

---- lines omitted ----

Gateway of last resort not set
		
		192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C 			192.168.1.0/24 is directly connected, G0/0
L 			192.168.1.1/32 is directly connected G0/0
```

C = Connected route: the network the interface is connected to 
L = Local route: the actual IP address on the interface (with a /32 mask)

When a route isn't in the routing table for an end host for example. All it needs is a default gateway to which it can send any traffic destined for outside the LAN - In Cisco this is known as the gateway of last resort.

##### Configuring a default route

* To confogure a **gateway of last resort** on a Cisco router, you must configure a **default route**
* A **default route** is a route that matches ALL possible destinations
* It is used only if a more specific route match isn't found in the routing table
* The default route is the least specific route possible:
	- IP: 0.0.0.0
	- Mask: 0.0.0.0


