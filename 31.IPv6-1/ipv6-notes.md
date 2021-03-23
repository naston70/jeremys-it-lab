## IPv6 Routing - OCG

Generally IPv6 uses the following principles in the same way as IPv4

- To be able to build and send IPv6 packets out an interface, end-user devices need an IPv6 address on that interface
- End user hosts need to know the IPv6 address of a default router, to which the host sends IPv6 packets if the host is in a different subnet
- IPv6 routers de-encapsulate and re-encapsulate each IPv6 packet when routing the packet
- IPv6 routers make routing decisions by comparing the IPv6 packets destination address to the routers IPv6 routing table; the matched route lists directions of where to send the IPv6 packet next

example:

PC1             = 2345::1
Default Gateway = 2345::2 (R1)

PC1 encapsulates the IPv6 packet and sends to the Default Gateway. R1 receives the incoming data-link frame and de-encapsulates the IPv6 packet from inside the frame, discarding the original data-link header and trailer. Once R1 knows to forward the IPv6 to the next hop, R1 adds a correct outgoing data-link header and trailer to the IPv6 packet, encapsulating the IPv6 packet.

The router must also see which type of packet is inside the frame. It does this by looking at the **protocol type** field in the data-link header. Usually IPv4 or IPv6. Also the router will use the IPv6 routing table, not the IPv4 routing table. 

## IPv6 Addressing Formats and Conventions

* IPv6 uses Hexadecimal
* Eight sets of four hex digits
* Each set, seperated by a colon :

#### Abbreviating and Expanding IPv6 Addresses


###### Abbreviating

Two basic rules govern the shortening or abbreviation of an IPv6 address:

* Inside each quartet of hex digits, remove the leading 0's
* Find any string of two or more consecutive quartets of all hex 0's and replace that set of quartets with a double colon - however this can only be used once

###### Expanding

Use two similar rules to reverse the logic of abbreviating:

* In each quartet, add leading 0's as needed until there are four hex digits
* If a double colon exists, count the quartets currently shown; the total should be less than 8, the replace the :: with 0000 until there is eight total quartets

###### Practice

Full                                     Abbreviated

2340:0000:0010:0100:1000:ABCD:0101:1010  2340:0:10:100:1000:ABCD:101:1010
30A0:ABCD:EF12:3456:0ABC:B0B0:9999:9009  30A0:ABCD:EF12:3456:ABC:B0B0:9999:9009
2222:3333:4444:5555:0000:0000:6060:0707  2222:3333:4444:5555::6060:707
3210:0000:0000:0000:0000:0000:0000:0000  3210::
210F:0000:0000:0000:CCCC:0000:0000:000D  210F::CCCC:0:0:D
34BA:000B:000B:0000:0000:0000:0000:0020  34BA:B:B::20
FE80:0000:0000:0000:DEDE:BEFF:FEEF:CAFE  FE80::DEDE:BEFF:FEEF:CAFE
FE80:0000:0000:0000:FACE:BAFF:FEBE:CAFE  FE80::FACE:BAFF:FEBE:CAFE

#### Representing the Prefix Length of an Address

The prefix length defines how many bits of the IPv6 address define the IPv6 prefix with a range from 0 to 128

#### Calculating the IPv6 Prefix

Each IPv6 prefix (subnet) has a number that represents the group. Starting with an IPv6 address and the prefix length a prefix can be found:
- Copy the first P bits
- Change the rest of the bits to 0

If the prefix length is a multiple of 4, hex digits can be used. **A prefix length that is a multiple of 4 means that each hex digit is either copied or changed to hex 0**

The process becomes:

- Identify the number of hex digits in the prefix by dividing the prefix length by 4
- Copy the hex digits determined to be in the prefix
- Change the rest of the hex digits to 0

*example:*
2001:0DB8:AAAA:0002:1234:5678:9ABC:DE01

The prefix length is 64. 64/4 = 16
The first 16 digits are copied and the last 16 changed to 0's
2001:0DB8:AAAA:0002:0000:0000:0000:0000

This address should then be abbreviated.

example: finding an IPv6 prefix from an Address/length value

| ADDRESS/LENGTH               | PREFIX             |
|------------------------------|--------------------|
| 210F::CCCC:BOBO:9999:9009/64 | 210F::/64          |
| 34BA:B:B:0:5555:0:6060:707/64| 34BA:B:B::/64      |
| 3124::DEAE:CAFE:FF:FFEO:1/64 | 3124:0:0:DEAE::/64 |
| 2BCD::FACE:BEFF:FEBE:CAFE/64 | 2BCD::/64          |



