## NAT

Exam Topics:

- Configure and verify inside source NAT using static and pools

#### NAT Concepts:

NAT, defined in RFC 3022 has many uses. Its key use is to conserve IPv4 addresses by allowing networks to use private IPv4 addresses. NAT translates nonroutable, private, internal addresses into routable public addresses. NAT also has the benefit of hiding internal IPv4 addresses from outside networks.

A NAT-enabled device typically operates at the border of a stub network. 
In NAT terminology, the *inside network* is the set of networks that are subject to translation. The *outside network* is all other addresses.

- Inside local address: Most likely a private address
- Inside global address: A valid public address that the inside host is given when it exits the NAT router.
- Outside global address: A reachable IPv4 address assigned to a host on the internet
- Outside local address: The local IPv4 address assigned to a host on the outside network.

###### A NAT example

1. PC1 sends a packet destined for the Internet to R2, the default gateway
2. R1 forwards the packet to R2, as directed by its routing table
3. R2 refers to its routing table and identifies the next hop as the ISP router. It then checks to see whether the packet matches the criteria specified for translation. R2 has an ACL that identifies the inside network as a valid host for translation. Therefore it translates an inside local IPv4 address to an inside global IPv4 address. It stores this mapping of the local address to global address in the NAT table 
4. R2 modifies the packet with the new source IPv4 address and sends it to the ISP router
5. The packet eventually reaches its destination which then sends its reply to the inside global address
6. When R2 receives replies from the destination, it consults the NAT table to match the inside global address to the correct inside local address. R2 then modifies the packet, inserting the inside local address as the destination address ad sending to R1
7. R1 receives the packet and forwards it to PC1

#### Dynamic and Static NAT

The two types of NAT translation are as follows:
- **Dynamic NAT**: Uses a pool of public addresses and assigns them on a first-come, first-served basis or reuses an existing public address configured on an interface. When a host with a private IPv4 address requests access to the internet, dynamic NAT chooses an IPv4 address from the pool that another host is not already using. Instead of using a pool, dynamic NAT can be configured to overload an existing public address configured on an interface
- **Static NAT**: Uses a one-to-one mapping of local and global addresses. These mappings remain constant. Static NAT is particularly useful for web servers or hosts that must have a consistent address that is accessible from the Internet

#### NAT Overload

NAT overloading (PAT) maps multiple private IPv4 addresses to a single public IPv4 address or a few addresses. When a response comes back from the outside, source port numbers determine the correct client for the NAT router to translate the packets.

1. PC1 and PC2 send packets destined for the internet
2. When the packets arrive at R2, NAT overload changes the source address to the inside global IPv4 address and keeps a record of the assigned port numbers to identify the client from which the packets originate
3. R2 updates its NAT table. R2 then routes the packets to the Internet
4. When the webs server replies, R2 uses the destination source port to translate the packet to the correct client

NAT overload attempts to preserver the original source port. However, if this source port is already used, NAT overload assigns the first available port number, starting from the beginning of the appropriate port group 0-511, 512-1023 or 1024-6535

#### NAT Benefits

Using NAT offers the following benefits:
* NAT conserves registered IPv4 address space because, with NAT overload, internal hosts can share a single public IPv4 address for all external communications
* NAT increase the flexibility of connections to the public network. Multiple pools, backup pools and load-balancing pools can be implemented to ensure reliable public network connections
* NAT allows the existing scheme to remain while supporting a new public addressing scheme. This means that an organization can change ISPs without needing to change any of its inside clients
* NAT provides a layer of network security because private networks do not advertise their inside local addresses outside the organization. However, the phrase, *NAT firewall* is misleading; NAT does not replace a firewall

#### NAT Limitations
