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

If multiple links are added to an existing link to aid with congestion, STP will block the additional ports. All except one will be disabled by STP. It does this as if all of the switches Ports were forwarding, Layer 2 loops would form between switches, causing broadcast storms 

