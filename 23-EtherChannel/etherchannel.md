# EtherChanel

EtherChannel is a port aggregation technology in which multiple physical port links are grouped into one logical link. It is used to provide high speed links and redundancy. A maximum of 8 links can be aggregated to form a single link.

'EtherChannel' is Cisco's own term for port channelling. It is commonly used to increase the bandwidth of Layer 2 technologies

[SW] =================== [SW]    Two switches connected via f0/1 - 4
[1 ] =================== [2 ]

```
(config)#interface range fa0/1 - 4
(config)#switchport mode trunk
(config)#channel-group 1 mode negotiate
(config)#interface port-channel 1
(config)#switchport mode trunk
```

These commands can be issued on both switches to join the Ethernet wires in port 1,2,3 and 4. Each line typically holds 100mbps but bundling them together could create a theoretical 400mbps.

Alongside the increase in speed there is also redundancy built in as one link can go down and not affect the link (other than a reduction in speed)

When multiple links are bundled in this way it is possible to configure the port channel in the same way that you would configure a physical port. All members of the EtherChannel will follow the configuration.

What problem does EtherChannel solve?

If multiple links are added to an existing link to aid with congestion, STP will block the additional ports. All except one will be disabled by STP. It does this as if all of the switches Ports were forwarding, Layer 2 loops would form between switches, causing broadcast storms. 

The new links would remain unused unless the active link failed, in that casr one of the other links will start forwarding. 

By forming the links into one EtherChannel, these problems are solved and the gains in redundancy and speed are realised. 

- EtherChannel groups multiple interfaces together to act as a single interface
- STP will treat this group as a single interface
- Traffic using EtherChannel will be load balanced among the physical interfaces in the group
- An algorithm is used to determine which traffic will use which interface

#### EtherChannel Load-Balancing

- EtherChannel load balances based on flows
- A flow is a communication between two nodes in the network
- Frames in the same flow will be forwarded using the same physical interface
- If frames in the same flow were forwarded using different physical interfaces, some frames may arrive at the destination out of order, which can cause problems

The interfaces used are determined by inputs used in the interface selection calculation
- Inputs that can be used:
	* Source MAC
	* Destination MAC
	* Source and Destination MAC
	* Source IP
	* Destination IP
	* Source and Destination IP

These inputs can be device specific.

Use this ```show etherchannel load-balance``` command to view the load balancing configuration

To change the Load Balancing configuration:
```
(config)#port-channel load-balance src-dst-mac
```
This will change the configuration to use the source and destination MAC address. The following options are available:
* dst-ip
* dst-mac
* src-dst-ip
* src-dst-mac
* src-ip
* src-mac


To configure the EtherChannel Cisco uses the ```port channel``` command but to view via the show command use ```etherchannel``` 

```
SW# show etherchannel load-balance
SW(config) port-channel load-balance method
```


#### EtherChannel Configuration

- There are 3 methods of EtherChannel configuration on Cisco switches


* PAgp (Port Aggregation Protocol)
	- Cisco Proprietary
	- Dynamically negotiates the creation/maintenance of the EtherChannel (Like DTP for trunks)

* LACP (Link Aggregation Control Protocol)
	- Industry standard 802.3ad
	- Dynamically negotiates the creation/maintenance of the EtherChannel (Like DTP for trunks)

LACP can be used with other vendors

* Static EtherChannel (usually avoided as there is no dynamic management or creation)
	- No protocol used to determine the creation of an EtherChannel
	- Interfaces are statically configured to form an EtherChannel

* Up to 8 interfaces can be formed into a single EtherChannel (LACP allows 16 but only 8 will be active, theother 8 will be on standby)

#### PAgP Configuration
```
SW1(config-if-range)# channel group 1 mode ?
	active		Enable LACP unconditionally
	auto		Enable PagP only if a PAgP device is detected
	desirable	Enable PAgP unconditionally
	on 			Enable EtherChannle only
	passive 	Enable LACP only if a LACP device is detected

SW1(config-if-range)#channel-group 1 mode desirable
```
Two commands are used for PAgp, two for LACP and one for Static EtherChannel, PAgP modes work in the same way as DTP

The channel group number will have to match for member interfaces on the same switch but doesn't have to match for the channel group on the other switch.

LACP works in the same way but with different names, passive and active 

Static has one mode, on.

#### Manually Configuring the Negotiation Protocol

The protocol is usually set when setting the mode

```
SW1(config-if-range)#channel-protocol lacp
```

After configuring the mode, it is possible to configure the portchannel interface itself.

* Member interfaces must have the same matching configurations
	- Same duplex
	- Same speed
	- Same switchport mode
	- Same allowed vlans
* If an interfaces settings don't match it will be excluded

The most useful command for verifying an etherchannel is ```show etherchannel summary```

#### Layer 3 Etherchannel

A layer 3 etherchannel is similar to an interface on a router. The switch wont 'switch' traffic but route it. As its a Layer 3 interface, it also needs an IP address.

## Review of Commands
 
```
SW(config)port-channel load-balance mode
```
# configures the EtherChannel load-balancing method on the switch (mac, ip, src, dst, both)

```
SW# show etherchannel load-balance 
```
# displays information about the load balancing settings

``` 
SW(config-if)# channel-group number mode {desirable|auto|active|passive|on} 
```

# configures an interface to be part of an EtherChannel

``` 
SW# show ether channel summary 
```
# most useful and displays a summary of etherchannels on the switch

``` 
SW# show etherchannel port-channel 
```

# displays information about the virtual port-channel interfaces on the switch


-------------------------------------------------------------------------------------------------------------------------

#### Configuring a Layer 2 EtherChannel using LACP  (lab exercise commands)

```
ASW1>enable
ASW1#show spanning-tree
ASW1#conf t
ASW1(config)#int range g0/1 - 2
ASW1(config-if-range)#int po1
ASW1(config-if)#switchport mode trunk
```

The two ports will show as being in standalone mode as the other side switch has yet to be configured

```
DSW1>enable
DSW1#conf t
DSW1(config)#int range g1/0/3 -4 
ASW1(config-if-range)#channel-group 1 mode active
ASW1(config-if-range)#int po1
ASW1(config-if)#switchport mode trunk
```
At this point there will be a reminder to set encapsulation as this switch model supports both ISL and dot1q
```
ASW1(config-if-range)#switchport trunk encapsulation dot1q
ASW1(config-if-range)#switchport mode trunk
```
Now the EtherChannel between these two switches should be up. This can be verified using:
```
#do show etherchannel summary
```

Po1(SU) is shown. S flag for Layer 2 and the U flag meaning in use.
To check the trunk interfaces: ```do show int trunk```



