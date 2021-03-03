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

Borrow 9 bit = 512 subnets


Example 3:

Given the 172.18.0.0/16 network, you are asked to create 500 subnets for the company's various VLAN's. What prefix length should be used? Subnets should have same number of hosts.

Borrowing 8 bits = 256 subnets
8 host bits = 254 hosts

Example 4 

Whats subnet does host 172.25.217.192/21 belong to?

10101100.00011001.11011 001.11000000

10101100.00011001.11011 000.00000000

172.25.216.0/21


### QUIZ QUESTIONS

Question 1.
172.30.0.0/16 network. 100 subnets and 500 hosts. What prefix?

10101100.00011110.0000000 0.00000000

subs 128
hosts 2**9 - 2 = 510 hosts

Question 2.

What subnet does 172.21.111.201/20 belong to?

10101100.00010101.0110 1111.11001001

10101100.00010101.0110 000.00000000

172.21.96.0/21

Question 3

What is the broadcast of 192.168.91.78/26

11000000.10101000.01011011.01 001110

192.168.91.01111111 
= 127

Question 4

You divide 172.16.0.0/16 into 4 subnets of equal size. Identify the broadcast and network of the second subnet

4 subnets = 2**2 = 4 bits
2**12 hosts = 4096 -2 = 4094

As we borrowed 2 bits the prefix becomes /18. Take the 18th 0 and convert to a 1 to make: 172.16.64.0

10101100.00010000.01 000000.00000000 = 172.16.64.0 which is second subnet network address

To find the broadcast change the host portion to 1's 172.16.127.255


Question 5 

You need to divide 172.30.0.0/16 network into subnets of 1000 hosts each. How many subnets are you able to make?

To know how many subnets we can make we need to know how many bits we can borrow but to find out how many we can borrow we need to find out how many host bits we need for 1000 hosts.

1000 hosts = 2**10 1024-2 = 1022

10101100.00011110.000000 00.00000000 = /22

That means there are 6 borrowed bits. 
6 borrowed bits means 2**6 = 64 subnets