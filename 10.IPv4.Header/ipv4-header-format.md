## IPv4 Header Format

O = OCTET
B = BIT


O  B	 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31
				|		|			    |     |
0  0     Version|  IHL  |      DSCP     | ECN |  		Total Length

4  32			Identification				  | Flags  |      Fragment Offset

8  64		TTL			|  Protocol			  |			Header Checksum

12 96								Source IP address 32 bit

16 128								Destination IP address

20 160   Options...


60 489

Version = 4 bits, IHL = 4 bits, DSCP = 6 bits, ECN = 2 bits, Total Length = 16 bits
Identification = 16 bits, Flags = 3 bits, Fragment Offset = 13 bits
TTL = 8 bits, Protocol = 8 bits, Header Checksum = 16 bits

## Protocol Field Values:

1 = ICMP
4 = IPv4
6 = TCP
17 = UDP
89 = OSPF

* Maximum length of IPv4 header = 60 bytes
* Minimum length of IPv4 header = 20 bytes
* Maximum value of 'Total Length' field = 65535
* Minimum value of 'Total Length' field = 20
* Minimum value of IHL field = 5
* Maximum value of IHL field = 15
* Maximum length of Options field = 320 bits / 40 bytes
* Minimum length of Options field = 0 bits
* Flags field MF bit = 2
* Flags field DF bit = 1