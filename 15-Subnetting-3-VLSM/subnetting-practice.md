# Subnetting Practice

####| subnettingquestions.com | subnetting.org | subnettingpractice.com |


1) First valid host: 192.168.3.147/26

11000000.10101000.00000011.10 010011

192.168.3.128 = BC + 1 for 1st Valid

2) What valid host range is the IP 192.168.153.183/25 a part of?
11000000.10101000.10011001.1 0111011
192.	 168	  153	  .1 0000000 = 192.168.153.128 - 254

3) Broadcast Address of network: 

192.168.247.128 255.255.255.224 = /27
11000000.10101000.11110111.100 11111

192.168.247.159

4) Range of 172.18.71.121/25

10101100.00010010.01000111.0 1111001
172.18.71.0
172.18.71.127

Need to minus 1 from the broadcast and add one to the network to find the range IPs


5) Last valid host on the subnet 172.19.84.0/22
10101100.00010011.010101 11.00000000 /22

172.19.84.0
172.19.87.254

6)Subnet of host 192.168.236.117/29 

11000000.10101000.11101100.01110 011

192.168.236.112

7) Host range 172.25.119.129/23
11001010.00011001.01110101.10000001
11001010.00011001.0111010 1.10000001
172.25.118.1
172.25.119.254

8)Last host on subnet: 172.29.244.0 /22
111101 11 .255 minus 1 for host
172.29.247.254

9)Valid host range 172.24.247.5 /23:
172.24.1111011 0.0
172.24.246.0 + 1 
172.24.247.255 - 1

10) Which subnet does 172.31.178.1 /23

172.31.1011001 0.1
172.31.178.0

11) Valid range for 172.30.96.195 /23

172.30.0110000 0.195

172.30.96.0 + 1
172.30.97.255 - 1

12) 172.27.255.228 /27 which subnet

111 00100 

172.27.255.224

13) subnet of 172.24.135.234 255.255.255.240 = /28

1110 1010

.224

14) subnet of 172.23.174.168 /28
1010 1000

.160

15) How many subnets and hosts per subnet can you get from 192.168.221.0/26

subnets = 2 borrowed bits 2**2 = 4
hosts = 2 ** 6 - 2 = 62

16) How many subnets and hosts per subnet can you get from 192.168.176.0/29
subnets 2**5 = 32
hosts = 2 ** 3 - 2 = 6

17) You are designing a subnet mask for the 172.24.0.0 network. You want 10 subnets with up to 3800 hosts on each subnet. What subnet mask should you use?

2 ** 12 = 4096 need 12 host bits

172.24.0000  0000.00000000

/20 = 255.255.240.0

18) What is the broadcast address of the network 172.17.227.0/24?
172.17.227.255

19)You are designing a subnet mask for the 172.20.0.0 network. You want 3500 subnets with up to 9 hosts on each subnet. What subnet mask should you use?

2**12 = 4096 need 12 subnet bits

172.20.00000000.0000 0000

255.255.255.240 /28

20)What is the first valid host on the subnetwork that the node 172.18.54.209/23 belongs to?

172.18.0011011 0.

172.18.54.1

21)How many subnets and hosts per subnet can you get from the network 10.0.0.0/20?
2**12 = 4096
2**12 - 2 = 4094

22) You are designing a subnet mask for the 172.19.0.0 network. You want 80 subnets with up to 300 hosts on each subnet. What subnet mask should you use?

2**9 = 512

172.19.0000000 0.00000000

/23 255.255.254.0