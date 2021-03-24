## IPv6 - 2

#### EUI - CONFIGURING IPv6 ADDRESSESS WITH EUI-64

- EUI stands for Extended Unique Identifier
- EUI is a method of converting a MAC address into a 64-bit interface identifier
- The interface identifier can then become the 'host portion' of a /64 IPv6 address
- How to convert the MAC address:
    1. Divide the MAC address in half eg 1234 5678 90AB becomes 123456 | 7890AB
    2. Insert FFFE in the middle: 1234 56FF FE78 90AB
    3. Invert the 7th bit (4 bit per number) 0001 0010 0011 1000 (1234)
    4. 7th bit is the 2 (0010) which becomes 0000 when inverted = 1034
    5. 1034 56FF FE78 90AB it will be added on to the prefix to make the complete IPv6 address

Practice converting a MAC address into an EUI-64 Interface Identifier:
|MAC ADDRESS                |EUI-64 Interface Identifier|
|---------------------------|---------------------------|
| 782B CB AC 0867           |7A2B CBFF FEAC 0867        |
| 0200 4C 4F 4F50           |0000 4CFF FE4F 4F50        |
| 00FF 6B A6 F456           |02FF 6BFF FEA6 F456        |

**EUI-64 allow routers to automatically generate an IPv6 address by expanding the MAC address to a 64 bit interface ID, which is then combined with the specified IPv6 address prefix**

Its a method of automatically generating an IPv6 address using a prefix and MAC

#### Global Unicast Addresses

* Global unicast IPv6 addresses are public addresses which can be used over the Internet
* The must be registered and are expected to be globally unique
* Defined as all addresses which aren't reserved for other purposes

2001:0DB8:8B00:0001::1/64

First 3 are the 48-bit 'global routing prefix'
4th is the 'subnet identifier'
Last 16 = 'interface identifier', the host portion of the address

#### Unique Local Addresses

* Unique local IPv6 addresses are private addresses which cannot be used over the Internet
* Do not need to be registered
* Requires the 8th bit to be set to 1 so the first two digits must be FD
* The global ID should be unique so that addresses don't overlap in merges

**FD**45:93AC:8A8F:0001:0000:0000:0000:0001/64

FD indicates a unique local address (8-bits)
The 40-bit 'global ID' should be randomly generated
The next 16 bits (0001) are the subnet identifier
Totals 64 bits of the network prefix
Next 64 bits is the host portion 

#### Link Local Addresses

 * Link-local IPv6 addresses are automatically generated on IPv6-enabled interfaces
 * Uses the address block FE80, only link local address will begin with FE8
 * The interface ID is generated using EUI-64 rules
 * *Link-Local* means these addresses are used for communication within a single subnet. Routers will not route packets with a link-local destination address.
 * Uses of link-local addresses:
     - routing protocol peerings (OPSFv3 for neighbor adjacencies)
     - next-hop addresses for static routes
     - NDP (IPv6 replacement for ARP)

#### Multicast Addresses

- **Unicast** is one to one
- **Broadcast** is one-to-all
- **Multicast** addresses are one-to-many

* IPv6 uses the range FF00::/8 for multicast
* **IPv6 doesn't use broadcast,** there is no broadcast address in IPv6

## MULTICAST ADDRESS IPv6 and IPv4

| Purpose           | IPv6    | IPv4       |
|-------------------|---------|------------|
| All nodes/ hosts  | FF02::1 | 224.0.0.1  |
| All routers       | FF02::2 | 224.0.0.2  |
| All OSPF routers  | FF02::5 | 224.0.0.5  |
| All OSPF BRs/BDRs | FF02::6 | 224.0.0.6  |
| All RIP routers   | FF02::9 | 224.0.0.9  |
| All EIGRP routers | FF02::A | 224.0.0.10 |

IPv6 defines multiple scopes which indicate how far the packet should be forwarded

- **Interface-local** (FF01): The packet doesn't leave the device. Can be used to send traffic to a service within the local device
- **Link-local** (FF02): The packet remains in the local subnet. Routers will not route the packet between subnets
- **Site-local** (FF05): The packet can be forwarded by routers. Should be limited to a single physical location
- **Organization-local** (FF08): Wide scope than site-local
- **Global** (FF0E): No boundary, possible to be routed over the Internet

#### Anycast IP Addresses

* Anycast is a new feature of IPv6
* Anycast is one-to-one-of-many
* Multiple routers are configured with the same IPv6 address
    - They use a routing protocol to advertise the address
    - When hosts send packets to that destination, routers wil forward it to the nearest router configured with that IP (using routing metric)
* There is no specific range for anycast addresses. Use a regular address and specify it as anycast
```
R1(config-if)#ipv6 address 2001:db8:1:1::99/128 anycast
```





