## First Exam

Exam Mode: Study Mode
Exam Bank: Random Exam
Result   : FAIL

#### Review of Incorrect Questions

1.
VLAN Hopping  - An attacker send double tagged 802.1Q frames over a trunk link
MAC Flooding  - An attacker sends traffic out every port on a switch
ARP Poisoning - Attacker intercepts traffic intended for another recipient
MAC Spoofing  - An attacker identifies itself using the address of another host
DHCP Spoofing - An attacker installs a rogue server on the network

4.
A host configuration with the Internet IP 172.16.12.10, subnet of 255.255.255.240 and default gateway of 172.16.12.1 is valid for hosts on 172.16.12.0/28. In this scenario, the /28 is CIDR = 255.255.255.240.

The /28 means 28 bits are used for the network portion of the address. 4 bits remain for host addresses (2**4) = 16 addresses are available on the subnet. 14 are usable. Therefore .10 is in the valid range 

5.
A company that uses a service providers infrastructure, programming tools and programming languages to develop and server cloud-based applications is an example of a Platform as a Service (PaaS)

6.
Routers are unable to form an adjacency because the OSPF areas must match. Although it is possible to configure multi-area OSPF, the OSPF areas on adjacent interfaces must match in order for two OSPF routers to form an adjacency

8.
Switches uses destination MAC addresses to make forwarding decisions.

9.
The ```show ip nat translations``` command displays mapping between internal and external IP addresses when NT is configured on a router. NAT translates between public and private IP addresses to enable hosts on a privately addresses network to access a public network such as the internet. By default NAT provides only a one-to-one mapping of addresses. If multiple hosts require simultaneous access of the public network, NAT must be configured to use either a pool of public IP addresses or NAT overloading.

The ```show ip nat translations``` command displays five fields of information for each NAT translation session:
* Protocol 
* Inside global - displays an IP that represents an inside host as seen by hosts on the outside network
* Inside local - displays the IP address configured on a host on the local network
* outside local - displays the IP address of a host on the outside network as seen from a host on the inside network 

10.
EIGRP supports unequal-cost load balancing.
OSPF only supports equal cost 
RIP only supports equal cost 
