## DHCP

Allows hosts to dynamically learn various aspects of their network configuration, such as IP, subnet mask, default gateway, dns server etc, without manual configuration

It is an essential part of modern networks and typically used for 'client devices' such as PC's and phones. Devices such as routers or servers are usually manually configured.
In small networks the router typically acts as the DHCP server for the hosts in the LAN. In large networks it will be a server.

UDP Port 68 for DHCP client
UDP Port 69 for DHCP server

Four Steps:

1. DHCP-Discover: Are there any DHCP servers in this network? I need an IP.
2. DHCP-Offer: How about this address?
3. DHCP-Request: I want to use the IP just offered
4. DHCP- ACK: Okay, it can be used.

#### DHCP Relay

* Some networks might be configured to use each router as the DHCP server for its connected LANs
* However, large enterprises often choose to use a centralized DHCP server
* If the server is centralized, it wont receive the DHCP clients broadcast DHCP messages (broadcast messages don't leave the local subnet)
* To fix this, a router can be configured to act as a DHCP relay agent
* The router will forward the clients broadcast DHCP messages to the remote DHCP server as unicast messages

#### DHCP SERVER Configuration in IOS
```
#ip dhcp excluded-address 192.168.1.1 192.168.1.10
#ip dhcp pool POOL_NAME
#network [network-address] [subnet or / notation] ie 192.168.1.0 /24
#dns-server [dns] 8.8.8.8
#domain-name example.com 
#default-router [ip]
#lease 0 5 30
```

```
#show ip dhcp binding
```

Shows connected devices with dhcp leases

#### DHCP Relay Agent in IOS

From interface configuration mode:
```
#ip helper-address [ip_of_server]
```

The router would need a route to the server.
Using ```show ip interface [interface] there is output showing the helper-address IP

## Configuring IOS as a DHCP client
```ip address dhcp
```


















