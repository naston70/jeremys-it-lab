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

**The auto, desirable and non-silent keywords can only be used with PAgP.** The desirable keyword configures the channel group to actively negotiate PAgP, and the auto keyword configures the channel group to listen for PAgP negotiation to be offered. Either or both sides must be set to desirable to establish an EtherChannel. The optional ```non-silent``` keyword requires that a port receive PAgP packets before the port is added to the channel. 

#### Code Types for Automation Software

**PUPPET**
```
sudo::conf { 'CoAdmins':
ensure  => present,
content => '%admin ALL=(ALL) ALL'
}
```

The code above is a Puppet resource declaration. Puppet modules are written in Ruby DSL or in a Ruby-like Puppet language known as Puppet DSL. 

**CHEF**
```
sudo 'CoAdmins'
		group 'CoAdmins'
		nopasswd true
```

Chef is a configuration tool written in Ruby. Chef uses a client/server architecture or a standalone client configuration. Chef communicates by using HTTPS port 443. Configuration information is contained with cookbooks and stored on a Chef Server.

Ansible and Salt are both written using Python 

## Generic Routing Encapsulation

GRE is an IP encapsulation protocol used for encapsulating data packets that use one routing protocol inside the packets of another protocol. GRE is one way to set up a point to point connection across a network. IE an unsupported packet can be encapsulated inside a supported packer. This is called tunneling. GRE tunnels are usually configured between two routers, with each router acting like the end of the tunnel. Routers in between will not open the encapsulated packets; they only reference the header surrounding the packets in order to forward them

## EIGRP review

1. Which of the following are used in the calculation of EIGRP weight metrics?
```
a. the average segment delay
b. the lowest bw segment
c. the highest bw segment
d. the sum of the segment delays 
```

Answer B, the lowest bw segment and D, the sum of the segment delays

EIGRP uses the lowest segment bandwidth ans the sum of the segment delays in the calculation of metric weights, or k values. The ```metric weights``` commands adjust K values, which EIGRP use to calculate the best path to a destination network. By default EIGRP uses the K values that are related to bw and delay. K values must match between two routers for a neighbor relationship to be established between the routers.
c.

#### Wireless LAN Controllers

1. Which of the following best describes an AP deployment that connects APs to a WLC that is housed within a switch stack?

A. C - An embedded AP deployment

An embedded AP deployment typically connects APs to a Cisco Wireless LAN controller that is housed within a switch stack. The primary difference between this deployment and others is that the WLC is embedded within a stack of switching hardware instead of existing as a seperate entity.

**Other types of deployments:**
A Lightweight Deployment - can be embedded, however a lightweight AP deployment does not always connect APs to a WLC that is housed within a switch stack

An Autonomous AP deployment does not APs to a WLC that is housed in a stack, It contains interfaces for both wired and wireless networks and are typically deployed connected to the access layer of the three-tier hierarchical network model

A cloud-based AP deployment does not connect APs to a WLC that is housed within a switch stack, Instead cloud based APs connect to and are automatically configured by a WLC that is housed in a cloud-based system - ie Cisco Meraki AP

##### WLC GUI - Security

Using the Layer 3 Security drop down list box on the Layer 3 tab which security setting are most likely to be configured?

A. VPN-Pass-Through

When configuring a new WLAN, it is most likely to configure VPN Pass-Through by using the Layer 3 Security dropdown list on the Layer 3 tab of the Cisco WLC. The VPN VPN-Pass-Through setting is only available when configuring a WLAN (Not Guest WLAN)

**Layer 2 - Security Tab:**
- None 
- WPA+WPA2 
- 802.1X 
- Static WEP 
- Static WEP + 802.1X 
- CKIP (Cisco)
- None + EAP Pass-Through

**Layer 3 - Security Tab 
- None 
- IPSec
- VPN-Pass-Through
- Web Authentication 
- Web Pass-Through

#### The Five OSPF Broadcast Types

* **Broadcast**
* **Non Broadcast**
* **Point-to-Point**
* **Point-to-multipoint**
* **Point-to-multipoint**

OSPF **Broadcast** network type is enabled by default on Fiber Distributed Data Interface (FDDI) and Ethernet Interfaces, including FastEthernet and Gigabit Ethernet Interfaces. On broadcast networks, designated router (DR) and backup designated router (BDR) elections are performed. Multicast updates are sent so manual configuration of neighbor routers with the ```neighbor``` command is not required. By default, the Hello Timer is 10 seconds and the dead timer is set to 40 seconds.

OSPF **non-broadcast** is enabled by default on Frame Relay and X.25 networks. DR and BDR elections are performed. Non broadcast networks do not allow multicasts, therefore manual configuration of neighbor routers with the ```neighbor``` command is required so OSPF sends unicast updates. Hello timer is 30 seconds and dead timer 120. Also known as NBMA network - non-broadcast multiple access

OSPF **Point-to-Point** network type is enabled by default on HDLC and Point-to-Point Protocol interfaces. On Point-to-Point networks, DR and BDR elections are not performed. Multicast updates are sent, so manual configuration of neighbor routers with the neighbor command is not required. Default Hello is 10 and Dead is 40 seconds

