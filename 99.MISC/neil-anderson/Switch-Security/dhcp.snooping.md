## DHCP Snooping

Arises when a rogue DHCP server is connected to a network. PC's can get wrong information, usually caused by users connecting devices but can also be an attack.

When DHCP snooping is enabled, DHCP server responses are dropped if they do not arrive on a trusted port.

(Switch config for when the dhcp server is coming in from f0/1)
```
#ip dhcp snooping
#ip dhcp snooping vlan 10
#int f0/1
#ip dhcp snooping trust
```

