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

1. PC1 sends a packet destined for the Internet to R!, the default gateway
2. R1 forwards the packet to R2, as directed by its routing table
