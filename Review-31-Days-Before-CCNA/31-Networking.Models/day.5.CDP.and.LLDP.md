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
