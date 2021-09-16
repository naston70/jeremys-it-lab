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

128    64    32    16    8    4    2    1
128    192   224   240   248  252  254  255
/25    /26   /27   /28   /29  /30  /31  /32
/17    /18   /19   /20   /21  /22  /23  /24
#### Problem 2

* IP - 133.46.200.122 /28 = .240
1 - 16
2 - Host Address
3  .240
4 - 133.46.200.112
5 - 133.56.200.127
6 - 133.46.200.113
7 - 133.46.200.126
8 - 128

#### Problem 3

* 146.24.16.137 /22
1. 4
2. Host Address
3. .252.0
4. .16.0
5. .19.255
6. .16.1
7. .19.254
8. 32-22 = 10**2 = 1024 - 2 usable

