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

A cisco router can be configured to handle DHCP requests in two ways: as a DHCP server or as a DHCP relay agent. A cisco router can also be configured as a DHCP client, requesting an IPv4 address from a DHCP server for one or more of its interfaces.


