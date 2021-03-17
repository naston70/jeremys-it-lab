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

Version = 4 bits, IHL = 4 bits, DSCP = 6 bits, ECN = 2 bits, Total Length = 16
Identification = 16 bits, Flags = 3 bits, Fragment Offset = 13 bits
TTL = 8 bits, Protocol = 8 bits, Header Checksum = 16 bits