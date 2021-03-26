## IPv6 Configuration

Cisco routers give two options for static configuration of IPv6 addresses. In one configuration is the full 128-bit address or in the other, configuration of a 64-bit prefix and let the router derive the second half of the address.

#### Configuring the Full 128-bit Address

To statically configure the full 128-bit unicast address, (global or unique local) the router needs the ```ipv6 address [address/prefix-length]``` interface subcommand on the interface. It can be abbreviated or the full 32 digit hex address. 

###### Configuring a Static IPv6 Address:
```
ipv6 unicast-routing

int g0/0
ipv6 address 2001:db8:1111:1::1/64
int g0/0/0
ipv6 address 2001:db8:1111:4::1/64
```

#### Enabling IPv6 Routing

On Cisco routers IPv6 routing is disabled by default. The single command ```ipv6 unicast-routing``` will enable it.

A router must enable IPv6 globally and enable IPv6 in the interface before the router will attempt to route IPv6 packets in and out an interface.

#### Verifying IPv6 Configuration

```
show ipv6 interface brief
```
shows address info but not prefix length info
```
show ipv6 interface
```
gives details of IPv6 interface settings

#### Generating a Unique Interface ID using EUI-64 (Extended Unique Identifier)

IPv6 follows the same general model as IPv4 for which types of devices typically use static, predefined addresses and which use a dynamically learned address. Typically, in IPv4 a router would have a static IP and an end host learn its address from DHCP. The same applies to IPv6.

IOS supports two methods to configure a stable IPv6 address. The first method by using the ```ipv6 address``` command to define the full 128-bit address and the second by using the same ```ipv6 address``` command but the command configures only the 64-bit IPv6 prefix for the interface and the router automatically generates a unique interface ID.

**EUI-64 method:**
    1. Split the 6-byte MAC address in two halves
    2. Insert FFEE in between the two, making the interface ID now have a total of 16 hex digits
    3. Invert the seventh bit of the interface ID 

Configuring a router interface to use EUI-64:
```ipv6 address [address][prefix-length] eui-64
```

The ```eui-64``` keyword tells the router to find the interface MAC address and to do the EUI-64 conversion math to find the interface ID

#### Dynamic Unicast Address Configuration

In most cases, network engineers configure the IPv6 addresses of router interfaces so that the addresses do not change until the engineer changes the router configuration. However, routers can be configured to use dynamically learned IPv6 addresses. Useful for routers using DSL and cable technologies.

Cisco routers support two ways for the router interface to dynamically learn an IPv6 address to use:

- Stateful DHCP
- Stateless Address Autoconfiguration

Both methods use the familiar ```ipv6 address``` command, neither option configures the actual IPv6 address instead the commands configure a keyword which tells the router which method to use to learn its IPv6 address.
```
ipv6 address dhcp
ipv6 address autoconfig
```

#### Special Addresses Used by Routers

After the ```ipv6 unicast-routing``` global config command is set, which enables the function of IPv6 routing, the addition of a unicast IPv6 address on an interface causes the router to do the following:

* Gives the interface a unicast IPv6 address
* Enables the routing of IPv6 packets in/out that interface
* Defines the IPv6 prefix (subnet) that exists off that interface
* Tells the router to add a connected IPv6 route for that prefix, to the routing table, when that interface is in the up/up state

Whilst IPv6 and IPv4 share many similarities IPv6 also has a number of functions not present in IPv4. Often these additional features use other IPv6 addresses, many of which are multicast.

#### Link Local Addresses

IPv6 uses link-local addresses as a special kind of unicast IPv6 address. These addresses are not used for normal IPv6 packet flows that contain data for applications. Instead these addresses are used for routing and by some overhead protocols.

###### Link Local Address Concepts

**IPv6 defines rule so that packets sent to any link-local address should not be forwarded by any router to another subnet.** As a result, several IPv6 protocols make use of link-local addresses when the protocols messages need to stay within the local LAN. NDP for example, uses link-local addresses.

Routers also use link-local addresses as the next-hop IP addresses in IPv6 routes. IPv6 hosts also use default gateway / router concepts, like IPv4 but instead of the router address being in the same subnet, hosts refer to the routers link-local address. 
```
show ipv6 route
```
This command lists the link-local address of the neighboring router rather than the global unicast or local unicast address.

Key facts about Link-Local Addresses:

- **Unicast(not multicast)**: Link-Local addresses represent a single host, and packets sent to a link-local address should be processed by only that one IPv6 host
- **Forwarding scope is the local link only:** Packets sent to a link-local address do not leave the local data link because routers do not forward packets with link-local destinations
- **Automatically generated:** Every IPv6 host interface (and router interface) can create its own link-local address automatically, solving some initialization problems for hosts before they dynamically learn their IP
- **Common uses:** Link-local addresses commonly used for overhead protocols to stay on one subnet and as next-hop addresses on IPv6 routes

#### Creating Link-Local Addresses on Routers

**All link-local addresses must start with the same prefix, FE80:0:0:0**

The second half can be formed using EUI-64 rules, randomly generated or configured

IOS creates a link-local address for any interface that has configured at least one other unicast address using the ```ipv6 address``` command. 

IOS can either automatically create the link-local address or it can be configured. IOS choose the link-local address based on the following rules:

* If configured, the router uses the value in the ```ipv6 address {address} link-local``` interface subcommand. Must be from FE80::/10 range.
* If not configured, IOS calculates the link-local using EUI-64 rules.

#### Routing IPv6 with only Link-Local Address on an Interface

The 4 ```ipv6 address``` commands above are:

Static configuration of a specific address:
```
ipv6 address {address / prefix-length}
```

Static configuration of a specific prefix and prefix length and the router generating the interfac ID using EUI-64
```
ipv6 address {prefix / prefix-length} eui-64
```

Dynamic of the address and prefix using DHCP:
```
ipv6 address dhcp
```

Dynamic learning of prefix and prefix length with the router using SLAAC for the interface ID calculation:
```
ipv6 address autoconfig
```

To complete the list:
``` 
ipv6 enable
```

This command makes sense when understanding some links, particularly WAN links, do not need global unicast addresses. 

End hosts do not need to know a WAN links IPv6 addresses in order to send a packet to another host. They may need to know the routers LAN IPv6 addresses, for a default gateway but not WAN interface addresses.
Additionally, the routers do not need to have global unicast (or unique local) addresses on the WAN links for routing to work. IPv6 routing protocols use link-local addresses as the next-hop address when dynamically building IPv6 routes. Static routes can also use link-local addresses for next-hop addresses.

Creating a WAN link with no global unicast or unique local address can work. As a result there is no need to assign an IPv6 subnet to each WAN link. Then to configure the WAN interfaces, use the ```ipv6 enable``` command, enabling IPv6 and giving each interface a generated link-local IPv6 address -  on both ends

#### IPv6 Multicast Addresses



