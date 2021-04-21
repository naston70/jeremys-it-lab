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

## Dynamic ARP Inspection - DAI

Man in the Middle ARP spoofing - attacker sends a gratuitous ARP claiming a MAC causing devices to update their ARP cache. Traffic goes through the attacker. Can also be used for DDoS. 

- When you enable DHCP snooping, the switch inspects the DHCP traffic and keeps track of which IP addresses were assigned to which MAC addresses
- ie PC1 with MAC 1.1.1 was assigned IP 10.10.10.10
- If invalid ARP traffic tries to pass through the switch, ie 3.3.3 saying its IP is 10.10.10.10, the switch drops the traffic

DAI is not performed on trusted ports. Enable this for non DHCP clients

(config)
```
#int f0/1
#ip arp inspection trust 
#ip arp inspection vlan 10
```

## 802.1X Identity Based Networking

- When 802.1X is enabled, only authentication traffic is allowed on switch ports until the host and user are authenticated
- When the user has entered a valid username and password, the switch port transitions to a normal access port in the relevant VLAN 

## Port Security - Preventing Unauthorised Devices 



