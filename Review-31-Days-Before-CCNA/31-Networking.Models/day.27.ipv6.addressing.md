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

Global Unicast: 2000::/3
Link-local: FE80::/10
Loopback: ::1/128
Unspecified: ::/128
Unique Local: FC00::/7
Embedded IPv4: ::/80

IPv4 has three address type, unicast, multicast and broadcast. IPv6 does not use broadcast addresses. Instead IPv6 uses unicast, multicast and anycast addresses

**Unicast:-**
Global Unicast | Link-local | Loopback | Unspecified Address | Unique Local | Embedded IPv4

**Multicast:-** Assigned | Solicited node

**Anycast**

#### Unicast

A unicast address uniquely identifies an interface on an IPv6 device. A packet sent to a unicast address is received by the interface that is assigned to that address. Much as with IPv4, source IPv6 addresses must be unicast addresses. 

###### Global Unicast Address

IPv6 has an address format that enables aggregation upward, eventually to the ISP. An IPv6 global unicast address is globally unique. Like a public IPv4 address it can be routed in the Internet without modification. An IPv6 global unicast address consists of a 48 bit global routing prefix, a 16 bit subnet ID and a 64 bit interface ID. 

Global unicast addresses that are currently assigned by the IANA use the range of addresses starting with 001 (2000::/3). This range represents one-eight of the total IPv6 total address space and is the largest block of assigned addresses.

Using the 2000::/3 pie piece, the IANA assigns /23 or shorter address blocks to the RIRs, from there, ISPs are assigned /32 or shorter and customer are the assigned /48 or shorter blocks. 

In IPv6 an interface can be configured with multiple global unicast addresses, which can be on the same or different subnets In addition, an interface does not have to be configured with a global unicast address, but it must have at least a link-local address. 

###### Summary of Global Unicast Configuration Options

**Manual:** 
    - *Static:*
     Much as with IPv4, the IPv6 address and prefix are statically configured on the interface
    - *EUI-64:*
    The prefix is configured manually. The EUI-64 process uses the MAC address to generate the 64-bit interface ID
    - *IPv6 unnumbered:* 
    Much as with IPv4, an interface can be configured to the IPv6 address of another interface on the same device. 

**Dynamic:**
    - *Stateless Address autoconfiguration:*
    SLAAC determines the prefix and prefix length from neighbor discovery router advertisement messages and then creates the interface ID using the EUI-64 method
    - *DHCPv6:*
    Much as with IPv4, a device can receive some or all of its addressing from a DHCPv6 server


###### Link-local Address

Link-local address are confined to a single link. They need to be unique only to that link because packets with a link-local source or destination address are not routable off the link.
Link-local addresses are configured in one of three ways:
* Dynamically, using EUI-64
* Using a randomly generated interface ID
* Statically, entering the link-local address manually

Link-local address provide a unique benefit in IPv6. A device can create its link-local address completely on its own. 

Link-local unicast addresses are in the range FE80::/10 to FEBF::/10

###### Loopback Address 
The loopback address for IPv6 is an all-0s address except for the last bit, which is set to 1. As in IPv4, an end device uses the IPv6 loopback address to send an IPv6 packet to itself to test the TCP/IP stack. The loopback address cannot be assigned to an interface and is not routable outside the device. 

###### Unspecified Address

The unspecified unicast address is the all-0s address, represented as ::. It cannot be assigned to an interface but is reserved for communications when the sending device does not have a valid IPv6 address yet. For example, a device uses :: as the source address when using the duplicate address detection (DAD) process. The DAD process ensures a unique link-local address. Before a device can begin using its newly created link-local address, it sends out an all-nodes multicast to all devices on the link, with its new address as the destination. If the device receives a response, it knows the link-local address is in use and therefore needs to create another link-local address. 

###### Unique Local Address

Unique local addresses (ULA) are defined by RFC 4193. These are private addresses. However, unlike IPv4, ULAs are globally unique. This is possible due to the relatively large amount of address space in the Global ID portion. 
Unique Local addresses have the following characteristics:

