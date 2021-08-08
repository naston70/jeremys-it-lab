## DHCP and DNS

#### Exam Topics

- Explain the role of DHCP and DNS in a network 
- Configure and verify DHCP client and relay
- Verify IP parameters for Client OS

#### DHCPV4

DHCPV4 allows a host to obtain an IP address dynamically when it connects to the network. The DHCPv4 client contacts the DHCPv4 server by sending a request for an IP address. The DHCPv4 server chooses an address from a configured range called a pool and assigns it to the host client for a set period. 

###### Allocating IP Addressing Information Using DHCPv4

When a DHCPv4-configured device boots up or connects to the network, the client broadcasts a DHCPDISCOVER packet to identify any available DHCPv4 servers on the network. A DHCPv4 server replies with a DHCPOFFER, which is a lease offer message with an assigned IP address, subnet mask, DNS server and default gateway information as well as the duration of the lease

The client can receive multiple DHCPOFFER packets if the local network has more than one DHCPv4 server. The client chooses the first offer and broadcasts a DHCPREQUEST packet that identifies the explicit server and lease offer it is accepting.

Assuming the IP address is still valid, the chosen server returns a DHCPCK message, finalizing the lease. If the offer is no longer valid for some reason, the chosen server responds to the client with a DHCPNAK message. After it is leased, the client renews before the lease expiration through another DHCPREQUEST. If the client is powered down or taken off the network, the address is returned to the pool for reuse.

#### DHCPv4 Configuration Options

A cisco router can be configured to handle DHCP requests in two ways: as a DHCP server or as a DHCP relay agent. A cisco router can also be configured as a DHCP client, requesting an IPv4 address from a DHCP server for one or more of its interfaces. All these options can be configured at the same time on the same device. For example, a router might be the DHCP server for a directly connected LAN while at the same time forwarding DHCP server requests to another DHCP server for other LANs. In addition, the router could have one or more of its interfaces configured to request DHCP addressing from a remote server.

#### Configuring a Router as DHCPv4 server

A cisco router running IOS software can be configured to act as a DHCPv4 server. The Cisco IOS DHCPv4 server assigns and manages IPv4 addresses from specified address pools within the router to DHCPv4 clients

The step to configure a router as a DHCPv4 server:

1. Use ```ip dhcp excluded-address [address|low|high]``` command to identify an address or range of addresses to exclude from the DHCPv4 pool.
eg:
```
# ip dhcp excluded-address 192.168.10.1 192.168.10.20
```

2. Create the DHCPv4 pool which moves into the DHCP configuration mode:
```
# ip dhcp pool LAN-POOL-10
```

3. Configure the IP addressing parameter you need to automatically assign to requesting clients

#### Configuring a Router to Relay DHCPv4 requests

In a complex network, the DHCPv4 servers are usually contained in a server farm. Therefore clients typically are not on the same subnet as the DHCPv4 server. To ensure the broadcasted DHCPDISCOVER messages are sent to the remote DHCPv4 server, use the ```ip helper-address``` command.

#### Configuring a Router as a DHCPv4 Client 

Cisco routers in small offices or branch sites are often configured as DHCPv4 clients. The method used depends on the ISP. However, in its simplest configuration, the interface used to connect to a cable or DSL modem is configured with the ```ip address dhcp``` cmd 

## DHCPv6

IPv6 has two methods for automatically obtaining a global unicast address:
- Stateless address autoconfiguration (SLAAC)
- Stateful DHCPv6

#### SLAAC




