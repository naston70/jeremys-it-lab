# Life of a Packet Notes

Sending a packet across a network, from 192.168.1.0/24 to 192.168.4.0/24

PC1 sees it is sending the packet to a device in a different network, so forwards the packet to its default gateway (.254 in this case). 
In this example, no traffic has been sent so an ARP request will be made

**ARP Request**

Src IP: 192.168.1.1
Dst IP: 192.168.1.254
Dst MAC: ffff.ffff.ffff
Src Mac: 1111

