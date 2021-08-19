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

NAT ov
