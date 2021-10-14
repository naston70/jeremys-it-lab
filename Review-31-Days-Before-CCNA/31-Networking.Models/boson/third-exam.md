## Boson 3rd Review

In a split-MAC deployment, a lightweight access point is responsible for prioritizing packets and responding to beacon and probe requests. 

In a Cisco Unified Wireless Network deployment, the MAC functions that are normally handled by a single device in an autonomous wireless network a distributed between lightweight APs and and Wireless LAN Controllers. The functionality provided by the lightweight AP includes handling real-time processing of data, such as sending and receiving 802.11 traffic, responding to beacons and probe messages, encryption and packet prioritization. In addition the lightweight AP must send management information to the WLC so that the WLC can forward the information to a management station.

By contrast, a WLC handles tasks that are not time sensitive, such as security management, lightweight AP configuration management and client load balancing. The WLC is also responsible for client association requests, data encapsulation, client authentication, key exchange, security policy enforcement and Radio frequency management

------------------------------------------------------------------------------------------------------------------------

IPv6 computer that configures IPv6 address for itself: FE80::/10

FE80::/10 link local addresses are unique only on the local segment. Not routable 

------------------------------------------------------------------------------------------------------------------------

IEEE 802.3 Ethernet Frame

[preamble]-[sof]-[destination address]-[source address]-[type]-[payload]-[fcs]

preamble, sof, destination address, source address, type, payload, fcs 

------------------------------------------------------------------------------------------------------------------------

```errdisable detect cause inline-power```

If a PD attempts to draw more power than the cutoff power from a POE interface, how long will the interface remain in error-disabled state?

a. until it is manually reset with the shutdown and no shutdown commands

------------------------------------------------------------------------------------------------------------------------

Congestion avoidance that drops lower-priority packets if network congestion is detected?

a. Weighted random early detection is a congestion avoidance method that drops lower-priority packets if network congestion is detected. WRED selectively drops packets when output queues reach a predefined threshold.

------------------------------------------------------------------------------------------------------------------------

[enable secret] - configures and encrypts a clear-text password for gaining access to enable mode

[password 7] - configures an encrypted VTY login password

[service password-encryption] - enables global password encryption

[enable password] - configures a clear text password for gaining access to enable mode

[enable secret 5] - configures a previously encrypted password for gaining access to enable mode

------------------------------------------------------------------------------------------------------------------------

By default, a Cisco switch will send LLDP advertisements every 30 seconds when LLDP is enabled on an interface. LLDP is an OSI Layer 2 open-standard discovery protocol that is used to facilitate interoperability between cisco devices and non-Cisco devices. 
LLDP advertisements    = every 30 seconds
LLDP hold time         = 120 seconds
Reinitialisation delay = 2 seconds

------------------------------------------------------------------------------------------------------------------------



