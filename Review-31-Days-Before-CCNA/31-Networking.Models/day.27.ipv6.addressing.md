## IPv6 Addressing 

Exam Topics

- Configure and verify IPv6 addressing and prefix
- Compare IPv6 address types

#### Overview and Benefits of IPv6

Scaling networks today requires a limitless supply of IP addresses and improved mobility that private addressing and NAT alone cannot meet. IPv6 satisfies the increasingly complex requirements of hierarchical addressing that IPv4 does not provide. The main benefits include:

* Extended address space: 128 bit address space 

* Stateless address autoconfiguration: IPv6 provides host devices with a method for generating their own routable IPv6 addresses. IPv6 also supports stateful configuration using DHCPv6

* Eliminates the need for NAT/PAT: NAT/PAT was conceived as part of the solution to IPv4 address depletion.

* Simpler Header: A simpler header offers several advantages over IPv4:
    - Better routing efficiency for performance and forwarding-rate scalability
    - No broadcasts and thus, no potential threat of broadcast storms 
    - No requirement for processing checksums
    - Simpler and more efficient extension header mechanisms 

* Mobility and security: helps compliance with mobile and IPsec standards:
    - IPv4 does not automatically enable mobile devices to move without breaks in established network connections
    - In IPv6, mobility is built which means that any IPv6 node can us mobility when necessary 
    - IPsec is enabled on every IPv6 node is available for use, making the IPv6 Internet more secure

* Transition strategies: You can incorporate existing IPv4 capabilities with the added features of IPv6 in several ways
    - You can implement a dual-stack method, with both IPv4 and IPv6 configured on the interface of a network device.
    - You can use tunneling, which becomes more prominent as the adoption of IPv6 grows. 

#### IPv6 Address Types

IPv4 has three address type, unicast, multicast and broadcast. IPv6 does not use broadcast addresses. Instead IPv6 uses unicast, multicast and anycast addresses

**Unicast:-**
Global Unicast | Link-local | Loopback | Unspecified Address | Unique Local | Embedded IPv4

**Multicast:-** Assigned | Solicited node

**Anycast**

#### Unicast

A unicast address uniquely identifies an interface on an IPv6 device. A packet sent to a unicast address is received by the interface that is assigned to that address. Much as with IPv4, source IPv6 addresses must be unicast addresses. 

###### Global Unicast Address

IPv6 has an address format that enables aggregation upward, eventually to the ISP. An IPv6 global unicast address is globally unique. 
