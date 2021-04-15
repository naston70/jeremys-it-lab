## DHCP

DHCP is a client/server protocol that automatically provides a host with its ip address and other related configuration information such as the subnet mask and default gateway.

DHCP clients obtain their IP configuration information from a DHCP server, rather than being manually configured

#### How It Works

client ------------------------- server
--------------------------------------> DHCP Discover (Broadcast)
<-------------------------------------- DHCP Offer (Unicast/Broadcast)
--------------------------------------> DHCP Request (Broadcast)
<-------------------------------------- DHCP Ack (Unicast/Broadcast)

#### DHCP Benefits

- Centralized and automated IP configuration, rather than manually assigning an IP address to every host
- Can assign additional IP configuration by means of DHCP options (ie phones)
- Efficient handling of clients that are updated frequently, such as devices moving to different locations on a wireless network
- The forwarding of initial DHCP messages by using a DHCP relay agent, which eliminates the need for a DHCP server on every subnet

DHCP minimizes configuration errors caused by manual IP address configuration, such as typos or address conflicts caused by the assignment of an IP address to more than one computer at the same time. 

