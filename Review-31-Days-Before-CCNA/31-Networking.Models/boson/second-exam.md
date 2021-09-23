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

3. You issue the following in global config:
```ipv6 route 2001:db8:a::/32 2001:db8:a::1 5```

What has been created?

A recursive static route that is also a floating static route. A recursive static route specifies the destination IPv6 network and the IPv6 next-hop address only. 

The floating static route adds an administrative distance (AD) 5 in this case

**Unicast link local addresses:** range between FE80 through FEBF and are local to that link

#### LACP

Channel groups on each switch must operate in compatible modes to create a functional EtherChannel link. The ```channel-group [number] mode {on|active|passive|auto|desirable}``` command is used to configure the operating mode for an interface or range of interfaces, in a channel group. 

**Channel Group Modes:**

OFF with any other mode results in NO formation
For PAgP:
desirable-auto and desirable-desirable

For LACP:
passive-active and active-active 

The only other formation occurs with ON-ON 

**The active and passive keywords can only be used with LACP.** The active keyword configures the channel group to actively negotiate LACP and the passive keyword configures the channel group to listen for LACP negotiation to be offered. Either or both sides of the link must be set to active to establish an EtherChannel over LACP, setting both to passive will not establish an EtherChannel over LACP.

**The auto, desirable and non-silent keywords can only be used with PAgP.**