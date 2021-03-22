## IPv6

Exam Topics:
- Configure and verify IPv6 addressing and prefix - 1.8
- Compare IPv6 address type - 1.9
- Configure and verify IPv4 and IPv6 static routing - 3.3

#### Hexadecimal review

Number systems:
    - Binary / Base 2 / 0b = (0,1)
    - Decimal / Base 10 / 0d = (0,1,2,3,4,5,6,7,8,9)
    - Hexadecimal / Base 16 / 0x = (0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F)

CONVERSIONS: 

1)
0b11011011 - split the number into 4 bit groups
0b1101  0b 1011 - convert each group into decimal
0d13 --- 0d11  - convert the decimal to hexadecimal
0xD -- 0xB

0b11011011 = 0xDB

2)
0b00101111 = 0x??
0b0010  0b1111
0d2     0d15
0x2     0xF
0x2F

3)
0b100000001 = 0x?
0b1000  0b0001
0d8     0d1
0x8     0x1
0x81

Converting Hexadecimal to Binary (reverse the process)
1)
0xEC = 0b?
0xE  0xC
0d14  0d12
0b1110  0b1100
0b11101100 

2)
0x2B = 0b??
0x2    0xB
0d2    0d11
0010   1011
00101011

## Why IPv6?
- Main reason is that there aren't enough IPv4 addresses available
- Only 2**32 address available
- When designed there was no idea the Internet would grow to the size it has
- VLSM, private IPv4 addresses and NAT have been used to conserver the use of IPv4 but are only short term solutions
- IPv6 is the long-term solution






































