## Fine Tuning and Troubleshooting OSPF

Exam Topics

- Configure and verify single area ospf

## OSPFv2 Configuration
```
R1(config)# router ospf 10
R1(config-router)# router-id 1.1.1.1
R1(config-router)# network 172.16.1.0 0.0.0.3 area 0 
R1(config-router)# network 172.16.3.0 0.0.0.3 area 0
R1(config-router)# network 192.168.10.4 0.0.0.3 area 0
R1(config-router)# passive-interface g0/0
R1(config-router)# auto-cost reference-bandwidth 10000
R1(config-router)# interface s0/0/1
R1(config-router)# bandwidth 64 
```

## Modifying OSPFv2

#### Redistributing a Default Route 

(Example R1 has a link to the Internet, that makes R1 an autonomous system boundary router).
Therefore a default route to the Internet is configured and redistribute the default static route with the ```default-information originate```command. 
```
R1(config)# ip route 0.0.0.0 0.0.0.0 Serial 0/1/0
R1(config)# router ospf 10
R1(config-router)# default-information originate
```

Any other routers in the area should now have default routes identified with the O*E2 code.

#### Modifying Hello and Dead Intervals