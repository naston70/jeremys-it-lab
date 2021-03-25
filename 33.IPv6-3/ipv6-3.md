## IPv6 - 3

#### The IPv6 Header

40 bytes in length

###### IPv6 Header - Version 
- Length 4 bits
- Indicates the version of IP that is used
- Fixed value of 6 (0b0110) to indicate IPv6

###### IPv6 Header - Traffic Class
* Length 8 bits
* Used for QoS to indicate high priority traffic
* For example, IP phone traffic will have a Traffic calls value which will give it priority over other traffic

###### IPv6 Header - Flow Label
- Length 20 bits
- Used to identify specific traffic flows (communications between a specific source and destination)

###### IPv6 Header - Payload Length
* Length 16 bits
* Indicates the length of the payload (the encapsulated Layer 4 segment) in bytes
* The length of the IPv6 header itself isn't included because its always 40 bytes

###### IPv6 Header - Next Header
- Length 8 bits
- Indicates they type of the 'next header' (header of the encapsulated segment) for example TCP or UDP
- Same function as the IPv4 headers 'Protocol' field

###### IPv6 Header - Hop Limit
* Length 8 bits
* The value in this field is decremented by 1 each router that forwards it. If it reaches 0, the packet is discarded
* Same function as the IPv4 headers 'TTL' field

###### IPv6 Header - Source / Destination
- Length 128 bits
- Contains the IPv6 addresses of the packets source and the packets intended destination


**Version = 4 bits,** **Traffic Class = 8 bits,** **Flow Label = 20 bits,** **Payload Length = 16 bits,** **Next Header = 8 bits,** **Hop Limit = 8 bits,** **Source / Destination = 128 bits**


## Solicited-Node Multicast Address

* An IPv6 solicited-node multicast address is calculated from a unicast address 
* ff02:0000:0000:0000:0000:0001:ff + [Last 6 hex digits of unicast address]
* 2001:0db8:0000:0001:0f2a:4fff:fe[a3:00b1]

#### NDP - Neighbor Discovery Protocol

- NDP is a protocol used with IPv6
- It has various functions, one of those being to replace ARP which is not used in IPv6
- The ARP-like function of NDP uses ICMPv6 and solicited-node multicast addresses to learn the MAC addresses of other hosts
- Two message types are used:
    1. Neighbor Solicitation (NS)
    2. Neighbor Advertisement (NA) (IPv6 type of ARP)
- Another function of NDP allows hosts to automatically discover routers on the local network. Two messages are used for this process:
    1. Router Solicitation (RS) = ICMPv6 Type 133 
        * -> sent to multicast address FF02::2 (all routers)
        * -> asks all routers on the local link to identify themselves
        * -> sent when an interface is enabled / host is connected to the network
    
    2. Router Advertisement (RA) = ICMPv6 Type 134
        * Sent to multicast F202::1 (all nodes)
        * The router announces its presence, as well as other information about the link
        * These messages are sent in response to RS messages
        * They are also sent periodically, even if the router hasn't received an RS

## SLAAC 

- Stands for Stateless Address Auto Configuration
- Hosts use the RS/RA messages to learn the IPv6 prefix of the local link and then automatically generate an IPv6 address
- Using the ```ipv6 address prefix eui-64``` command you need to manually enter the prefix
- Using the ```ipv6 address autoconfig``` command, you don't need to enter the prefix. The device uses NDP to learn the prefix used on the local link.
- The device will use EUI-64 to generate the interface ID or it can be randomly generated dependent on the device

#### Duplicate Address Detection

- DAD allows hosts to check if other devices on the local link are using the same IPv6 address
- Any time an IPv6 enabled interface initializes, or an IPv6 address is configured on an interface, it performs DAD
- DAD uses 2 messages: NS and NA (Neighbor Solicitation & Neighbor Advertisements)
- The host will send an NS to its own IPv6 address. If there is no reply, it knows the address is unique
- If it gets a reply, it means another host on the network is already using the address

## IPv6 Static Routing

* IPv6 routing works the same as IPv4 routing
* However the two processes are seperate on the router, with two seperate routing tables 
* IPv4 routing is enabled by default
* IPv6 routing is disabled by default and must be enabled with ```ipv6 unicast-routing``` 
* If IPv6 router is disabled, the router will be able to send and receive IPv6 traffic but will not route IPv6 traffic 

- A connected *network route* is automatically added for each connected network
- A local *host route* is automatically added for each address configured on the router
- Routes for link-local addresses are not added to the routing table

#### IPv6 Static Route Command

```
ipv6 route dst/prefix-length {next-hop | exit-interface [next-hop]} [ad]
```

**Directly attached** static route: Only the exit interface is specified.
```ipv6 route dst/prefix-length exit-interface
```
```R1(config)#ipv6 route 2001:db8:0:3::/64 g0/0
```

**Recursive** static route: Only the next hop is specified.
```ipv6 route dst/prefix-length next-hop
```
```R1(config)#ipv6 route 2001:db8:0:3::/64 2001:db8:0:12::2
```

**Fully specified** static route: Both the exit interface and next hop are specified 
```ipv6 route dst/prefix-length exit-interface next-hop
```
```R1(config)#ipv6 route 2001:db8:0:3::/64 g0/0 2001:db8:0:12::2
```

#### example routes

**network route**: 
```
R1(config)#ipv6 route 2001:db8:0:3::/64 2001:db8:0:12::2
```

**host route**
```
R1(config)#ipv6 route 2001:db8:0:3::/128 2001:db8:0:23::2
```

**default route**
```
R1(config)#ipv6 route ::/0 2001:db8:0:23::1
```


## IPv6 Config Lab Commands

Enable IPv6 on a router:
```
#ipv6 unicast-routing
```
Use SLAAC to configure IPv6 addresses:
