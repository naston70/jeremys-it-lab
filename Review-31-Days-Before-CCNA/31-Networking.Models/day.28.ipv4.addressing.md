## IPv4 Addressing

Exam Topics:

- Configure and verify IPv4 addressing and subnetting 
- Describe the need for private IPv4 addressing 

#### IPv4 Addressing 

An IP address consists of two parts:

- Network ID: The higher order, left most, bits specify the network address component of the address 
- Host ID: The low-order, rightmost bit specify the host address components of the address 

###### Classes of Addresses

From the beginning, IPv4 was designed with class structure: Class A,B,C,D and E. Class D us used for multicasting addresses and Class E is reserved for experimentation. Classes A,B and C are assigned to network hosts. To provide a hierarchical structure, these classes are divided into network and host portions. The high-order bits specify the network ID and the low-order bits specify the host ID. 

In a classful addressing scheme, devices that operate at Layer 3 can determine the address class of an IP address from the format of the first few bits in the first octet. Initially, this was important so that a networking device could apply the default subnet mask for the address and determine the host address. 

###### Purpose of the Subnet Mask

Subnet masks are always a series of 1 bits followed by a series of 0 bits. The boundary where the series changes from 1's to 0's is the boundary between the network and the host. This is how a device that operates at Layer 3 determines the network address for packet: by finding the bit boundary where the series of 1 bits ends and the series of 0 bit begins. The bit boundary for default subnet masks breaks on the octet boundary. Determining the network address for an IP address that uses a default mask is easy.

Say that a router receives a packet destined for 192.168.1.51 by ANDing the IP address and the subnet mask, the router determines the network address for the packet. By the ANDing rule, a 1 AND a 1 equals 1. All other possibilities equal 0.

192.168.1.51
11000000.10101000.00000001.00110011

255.255.255.0
11111111.11111111.11111111.00000000

192.168.1.0
11000000.10101000.00000001.00000000

#### Private and Public IP Addressing 

RFC 1918 eased the demand for IP addresses by reserving the following addresses for use in private internetworks.
