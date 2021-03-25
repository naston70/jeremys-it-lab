## IPv6 Addressing and Subnetting (OCG)

**Global Unicast** is the public IPv6 address space, unique across the globe

**Unique Local** similar to IPv4 private address space

#### The IPv6 Global Routing Prefix

Prefix = 'all addresses whose first 12 hex digits are xxxx:xxxx:xxxx'

Global Unicast addresses make up the majority of the IPv6 address space. 

Some types of IPv6 Address:

|Address type     |    First Hex Digits       |
|-----------------|---------------------------|
|Global Unicast   | All not otherwise reserved|
|Unique Local     | FD                        |
|Multicast        | FF                        |
|Link Local       | FE80                      |


#### IPv6 Subnetting Using Global Unicast Addresses

After an enterprise receives a block of reserved global unicast addresses, or a global routing prefix, the company will need to sub-divide that large block into smaller subnets
Usually a /64 prefix length is used

#### Deciding Where IPv6 Subnets are Needed