- Possess a globally unique prefix or at least have a very high probability of being unique
- Allows sits to be combined or privately interconnected without address conflicts or addressing renumbering
- Remain independent of any Internet service provider and can be used within a site without having Internet connectivity
- If accidentally leaked outside a site by either routing or the Domain Name System, don cause a conflict
- Can be used just like a global unicast address

###### IPv4 Embedded Address

IPv4 and IPv6 are not compatible. Features such as NAPT-PT and NAT64 are required to translate between the two address famalies. IPv4-mapped IPv6 addresses are used by transition mechanisms on hosts and routers to create IPv4 tunnels that deliver IPv6 packets over IPv4 networks. 

To create an IPv4 mapped IPv6 address, the IPv4 address is embedded within the low-order 32 bits of the IPv6. Basically IPv6 just puts an IPv4 address at the end and pads the rest of the address. The address doesn not have to be globally unique. 

#### Multicast - prefix FF00::/8

Multicast is a technique by which a device sends a single packet to multiple destinations simultaneously. AN IPv6 multicast address defines a group of devices known as a multicast group. 
Two types of IPv6 multicast addresses are used:
- Assigned multicast 
- Solicited-node multicast

###### Assigned Multicast 

Assigned Multicast addresses are used in context with specific protocols.

Two common IPv6 assigned multicast groups include the following:
        - FF02::1: All nodes multicast group:
        This is a multicast group that all IPv6 enabled devices join. As with a broadcast in IPv4, all IPv6 interfaces on the link process packets sent to this address. For example, a router sending an ICMPv6 Router Advertisement (RA) uses the all-nodes FF02::1 address. IPv6-enabled devices can then use the RA information to learn the links address information, such as prefix, prefix length and default gateway.
        - FF02::2 All-routers multicast group:
        This is a multicast group that all IPv6 routers join. A router becomes a member of this group when it is enabled as an IPv6 router with the ipv6 unicast-routing global configuration command. A packet sen to this group is received and processed by all IPv6 routers on the link or network. For example, IPv6-enabled devices send ICMPv6 Router Solicitation (RS) messages to the all-routers multicast address requesting an RA message.

###### Solicited-Node Multicast 

In addition to every unicast address assigned to an interface, a device has a special multicast address known as a Solicited-node multicast address. These multicast addresses are automatically created using a special mapping of the devices unicast address with the solicited-node multicast prefix FF02:0:0:0:0:1:FF00::/104

Solicited node multicast addresses are used for two essential IPv6 mechanisms, both part of NDP

* Address resolution: In this mechanism, which is equivalent to ARP in IPv4, an IPv6 device sends an NS message to a Solicited-node multicast address to learn the link-layer address of a device on the same link. The device recognizes the IPv6 address of the destination on that link but needs to know its data link address
* Duplicate address detection (DAD): As mentioned earlier, DAD allows a device to verify that its unicast address is unique on the link. An NS message is sent to the devices own solicited-node multicast address to determine whether anyone else has this same address 


#### Anycast 

An anycast address can be assigned to more than one device or interface. A packet sent to an anycast address is routed to the nearest device that is configured with the anycast address.

## Representing the IPv6 Address

#### Conventions for writing IPv6 addresses

IPv6 conventions use 32 hexadecimal numbers, organized into eight hextets of four hex digits seperated by colons, to represent a 128-bit IPv6 address.

To make things a little easier, two rules allow you to shorten what must be configured for an IPv6 address:

* Rule 1:- Omit the leading 0s in any given hextet 
* Rule 2:- Omit the all-0s hextets. Represent one or more consecutive hextets of all hex 0s with a double colon (::), but only for one such occurrence in a given address

This address has two locations in which one or more hextets have four hex 0s, so two main options work for abbreviating this address with the :: abbreviation in one of the locations. The following two options show the two briefest valid abbreviations:
    


