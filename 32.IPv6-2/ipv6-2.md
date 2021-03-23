## IPv6 - 2

#### EUI - CONFIGURING IPv6 ADDRESSESS WITH EUI-64

- EUI stands for Extended Unique Identifier
- EUI is a method of converting a MAC address into a 64-bit interface identifier
- The interface identifier can then become the 'host portion' of a /64 IPv6 address
- How to convert the MAC address:
    1. Divide the MAC address in half eg 1234 5678 90AB becomes 123456 | 7890AB
    2. Insert FFFE in the middle: 1234 56FF FE78 90AB
    3. Invert the 7th bit (4 bit per number) 0001 0010 0011 1000 (1234)
    4. 7th bit is the 2 (0010) which becomes 0000 when inverted = 1034
    5. 1034 56FF FE78 90AB it will be added on to the prefix to make the complete IPv6 address

Practice converting a MAC address into an EUI-64 Interface Identifier:
|MAC ADDRESS                |EUI-64 Interface Identifier|
|---------------------------|---------------------------|
| 782B CB AC 0867           |7A2B CBFF FEAC 0867        |
| 0200 4C 4F 4F50           |0000 4CFF FE4F 4F50        |
| 00FF 6B A6 F456           |02FF 6BFF FEA6 F456        |

**EUI-64 allow routers to automatically generate an IPv6 address by expanding the MAC address to a 64 bit interface ID, which is then combined with the specified IPv6 address prefix**

Its a method of automatically generating an IPv6 address using a prefix and MAC

#### Global Unicast Addresses

* Global unicast IPv6 addresses are public addresses which can be used over the Internet
* The must be registered and are expected to be globally unique
* Defined as all addresses which aren't reserved for other purposes

2001:0DB8:8B00:0001::1/64

First 3 are the 48-bit 'global routing prefix'
4th is the 'subnet identifier'
Last 16 = 'interface identifier', the host portion of the address

#### Unique Local Addresses

* Unique local IPv6 addresses are private addresses which cannot be used over the Internet
* Do not need to be registered
* Requires the 8th bit to be set to 1 so the first two digits must be FD
* The global ID should be unique so that addresses don't overlap in merges

**FD**45:93AC:8A8F:0001:0000:0000:0000:0001/64

FD indicates a unique local 








