## DHCP

DHCP is a client/server protocol that automatically provides a host with its ip address and other related configuration information such as the subnet mask and default gateway.

DHCP clients obtain their IP configuration information from a DHCP server, rather than being manually configured

#### How It Works

client ------------------------- server
--------------------------------------> DHCP Discover (Broadcast)
<-------------------------------------- DHCP Offer (Unicast/Broadcast)
--------------------------------------> DHCP Request (Broadcast)
<-------------------------------------- DHCP ACK (Unicast/Broadcast)

#### DHCP Benefits

- Centralized and automated IP configuration, rather than manually assigning an IP address to every host
- Can assign additional IP configuration by means of DHCP options (ie phones)
- Efficient handling of clients that are updated frequently, such as devices moving to different locations on a wireless network
- The forwarding of initial DHCP messages by using a DHCP relay agent, which eliminates the need for a DHCP server on every subnet

DHCP minimizes configuration errors caused by manual IP address configuration, such as typos or address conflicts caused by the assignment of an IP address to more than one computer at the same time. 

Servers and network infrastructure will not typically be DHCP clients. They will be mission critical devices which do not move and are required for the network and its services to function. They should be manually configured.

## Cisco DHCP Server Configuration 

```
#ip dhcp excluded-address [10.0.0.1 10.10.10.10]
#ip dhcp pool [10-Clients]
#network 10.10.10.0 255.255.255.0
#default router [router-ip]
#dns-server [dns-server]
```

## Configuring a Cisco Router as a DHCP Client

* Cisco routers are typically manually configured with a static IP addresses
* An exception to this is where an office is connected to the Internet but has not bought static public IP addresses (because it does not contain any publicly available servers which would need a fixed IP address for incoming connections)
* The office still requires a public IP address to allow internal hosts outbound connectivity to the Internet through NAT
* In this case the router will receive the public IP address on its outside interface from the Internet service provider via DHCP

```
#interface f0/0
#ip address dhcp
#no shutdown
```

```
show dhcp lease
```









