## CDP and LLDP

Exam Topic:

- Configure and verify Layer 2 discovery protocols

CDP is Cisco proprietary
LLDP is open standard

#### CDP Overview 

CDP sends advertisements to directly connected devices.

CDP runs on all Cisco manufactured equipment. It gathers the protocol addresses of neighboring devices and discovers the platforms of those devices. CDP runs over the data link layer only. This means that two systems that support different Layer 3 protocols can learn about each other.

###### CDP Defaults

| parameter    | default                                |
|--------------|----------------------------------------|
|              |                                        |
| CDP          | Enabled globally and on all interfaces |
| CDP version  | Version 2                              |
| CDP timer    | 60 seconds                             |
| CDP holdtime | 180 seconds                            |
|              |                                        |


CDP can assist in network discovery and troubleshooting. CDP advertises the following helpful information:
- Device ID
- Addresses
- Port ID
- Capabilities
- Version 
- Platform 

#### CDP Configuration
```
# show cdp interface 
...
GigabitEthernet0/1 is up, line protocol is up
  Encapsulation ARPA
  Sending CDP packets every 60 seconds
```

An interface does not have to be configured with a Layer 3 address to send or receive CDP advertisements. The interface only needs to be activated with the ```no shutdown``` command. 

###### Sending Layer 2 Messages
```
# show cdp neighbors

```

To disable CDP on the device, use the CDP global configuration command ```no cdp run``` To verify that the device is no longer running CDP by using the ```show cdp``` command 

After waiting for the 180-second holdtime to expire on the switch, you can verify that the switch is no longer receiving information about the router.

CDP can also be disabled on a per-interface basis. This configuration option is a security best practice for interfaces that are connected to untrusted networks. 
To disable CDP on an interface, use the ```no cdp enable``` command

#### Disabling CDP on an Interface 
```
router(config)# interface s0/0/0
router(config-if)# no cdp enable 
router(config-if)# end 
router# show cdp interface 
```

To adjust the time for CDP advertisements, use the ```cdp timer```global configuration command:
```
#cdp timer seconds
```

The range is 5 to 254 seconds and the default is 60 seconds. If you modify the CDP timer, you should also modify the holdtime with the ```cdp holdtime``` global configuration command:
```
router(config)# cdp holdtime seconds
```

The range is from 10 to 255, with default of 180 seconds

#### CDP Verification 
```
show cdp, show cdp neighbors, show cdp interface
```

The ```show cdp neighbors detail``` command lists all the information CDP gather about directly connected neighbors. 

When documentation is lacking or incomplete, CDP can be used to gather information about devices and to discover the network topology


## LLDP Overview

In addition to supporting CDP, Cisco devices also support LLDP, a vendor neutral open standard. LLDP works with routers, switches and wireless LAN access points. As with CDP, LLDP is a neighbor discovery protocol that is used for network devices to advertise information about themselves to other devices on the network. As with CDP, LLDP enables two systems running different network layer protocols to learn about each other. 

###### LLDP Defaults 
| parameter              | default                                 |
|------------------------|-----------------------------------------|
|                        |                                         |
| LLDP                   | Disabled globally and on each interface |
| LLDP timer             | 30 seconds                              |
| LLDP holdtime          | 120 seconds                             |
| LLDP reinitialization  | 2 seconds delay                         |


When enabled globally, LLDP is enabled on all interfaces. To disable LLDP on an interface, use the ```no lldp transmit``` and the ```no lldp receive``` commands
To adjust the time for LLDP advertisements, use the ```lldp timer``` global configuration command. The range is 5 to 65534 seconds and the default is 40 seconds. 

#### LLDP Configuration 