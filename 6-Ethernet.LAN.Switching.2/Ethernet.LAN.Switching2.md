# Ethernet LAN Switching

### ARP

* ARP stands for 'Address Resolution Protocol'
* ARP is used to discover the Layer 2 address (MAC) of a known Layer 3 address (IP)
* It consists of two messages:
	- ARP Request
	- ARP Reply
* ARP Request is **broadcast:** sent to all hosts on the network
* ARP Reply is **unicast:** sent only to one host (host that sent the request)

FFFF.FFFF.FFFF.FFFF is the broadcast MAC address, this is used when a device wants to send out to all other devices in the Local network

MAC commands:

```
SW1#show mac address-table

SW1#clear mac address-table
```



