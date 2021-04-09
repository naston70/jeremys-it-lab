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

## EIGRP Characteristics
* EIGRP is an Advanced Distance Vector routing protocol
* It supports large networks
* It has very fast convergence time 
* It supports bounded updates where network topology change updates are only sent to routers affected by the change
* Messages are sent using multicast
* EIGRP will automatically perform equal cost load balancing on up to 4 paths by default
* This can be increased up to 16 paths
* EIGRP can also be configured to perform unequal cost load balancing

#### EIGRP Config - AS Number
```
#router eigrp 100
```
The '100' in the example is the Autonomous System, meaning an independent administrative domain. EIGRP routers need to have the same AS number to peer with each other. 

#### EIGRP Configuration - network
```
#router eigrp 100
#network 10.0.0.0 0.0.255.255
```

- The network command uses a wildcard mask
- Subtract each octet in the subnet mask from 255 to calculate the wildcard mask
- A subnet of 255.255.255.253 = 0.0.0.3 (255 - 252 = 3)
- If not wildcard mask is entered it will use the classful boundary

**What the 'network' command means:**

- Look for interfaces with an IP address which falls within this range
- Enable EIGRP on those interfaces - send out and listen for EIGRP hello messages, and peer with adjacent EIGRP routers
- Advertise the network and mask which is configured on those interfaces

#### EIGRP Router ID
* EIGRP routers identify themselves using an EIGRP Router ID which is in the form of an IP address
* This will default to being the highest IP address of any loopback interfaces configured on the router, or the highest other IP address if a loopback does not exist
* Loopback interfaces never go down so the Router ID will never change
* You can manually specify the Router ID
* Best practice is to use a Loopback or manually set the Router ID 












