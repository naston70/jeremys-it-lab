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

SLAAC uses ICMPv6 Router Solicitation (RS) and Router Advertisement (RA) messages to provide addressing and other configuration information. A client then uses the RA information to build an IPv6 address and verify it with a special type of Neighbor Solicitation (NS) messages through duplicate address detection (DAD).
These three message types -  RS, RA, NS - belong to the Neighbor Discovery Protocol (NDP)

- **Router Solicitation message (RS):** When a client is configured to obtain its addressing information automatically using SLAAC, the client sends an RS message to the router. The RS messages is sent to the IPv6 all-routers multicast address - FF02::2
- **Router Advertisement message (RA):** A client uses this information to create its own IPv6 global unicast address. A router sends RA messages periodically or in response to RS messages. An RA messages includes the prefix and prefix length of the local segment. By default, Cisco routers send RA messages every 200 seconds. RA messages are sent to the IPv6 all-nodes multicast address FF02::1
- **Neighbor Solicitation messages (NS):** An NS message is normally used to learn the data link layer address of a neighbor on the same network. In the SLAAC process, a host uses DAD by inserting its own IPv6 address as the destination address in an NS message. The NS message is sent out on the network to verify that a newly minted IP address is unique. If an NS message is received the host knows it is not unique

#### Stateless DHCPv6

In stateless DHCPv6, the client uses the RA messages from the router to generate its global unicast address. However, the client then sends a request to the DHCPv6 server to obtain any additional information that the RA has not already supplied. 

For stateless DHCPv6, the O flag is set to 1 so that the client is informed that the additional configuration information is available from a stateless DHCPv6 server. 

#### Stateful DHCPv6

For Stateful DHCPv6, the RA messages tells the client to obtain all its addressing information from a DHCPv6 server. The M flag must be set on the interface.

## DHCPv6 Configuration Options

 A router can be configured as a stateless DHCPv6 server, a stateful DHCPv6 server and a DHCPv6 client. As in DHCPv4, the router can be configured with all three, depending on what role it plays for its various interfaces.

#### Configuring a Router as a Stateless DHCPv6 Server

To configure a router as a stateless DHCP server the ```ipv6 unicast-routing``` command is enabled. Then, in global configuration mode, configure the pool name, DNS server and domain name. Finally, the DHCPv6 pool on the appropriate interface and set the O flag so that clients on that interface know to request DHCPv6 services from the router

#### Configuring a Router as a Stateful DHCPv6 Server

The main difference between a stateless configuration and a stateful configuration is that a stateful server includes IPv6 addressing information and keeps a record of the IPv6 addresses that are leased out. Also, for the client side, the ```ipv6 address dhcp ``` command is used instead of the ```ipv6 address autoconfig```

## DHCP Troubleshooting

DHCP problems can arise for a multitude of reasons, such as software defects, NIC drivers, or DHCP relay agents.
However the most common problems are configuration issues

#### Resolving IPv4 Address Conflicts

Distinguishing whether DHCP is functioning correctly is important when the client is on the same subnet or VLAN as the DHCP server. If DHCP is working correctly when the client is on the same subnet or VLAN, the problem might be the DHCP relay agent. If the problem persists even when testing on the same subnet or VLAN as the server, the problem may be the server.

## DNS Operation
An IPv4 address lease can expire on a client that is still connected to a network. If the client does not renew the lease, the DHCP sever can reassign that IPv4 address to another client. When the client reboots, it requests an IPv4 address. If the DHCP server does not respond quickly, the client uses the last IPv4 address, creating a conflict. 

The ```show ip dhcp conflict``` command displays all address conflicts recorded by the DHCP server. The server uses the ping command to detect conflicts. The client uses ARP to detect clients. If an address conflict is detected the address is removed from the pool and is not assigned until an administrator resolves the conflict. 

#### Testing Connectivity Using a Static IP Address

When troubleshooting any DHCP issue, verify network connectivity by configuring static IPv4 address information on a client workstation. If the workstation cannot reach network resources with a statically configured IPv4 address, the root cause of the problem is not the DHCP server. At this point network connectivity troubleshooting is required.

#### Verify Switch Port Configuration

If the DHCP client cannot obtain an IPv4 address from the DHCP server at startup, attempt to obtain an IP address from the DHCP server by manually forcing the client to send a DHCP request. If a switch lies between the client and the DHCP server and the client cannot obtain the DHCP configuration, switch port issues may be the cause. These causes can include issues from trunking and channeling to STP and RSTP. PortFast configuration and edge port configurations resolve the most common DHCPv4 client issues that occur with an initial installation of a Cisco switch

#### Testing DHCPv4 Operation on the Same Subnet or VLAN 

Distinguishing whether DHCP is functioning correctly is important when the client is on the same subnet or VLAN as the DHCP server. If DHCP is working correctly when the client is on the same subnet or VLAN, the problem might be the DHCP relay agent. If the problem persists even when testing DHCP on the same subnet or VLAN as the DHCP server, the problem might be with the DHCP server.

## DNS Operation

DNS is a distributed system of servers that resolve domain names to IP addresses. The domain name is part of the uniform resource identifier (URI)

The DNS server stores different types of resource records to resolve names. These records contain the name, address and type of record. Some of these include: A, NS, AAAA and MX records.

When a client makes a query, the servers DNS process first looks at its own records to resolve the name. If it cannot resolve the name using its stored records, it contacts other servers to resolve the name.

## Troubleshooting DNS

As a network administrator, control over DNS issues is limited to two basic issues: DHCP server configurations and DNS server configurations.

In a small branch office, you are most likely using your ISP for all your DNS resolutions. Therefore, all the clients on your network will most likely have the IP address of the default gateway configured as the DNS server. 

In that case, issues with DNS are most likely due to issues with the default gateway router or connection to your ISP. 

## Verifying Host IP Configuration 

Whether manually configured or dynamically learned, every device on the network must have a valid IP address configuration. 
To work correctly a host needs:
* DNS Server IP Address
* Default gateway
* Devices own IP Address 
* Devices own subnet mask 


