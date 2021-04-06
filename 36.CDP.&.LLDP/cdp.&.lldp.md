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
```show cdp
```
Shows the global CDP information - timers and version in use
```show cdp traffic
```
How many packets, advertisements have been sent and received
```show cdp interface
```
Gives basic information on each interface, includes a basic summary
```show cdp neighbors
```
Shows table with information gathered from connected devices, Device ID, interface, holdtime, capability (helps determine device type connected to), platform and port ID
```show cdp neighbors detail
```
Shows further details about connected neighbors
```show cdp entry R2
```
Shows the details of just one entry

#### CDP configuration commands

* CDP is globally enabled by default
* CDP is also enabled on each interface by default
* To enable/disable CDP globally ```#[no] cdp run```
* To enable/disable CDP on specific interfaces: ```#[no] cdp enable```
* Configure CDP timer: ```#cdp timer seconds```
* Configure CDP holdtime: ```#cdp holdtime seconds```
* Enable/disable CDPv2: ```#cdp advertise-v2``


## Link Layer Discovery Protocol

- LLDP is industry standard 
- It is usually disabled by default, must be manually enabled
- A device can run CDP and LLDP at the same time
- LLDP messages are periodically sent to multicast MAC address 0180.C200.000E
- A device can run CDP and LLDP at the same time
- When a device receives an LLDP message, it processes and discards the message. It does not forward it to other devices
- Meassges sent every 30 seconds
- Holdtime 120 seconds


## LLDP Configuration Commands
* LLDP is usually globally disabled by default
* LLDP is also disabled on each interface
* To enable LLDP globally: ```#lldp run```
* To enable LLDP on specific interfaces tx ```lldp transmit```
* To enable LLDP on specific interfaces rx ```lldp receive```
* Configure the LLDP timer ```lldp timer secs```
* Configure the LLDP holdtime ```lldp holdtime secs``

Need to enable transmit and receive on interfaces

#### LLDP show commands

```#show lldp
```
shows basic LLDP information - timers, active/inactive

```show lldp traffic
```
Shows LLDP traffic statistics

```show lldp interface
```
shows information on the interfaces

```show lldp neighbors
```
Shows device id, local interface, hold-time, capability, port ID












