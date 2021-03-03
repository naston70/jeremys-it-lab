# Subnetting

Answer to first example:

Divide 192.168.1.0/24 into 4 networks with minimum 45 hosts in each network

/26 provides closest match

HINT: Find the broadcast address of subnet 1. The next address is the network address of subnet 2. Repeat this for subnets 3 and 4.
														 (SN) (HOST)
Subnet 1 = 192.168.1.0/26 = 11000000. 10101000. 00000001. 00  000000
Broadcast                 = 11000000. 10101000. 00000001. 00  111111 = 63
Broadcast = 192.168.1.63/26

Meaning that subnet 2 network address is = 

Subnet 2 = 192.168.1.64/26 = 11000000. 10101000. 00000001. 01 000000 
Broadcast 				   = 11000000. 10101000. 00000001. 01 111111 = 127
Broadcast = 192.168.1.127/26

Subnet 3 = 192.168.1.128/26 = 11000000. 10101000. 00000001. 10 000000 = 128
Broadcast 				    = 11000000. 10101000. 00000001. 10 111111 = 191

Subnet 4 = 192.168.1.192/26 = 11000000. 10101000. 00000001. 11 000000 = 192
Broadcast 				    = 11000000. 10101000. 00000001. 11 111111 = 255


#### Example 2

Divide the 192.168.255.0/24 network into five subnets of equal size and identify the five subnets.


192			168			255			0
11000000.	10101000.	11111111.	0 0000000
									Borrowing 1 bit to make a /25 = making 2 subnets

To find the number of subnets we use 2**x (x being the number of borrowed bits)

Borrowing 2 bits = 2 ** 2 = 4 subnets = /26

Borrowing 3 bits can make 8 subnets (2**3 = 8) which is /27 or .224

192.168.255.0 is first network 11000000.10101000.11111111.000  00000
Broadcast 					 = 11000000.10101000.11111111.000  11111 = 31

S2 = 32 BC = 63
S3 = 64 BC = 91
S4 = 96 BC = 127
S5 = 128 BC = 159
S6 = 160 BC = 191
S7 = 192 BC = 223
S8 = 224 BC = 256

#### Example question 3

What subnet does host 192.168.5.57/27 belong to?

To find write out into binary

192
11000000.	10101000.	00000101.	00111001

A /27 borrows 3 bits (last octet) 001 11001 
Convert the host portion to 0's = 001 00000 = 32

IP 192.168.5.57 belongs to subnet 192.168.5.32/27


#### Example question 4

What subnet does host 192.168.29.219/29 belong to?

borrows 5 bits 11011 011    11011011
			   11011 000
			   192+8+16=216

192.168.29.219/29 belongs to subnet 192.168.29.216/29


## Subnets/ Hosts Class C

| Prefix Length | Num of Subnets | Num of Hosts |
|---------------|----------------|--------------|
| /25           | 2              | 126          |
| /26           | 4              | 62           |
| /27           | 8              | 30           |
| /28           | 16             | 14           |
| /29           | 32             | 6            |
| /30           | 64             | 2            |
| /31           | 128            | 0(2)         |
| /32           | 256            | 0(1)         |


## Subnetting Class B Networks

**The process of subnetting Class A, Class B and Class C networks is EXACTLY THE SAME**

Example 1:

Given the 172.16.0.0/16 network, you are asked to create 80 subnets for the company's various VLAN's. What prefix length should be used?

172			16			0			0
1010110.	00010000.	00000000.	00000000

To find subnets use 2**x, where x i the number of borrowed bits

How many bits are needed to borrow? 

2 bits = 4, 3 bits = 8, 4 bits = 16, 5 bits = 32, 6 bits = 64, **7 bits 128**

Need to borrow 7 bits /16 + 7 bits = /23 mask for 128 subnets

1st SUBNET:
ip     :	172			16			0			0
binary :	10101100.	00010000.	00000000.	00000000

Example 2

Given the 172.22.0.0/16 network, you are asked to create 500 subnets for the company's various VLAN's. What prefix length should be used?


