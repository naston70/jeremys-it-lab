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

IPv6 and 4 both use the same concepts about where a subnet is needed:
- one for each VLAN
- one for each point-to-point WAn connection

#### Mechanics of Subnetting IPv6 Global Unicast Addresses

        [P Bits]        [S Bits]        [I Bits]
|Global Routing Prefix|    Subnet      |Interface ID|

|--------- P + S + I = 128 -----------|

Unlike IPv4, IPv6 has no concept of address classes, so no preset rules determine the prefix length of the global routing prefix. However the assignment of the Global Routing Prefix includes both the prefix and prefix length. 

example: 
2001:0db8:1111:0001:0000:0000:0000:0001 - global unicast IPv6 address

* Company was assigned 2001:0db8:1111 with a /48 prefix length
* A subnet field of 16 bits allows for 2**16 subnets (0001)
* The usual 64-bit interface ID is also used

**Listing the IPv6 Subnet Identifier:**

IPv6 needs to identify each IPv6 subnet with some kind of a subnet identifier or subnet ID. The subnet ID or prefix ID is then listed in the IPv6 routing tables along with the prefix length

**Assigning Addresses to Hosts in a Subnet:**

Once the IPv6 subnets have been planned an engineer can then plan and implement the individual IPv6 addresses. Addresses must be unique and the subnet ID itself cannot be used.

The process of assigning IPv6 Addresses to interfaces works similarly to IPv4. Addresses can be configured statically, along with the prefix length, default router and DNS IPv6 addresses. Alternatively, hosts can learn these settings dynamically, using either DHCP or SLAAC (Stateless Address Autoconfiguration)


## UNIQUE LOCAL UNICAST ADDRESSES

Unique local unicast addresses act as private IPv6 addresses. They have many similarities with global unicast, particularly in how to subnet. Biggest difference is the number available (unique local begin with hex FD), also they are registered with any authority and can be used by multiple organizations.

###### Rules of Unique Local Addresses:

* Use **FD** as first two hex digits
* Chose a unique 40-bit global ID
* Append the global ID to FD to for a 48-bit prefix, used in all the addresses
* Use the next 16 bits as the subnet field
* Use the remaining 64 bits for interface ID

[[(8 bits) FD|(40 bits) Global ID|(16 bits) Subnet|(64 Bits)Interface ID]]

###### Subnetting with Unique Local IPv6 Addresses:

The only difference to subnetting a global unicast and unique local unicast is the creation of the prefix locally and the 40 bits made + FD

###### The Need for Globally Unique Local Address:


