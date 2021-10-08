## IPv4 Subnetting

Subnets:

CIDR | Subnet Mask       | Addresses| Wildcard | 

/32  |= 255.255.255.255 =|= 1       |= 0.0.0.0
/31  |= 255.255.255.254 =|= 2       |= 0.0.0.1
/30  |= 255.255.255.252 =|= 4       |= 0.0.0.3
/29  |= 255.255.255.248 =|= 8       |= 0.0.0.7
/28  |= 255.255.255.240 =|= 16      |= 0.0.0.15
/27  |= 255.255.255.224 =|= 32      |= 0.0.0.31
/26  |= 255.255.255.192 =|= 64      |= 0.0.0.63
/25  |= 255.255.255.128 =|= 128     |= 0.0.0.127
/24  |= 255.255.255.0   =|= 256     |= 0.0.0.255


/23  |= 255.255.254.0   =|= 512     |= 0.0.1.255
/22  |= 255.255.252.0   =|= 1024    |= 0.0.3.255
/21  |= 255.255.248.0   =|= 2048    |= 0.0.7.255
/20  |= 255.255.240.0   =|= 4096    |= 0.0.15.255
/19  |= 255.255.224.0   =|= 8192    |= 0.0.31.255

#### Terminology

CIDR: Classless interdomian routing was developed to provide more granularity than legacy classful addressing; CIDR notation is expressed as /XX

VLSM: Variable-length subnet masks are arbitrary in length between 0 and 32 bits; CIDR relies on VLSMs to define routes.

