## Solving VLSM Subnetting Scheme

###### Starting Network: 172.16.1.0 /24

Divide into 7 subnets.

1. 125
2. 59
3. 25
4. 12
5. 2
6. 2
7. 2

Using Binary Place Values to assign correct Subnet size 

First ask if there is enough address space.

1. To create the subnet for 128 - 2 hosts we need to borrow 1 bit
172.16.1.0   /25 - 128
172.16.1.128 /26 - 64
172.16.1.192 /27 - 32 
172.16.1.224 /28 - 16
172.16.1.240 /30 - 4
172.16.1.244 /30 - 4
172.16.1.248 /30 - 4
