# Life of a Packet Notes

Sending a packet across a network, from 192.168.1.0/24 to 192.168.4.0/24

PC1 sees it is sending the packet to a device in a different network, so forwards the packet to its default gateway (.254 in this case). 
In this example, no traffic has been sent so an ARP request will be made

**ARP Request**

Src IP: 192.168.1.1
Dst IP: 192.168.1.254
Dst MAC: ffff.ffff.ffff
Src Mac: 1111

The dst MAC is the broadcast of ffff.ffff.ffff

PC1 sends the frame which the switch floods out all interfaces except the one it received it on. 

'Hi 192.168.1.254, What is your MAC address?'

When the router receives this message it sees the dst IP as its own. So forms an ARP Reply

Src IP: 192.168.1.254
Dst IP: 192.168.1.1
Dst MAC: .1111
Src Mac: .aaaa

ARP Request = Broadcast | ARP Reply = Unicast

Now PC1 knows the MAC of its default gateway and sends the packet to R1. R1 looks up the destination in its Routing table. It looks for the most specific match and encapsulates the frame to send on to the next hop. However, R1 doesn't know the MAC address of R2 yet, so first sends an ARP request

Src IP: 192.168.12.1
Dst IP: 192.168.12.2
Dst MAC: ffff.ffff.ffff
Src Mac: .cccc

It sends the ARP request and R2 receives it. R2 sees the matching IP so makes the ARP reply. 

R2 removes ethernet header and looks up the routing table for the most specific match. R2 doesnt know R4's MAC address so will first send an ARP Request to R4

Src IP: 192.168.24.2
Dst IP: 192.168.24.4
Dst MAC: ffff.ffff.ffff
Src Mac: .dddd

R4 sends ARP reply due to the same IP address. Sends the MAC back. Encapsulates the packet with an Ethernet header.

R2 receives, deencapsulates and adds the learnt info and forwards the packet with a new header 
