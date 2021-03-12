# EtherChanel

Etherchannel is a port aggregation technology in which multiple physical port links are grouped into one logical link. It is used to provide high speed links and redundancy. A maximum of 8 links can be aggregated to form a single link.

'Etherchannel' is ciscos own term for port channelling. It is commonly used to increase the bandwidth of Layer 2 technologies

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


To configure the EtherChannel cisco uses the ```port channel``` command but to view via the show command use ```etherchannel``` 

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


