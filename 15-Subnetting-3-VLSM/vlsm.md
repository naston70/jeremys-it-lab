# Subnetting Class A Networks


Given 10.0.0.0/8. You must create 2000 subnets

00001010.00000000.000 00000.00000000

2**11 = 2048
2**13-2 = 8190 hosts
/19 

Question 2

PC1 has IP 10.217.182.223/11

Identify:
1) Network Address:
2) Broadcast:
3) First Usable:
4) Last Usable:
5) Number of hosts:

00001010.110 11001.10110110.11011111 /11

00001010.110 00000.00000000.00000000

10.192.0.0
10.192.0.1
10.192.255.255
10.192.255.254
2**21 -2 = 2097150

## Variable-Length Subnet Masks

- VLSM is the process of creating subnets of different sizes, to make your use of network addresses more efficient
- VLSM can be more complicated but simple if steps are followed correctly.

						 192.168.1.0/24
Tokyo LAN A 											Toronto LAN A
110 hosts 												29 Hosts
					Point-to-Point Connection			
Tokyo LAN B 											Toronto LAN B
8 Hosts 												45 Hosts

#### VLSM - STEPS

1) Assign the largest subnet at the start of the address space
2) Assign the second largest
3) Continue until all hosts are assigned

From the above diagram

1 = Tokyo LAN A - 110
2 = Toronto LAN B - 45
3 = Toronto LAN A - 29  
4 = Tokyo LAN B - 8
5 = PtP - 5

192.168.1.0/24

11000000.10101000.000000001.0 0000000

NET ID: 192.168.1.0 /25
NET BC: 192.168.1.127
1st IP: 192.168.1.1
Last  : 192.168.1.126
total hosts: 126

Toronto LAN B /26
11000000.10101000.00000001.10 000000
							  111111
NET ID: 192.168.1.128/26
NET BC: 192.168.1.191/26
1st   : 192.168.1.129/26
Last  : 192.168.1.190/26
Hosts : 62

Toronto LAN A 
11000000.10101000.00000001.110 00000
NET ID: 192.168.1.192/27
NET BC: 192.168.1.223/27
1st   : 192.168.1.193/27
Last  : 192.168.1.222/27
Hosts : 32

Toronto LAN B
11000000.10101000.00000001.1110 000
								111
NET ID: 192.168.1.224/28
NET BC: 192.168.1.239/28
1st   : 192.168.1.225/28
Last  : 192.168.1.238/28
Hosts : 14

PtP Network - requires 2 hosts

Net ID: 192.168.1.240/30
Net BC: 192.168.1.243/30
1st   : 192.168.1.241/30
Last  : 192.168.1.242/30
Hosts : 2
