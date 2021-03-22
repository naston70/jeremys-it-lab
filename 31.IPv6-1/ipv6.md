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

#### IPv6 

* An IPv6 address is 128 bits
* IPv6 addresses are written in hexadecimal
* They use the / notation

#### Shortening an IPv6 address

- Leading 0's can be removed
2001:0DB8:000A:001B:20A1:0020:0080:34BD
2001:DB8:A:1B:20A1:20:80:34BD

- Consecutive quartets of all 0's can be replaced with a double colon ::
2001:0DB8:0000:0000:0000:0000:0080:34BD
2001:0DB8::80:34BD

- Consecutive quartets can only be abbreviated once in an IPv6 address

#### Expanding a Shortened IPv6 address

- Put leading 0's back in where needed
    FE80::2:0:0:FBE8
    FE80::0002:0000:0000:FBE8

- If a double colon is used put back in all 0 quartets ensuring a total of 8 quartets.
    FE80:0000:0000:0000:0002:0000:0000:FBE8




































