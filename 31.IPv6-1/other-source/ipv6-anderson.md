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








