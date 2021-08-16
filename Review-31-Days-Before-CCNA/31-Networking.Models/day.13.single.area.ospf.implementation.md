## Single-Area OSPF Implementation

Exam Topics:

- Configure and verify single area OSPFv2

------------------------------------------
**R1**
G0/0: 172.16.1.1 255.255.255.0

S0/0/0: 172.16.3.1 255.255.255.252

S0/0/1: 192.168.10.5 255.255.255.252

**R2**
G0/0: 172.16.2.1 255.255.255.0

S0/0/0: 172.16.3.2 255.255.255.252

S0/0/1: 192.168.10.9 255.255.255.252

**R3**
G0/0: 192.168.1.1 255.255.255.0 

S0/0/0: 192.168.10.6 255.255.255.252

S0/0/1: 192.168.10.10 255.255.255.252
------------------------------------------

#### The **router ospf** command

OSPF is enabled with the ```router ospf process-id``` global configuration command:
```
R1(config)# router ospf process-id

```

*process-id* is a number between 1 and 65535 and is chosen by the network administrator. The process-id is locally significant. It does not have to match other OSPF routers to establish adjacencies with those neighbors. This differs from EIGRP as the EIGRP process ID and autonomous system number must match before two EIGRP neighbors can become adjacent. 

#### Router ID 

 