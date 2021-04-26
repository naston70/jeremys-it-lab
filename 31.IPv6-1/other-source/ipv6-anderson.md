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







