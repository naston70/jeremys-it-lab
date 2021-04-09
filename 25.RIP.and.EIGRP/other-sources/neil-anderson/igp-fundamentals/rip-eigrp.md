## RIP 

* RIP is a Distance Vector protocol
* Uses hop count as the metric
* Max hop count is 15
* Performs ECMP for up to four routes

#### RIP v2 Configuration
```
R1(config)#router rip
R1(config-router)#version 2
R1(config-router)#network 10.0.0.0
```

The 'network' command should reference a classful network. No subnet mask is specified

- RIP will automatically summarise routes to the classful boundary by default
- 192.168.10.1/30 will be advertised as 192.168.10.0/24 (class C address)
- 172.16.10.1/30 will be advertised as 172.16.0.0/16 (class B address)
- This is not usually desirable

This can be achieved by using Manual Summarization. 

Manual summarization gives control of exactly how the summary is done. The individual summarised routes are not advertised - only their summary route
This is configured on the interface the advertisement will be sent out of.

PIPv2 Verification
```show ip protocols
```
 
```show run | section rip
```

```show ip route
```

```show ip rip database
```

#### Default Route Injection
```
ip route 0.0.0.0 0.0.0.0 203.0.113.2
router rip
default-information originate
```

This will create the default route out to the Internet and be advertised for all other devices to learn via RIP. (make out facing interface a passive-interface to stop routes being advertised outside of desired network)















