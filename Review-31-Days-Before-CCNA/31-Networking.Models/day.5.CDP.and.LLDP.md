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