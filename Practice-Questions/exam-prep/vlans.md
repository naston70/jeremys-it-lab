## VLANs
```
VLAN creation:

#vlan 100
#name Engineering

Access Port Configuration

#switchport mode access
#switchport nonegotiate
#switchport access vlan 100
#switchport voice vlan 150

Trunk Port Configuration

#switchport mode trunk
#switchport trunk encapsulation dot1q
#switchport trunk allowed vlan 10, 20-30
#switchport trunk native vlan 10

SVI Configuration
#interface vlan 100
#ip address 192.168.100.1 255.255.255.0
```
#### Terminology

**Trunking:**
Carrying multiple VLANs over the same physical connection

**Native VLAN:** 
By default, frames in this VLAN are untagged when sent accross a Trunking

**Access VLAN:**
The VLAN to which an access port is assigned

**Voice VLAN:**
If configured, enables minimal trunking to support voice traffic on addition to data traffic on access propagates

**DTP:**


##### VLAN Trunking Protocol (VTP)
*Domain:*
Common to all switches participating in VTP

*Server Mode:*
Generates and propagates VTP advertisements to clients; default mode on unconfigured switches

*Client Mode:*
Received and forwards advertisements from servers; VLANs cannot be manually configured on switches in client mode

*Transparent Mode:*
Forwards advertisements but does not participate in VTP, VLANs must be configured manually