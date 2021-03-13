# Subnetting

How many usable addresses are there in each network?

###### 2**n - 2 = usable addresses. n = number of host bits

203.0.113.0/25: 32 - 25 = 7 (2**7) - 2 = 126 usable
203.0.113.0/26: 32 - 26 = 6 (2**6) - 2 = 62 usable
203.0.113.0/27: 32 - 27 = 5 (2**5) - 2 = 30 usable
203.0.113.0/28: 32 - 28 = 4 (2**4) - 2 = 14 usable
203.0.113.0/29: 32 - 29 = 3 (2**3) - 2 = 6 usable
203.0.113.0/30: 32 - 30 = 2 (2**2) - 2 = 2 usable
203.0.113.0/31: 32 - 31 = 1 (2**1) - 2 = 0 usable - for point to point links when no need for a net or broadcast ip
203.0.113.0/32: 32 - 32 = 0 (2**0) - 2 = -1 X - used for a static route 

#### CIDR Notation

C

255.255.255.**128** = /25
255.255.255.**192** = /26
255.255.255.**224** = /27
255.255.255.**240** = /28
255.255.255.**248** = /29
255.255.255.**252** = /30
255.255.255.**254** = /31
255.255.255.**255** = /32




