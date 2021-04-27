## The Need for IPv6

* NAT breaks the end to end IP model
* Can cause issues with security and some applications

- Devices such as application layer firewalls, traversal servers and proxy servers can help with these issues
- A cleaner solution is for IP to support an addressing scheme big enough to give all devices in the world a publicly reachable address 
- IPv6 uses a 128 bit address instead of the 32 of IPv4

#### Dual Stack
* It doesn't have to be an either or situation
* In a 'dual stack implementation a network interface can have both an IPv4 and an IPv6 address at the same time'
* It can then communicate using either protocol
* Dual stack can be enabled long term to support both IPv4 and IPv6 applications or as an IPv4 to IPv6 transition strategy

#### The IPv6 Address format

- Written as X:X:X:X:X:X:X:X
- Each 'X' is a 16 bit hexadecimal field (0-9, A-F)
- IPv4 addresses are 32 bits long, written as x.x.x.x 
- Each segment is 8 bits so they are known as segments
- Each segment is 16 bits in an IPv6 address 

#### Address Shortening

* IPv6 addresses are long, they can be shortened to make things more convenient
* Address shortening is a standard convention and supported by all vendor devices
* Leading zeros in each field can be removed 
* 2001:0DB8:0000:0001:0000:0000:0000:0001 can be shortened to: 2001:0DB8:0:1:0:0:0:1
* Successive all zero field can also be shortened to '::'
* 2001:0DB8:0:1:0:0:0:1 can be written as 2001:0DB8:0:1::1
* Successive zero fields can be shortened only once in an address to avoid confusion 
* 2001:0:0:1:0:0:B can be shortened to
    - 2001::1:0:0:0:B or
    - 2001:0:0:1::B 
* Cant be shortened to 2001::1::B 

#### IPv6 Address Types

* **Global Unicast**
* **Unique Local**
* **Link Local**

#### Global Unicast

- Global Unicast Addresses are similar to IPv4 public addresses 
- They are assigned to an individual host and have global reachability
- They are assigned from the range 2000::/3

- Internet authorities assign blocks from the overall 2000::/3 range to organisations
- A common assignment for a company is a /48 block 
- A smaller or larger block can be assigned depending on company size

* IPv6 standards state that addresses assigned to individual hosts should use a /64 mask
* The IPv6 address is 128 bits so /64 splits it in half for the network and host portion of the address 
* X:X:X:X | X:X:X:X 

- If a company is assigned a /48 address by the Internet authorities and uses /64 host addresses, that leaves 16 bits the company can assign to its internal subnets
- ie, a company is assigned 2001:10:10::/48 by the Internet authorities, it can assign subnets 2001:10:10:0::/64 to 2001:10:10:FFFF::/64 to its internal network segments
- 16 bits = 65,535 possible subnets 
- Using a /64 for all network subnets including point to point links and loopback addresses can see wasteful but the official declaration is that the IPv6 address space is so large that it does not create a problem
- Using /63 every simplifies the addressing and enables the use of EUI-64 addresses 

#### Global Unicast Address Configuration

- Enable IPv6 routing first 
```
#ipv6 unicast-routing
#int f0/0
#ipv6 add 2001:db8:0:1::1/64
```

#### Broadcast and Multicast

- IPv4 supports broadcast to all hosts on 255.255.255.255
- Routers do not forward broadcast traffic so this stays on the local subnet
- IPv6 does not support broadcast traffic
- It does however support multicast to all hosts on the local subnet (ff02::1) which is functionally equivalent
- Many services which use broadcast 255.255.255.255 in IPv4 use more specific multicast addresses in IPv6 

#### Global Unicast Verification

Similar to normal command:
```
# show ipv6 interface brief
```

Can also use ping on IPv6 and trace route 

#### EUI-64 Addresses 

* A Cisco router can generate full IPv6 addresses for itself when given the interface and /64 network to use
* The host portion of the address is derived from the interfaces MAC address, which is guaranteed to be globally unique 
* A MAC address is a /48 address compared to the /64 host portion of the IPv6 address
* FF:FE is injected in the middle of the /48 MAC address to bring it up to 64 bits. Also the 7th bit is inverted

#### EUI-64 Address Configuration
```
#int f0/0
#ipv6 address 2001:db8:0:1::/64 eui-64
```

The host portion is entered and the rest is created from the eui-64 process.
- The router will borrow the MAC address from the first Ethernet port for non-Ethernet interfaces such as serial ports
- It is not recommended to use EUI-64 on router interfaces. It is better to use a memorable address 
- Useful for end hosts or use SLAAC

#### Unique Local and Link Local Addresses

- Unique Local Addresses are similar to IPv4 private addresses
- They are not publicly reachable
- They are assigned from the range FC00::/7
- Hosts should be assigned /64 addresses

#### Link Local Addresses
* Link local addresses are valid for communications on that link only
* They are assigned from the range FE80::/10 - FEB0::/10
* Host should be assigned /64 addresses 
- They can be used for communications which should not be forwarded beyond the local link, like routing protocol hello packets and updates
- They are mandatory on IPv6 enabled Cisco router interfaces
- They are automatically generated with EUI-64 addresses when an IPv6 interface is enabled
- The EUI-64 address can be overridden with manual configuration 
- Link local addresses are valid on the local link only so you can use the same address on multiple interfaces
```
#int 0/0
#ipv6 address fe80::1 link-local
#int 0/1
#ipv6 address fe80::1 link-local
```
This is useful for keeping more logical link-local addresses

#### Link Local Addresses Lab 
```
[enable ipv6 routing]
#ipv6 unicast-routing
#int f0/0
#ipv6 2001:db8:0:0::1/64
#no shutdown

#sh ipv6 int br 
```

Link local will be automatically generated, to override this address to make a more logical address:
```
#int f0/0
#ipv6 add fe80::1 link-local
```















