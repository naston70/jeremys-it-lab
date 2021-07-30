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
