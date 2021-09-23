## Study Mode Exam 2


#### Reviews

* IPv6 types
* LACP active/passive | desirable/auto
* Code types for Puppet, Chef, Ansible and Salt
* GRE tunnels
* EIGRP terms
* WLC GUI
* OSPF non-broadcast
* NAT 
* Syslog levels Ernie-Always-Cries-Even-When-No one-Is-Dying 
or Emergency - Alert - Critical - Errors - Warning - Notification - Informational - Debug
* GRE tunnels
* FHRP MAC addresses
* port security violation modes
* security levels enable and secret

#### IPv6 Types

```
FF00::/8  == Multicast
2000::/3  == Global Unicast
FE80::/10 == Link-Local Addresses
FC00::/7  == Unique Local Addresses
::1/128   == Loopback 
```
**IPv6 questions:**
1. What is the IPv6 prefix for a unicast link local address?
A. FE80::/10

2. Which of the following IPv6 addresses is a link-local multicast address that is used to send a packet to all routers on a segment?
```
FF02::2
FF05::2
FF02::1
FF05::1
```

FF02::2, why?

All hosts        : FF02::1 = 224.0.0.1
All routers      : FF02::2 = 224.0.0.2
All OSPF routers : FF02::5 = 224.0.0.5
All OSPF DRs     : FF02::6 = 224.0.0.6
All RIP Routers  : FF02::9 = 224.0.0.9
ALL EIGRP routers: FF02::A = 224.0.0.A 


