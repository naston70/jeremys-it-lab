## CDP and LLDP

Layer 2 Discovery Protocols


#### Layer 2 Protocols

- Layer 2 discovery protocols such as CDP and LLDP share information with and discover information about neighboring devices
- The shared information includes hostname, ip address, device type, etc
- CDP is Cisco proprietary
- LLDP is industry standard
- As they share information about the devices in the network, they can be considered a security risk and often aren't used. 

#### CDP
* CDP is a Cisco proprietary protocol
* It is enabled on Cisco devices by default
* CDP messages are periodically sent to multicast address 0100.0ccc.cccc
* WHen a device receives a CDP message, it processes and discards the message. It does not forward it to other devices.
* By default, CDPmessages are sent once every 60 seconds
* By default, the CDP holdtime is 180 seconds. If a message isn't received from a neighbor for 180 seconds, the neighbor is removed from the CDP neighbor table
* CDPv2 messages are sent by default

#### Basic CDP commands











