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

In most cases, network engineers configure the IPv6 addresses of router interfaces so that the addresses do not change until the engineer changes the router configuration. However, routers can be configured to use dynamically learned IPv6 addresses. Useful for routers using DSL and cable technologies



