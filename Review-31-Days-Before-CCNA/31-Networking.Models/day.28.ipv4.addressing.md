## IPv4 Addressing

Exam Topics:

- Configure and verify IPv4 addressing and subnetting 
- Describe the need for private IPv4 addressing 

#### IPv4 Addressing 

An IP address consists of two parts:

- Network ID: The higher order, left most, bits specify the network address component of the address 
- Host ID: The low-order, rightmost bit specify the host address components of the address 

###### Classes of Addresses

From the beginning, IPv4 was designed with class structure: Class A,B,C,D and E. Class D us used for multicasting addresses and Class E is reserved for experimentation. Classes A,B and C are assigned to network hosts. To provide a hierarchical structure, these classes are divided into network and host portions. The high-order bits specify the network ID and the low-order bits specify the host ID. 

In a classful addressing scheme, devices that operate at Layer 3 can determine the address class of an IP address from the format of the first few bits in the first octet. Initially, this was important so that a networking device could apply the default subnet mask for the address and determine the host address. 

###### Purpose of the Subnet Mask

Subnet masks are always a series of 1 bits followed by a series of 0 bits. The boundary where the series changes from 1's to 0's is the boundary between the network and the host. This is how a device that operates at Layer 3 determines the network address for packet: by finding the bit boundary where the series of 1 bits ends and the series of 0 bit begins. The bit boundary for default subnet masks breaks on the octet boundary. Determining the network address for an IP address that uses a default mask is easy.

Say that a router receives a packet destined for 192.168.1.51 by ANDing the IP address and the subnet mask, the router determines the network address for the packet. By the ANDing rule, a 1 AND a 1 equals 1. All other possibilities equal 0.

192.168.1.51
11000000.10101000.00000001.00110011

255.255.255.0
11111111.11111111.11111111.00000000

192.168.1.0
11000000.10101000.00000001.00000000

#### Private and Public IP Addressing 

RFC 1918 eased the demand for IP addresses by reserving the following addresses for use in private internetworks:

* Class A: 10.0.0.0/8 (10.0.0.0 - 10.255.255.255)
* Class B :172.16.0.0/12 (172.16.0.0 - 172.31.255.255)
* Class C: 192.168.0.0/16 (192.168.0.0 - 192.168.255.255)

If you are addressing a nonpublic intranet, these private addresses are normally used instead of globally unique public addresses. This provides flexibility in your addressing design. Any organization can take full advantage of an entire Class A address. Forwarding traffic to the public Internet requires translation to a public address using NAT. But by overloading an Internet-routable address with many private addresses, a company needs only a handful of public addresses. 

#### Subnetting in Four Steps

- Step 1. Determine how many bits to borrow, based on the host requirements
- Step 2. Determine the new subnet mask 
- Step 3. Determine the subnet multiplier
- Step 4. List the subnets, including the subnetwork address, host range and broadcast range.

Eg, given the network address 192.168.1.0 and mask 255.255.255.0 or 192.168.1.0/24. You need 30 hosts per network within as man subnets as possible.

###### Determine How Many Bits to borrow

To determine the number of bits you can borrow, you must first know how many bits you have to start with. (32 - 24 = 8)

Because our requirement specifies 30 host addresses per subnet, we need to first determine the minimum number of host bits to leave. The remaining bits can be borrowed:

Host bits = Bits borrowed + Bits Left. 

2** X - 2 = number of hosts. 

This will leave 3 remaining bits, 2 ** 3 = 8

0 = 00100000 = .0
1 = 01000000 = .32
2 = 01100000 = .64
3 = 10000000 = .96
4 = 10100000 = .128
5 = 10100000 = .160
6 = 11000000 = .192
7 = 11100000 = .224

###### Determine the New Subnet Mask

The 3 borrowed bits are added to the existing 24 to create a new subnet mask of /27. 255.255.255.224

###### Determine the Subnet multiplier

- Method 1: subtract the last nonzero octet of the subnet mask from 256. ie 256 - 224 = 32
- Method 2: the decimal value of the last bit borrowed is the subnet multiplier. (in this example the 32 bit was borrowed)

###### List the Subnets, Host Ranges and Broadcast Addresses 

Subnet 0 | 192.168.1.0  | 192.168.1.1 - .30  | broadcast 192.168.1.31
Subnet 1 | 192.168.1.32 | 192.168.1.33 - .62 | broadcast 192.168.1.63
Subnet 2 | 192.168.1.64 | 192.168.1.65 - .94 | broadcast 192.168.1.95

###### Subnetting Example 1

Subnet 172.16.0.0/16 to provide at least 80 hosts per subnet with as many subnets as possible:

Step 1: 2**7 - 2 = 126
16 - 7 = 9 bits for subnets 2**9 = 512

Step 2: Original /16 + 9 = /25 or 255.255.255.128

Step 3: Subnet multiplier is 128, 256 - 128 = 128

###### Subnetting Example 2

Subnet 172.16.0.0/16 to provide 80 subnets 

1. There are 16 host bits. Borrow 7 to make 2**7 = 128 subnets, this leaves 9 bits for host addresses 2**9 - 2 = 510 hosts per subnet 

2. Subnet mask is /16 + 7 bits = /23 so 255.255.254.0

3. Subnet multiplier is 2, which can be found as 256 - 254, or the 2 bit is the last borrowed bit

###### Subnetting Example 3 

Subnet 172.16.10.0/23 to provide at least 60 host addresses with as many subnets as possible

1. 2**6 - 2 = 62 
There are 9 host bits, leave the 6 for host addresses and borrow the first 3 bits to create as many subnets as possible 
2**3 = 8 subnets 

2. Original subnet of /23 + 3 = /26 or 255.255.255.192

3. 256 - 192 = 64

###### VLSM

With VLSM, you can customize subnets to fit into your network. Subnetting works the same way. You just have to do it more than once to complete your addressing scheme. To avoid overlapping address space, start with the largest host requirement, create a subnet for it and then continue with the next largest requirement.

Given the address space 172.30.4.0/22 apply an addressing scheme that conserves the most addresses for future growth. 
Network requirements:
LAN1 = 60 hosts
LAN2 = 10 hosts
LAN3 = 250 hosts
LAN4 = 100 hosts

We need five subnets, four LAN subnets and one WAN subnet. Starting with the largest host requirement on LAN3, begin subnetting the address space. 

To satisfy the 250 host requirement, we leave 8 host bits (2**8 - 2 = 254). There are 10 host bits we borrow the other two to create the first subnets (2**2 = 4) The starting subnet mask is /22, turn on the next 2 bits to equal /24 or 255.255.255.0

* Subnet 0 = 172.30.4.0/24
* Subnet 1 = 172.30.5.0/24
* Subnet 2 = 172.30.6.0/24
* Subnet 3 = 172.30.7.0/24

Assigning Subnet 0 to LAN 3, we are left with three /24 subnets, continuing with the process, LAN 4 is the next largest requirement.

LAN4 
2**7 = 128 - 2 = 126 hosts 
8 bits - 7 = 1 bit borrowed, 2**1 = 2. SO 2 subnets 
Subnet mask = /24 + 1 = 255.255.255.128
Multiplier is 128
The two subnets are:
173.30.5.0/25
172.30.5.128/25

LAN1
As the first subnet satisfies the previous LAN, the second subnet 172.30.5.128/25 can be further subnetted.

2**6 = 64 - 2 = 62
7 bits - 1, 2**1 = 2
The starting subnet mask is /25 + 1 = /26 or 255.255.255.192
256 - 192 is the multiplier 64
Subnets are:
172.30.5.128/26
172.30.5.192/26

Final LAN2 needs 10 hosts