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
