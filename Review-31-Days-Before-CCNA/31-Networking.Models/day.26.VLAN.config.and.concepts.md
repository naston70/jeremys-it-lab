## VLAN and Trunking Concepts and Configurations

#### EXAM TOPICS
- Configure and verify VLANs (normal range) spanning multiple switches

- Configure and verify interswitch connectivity

#### VLAN Concepts 

Although a switch comes out of the box with only one VLAN, normally a switch is configured to have two or more VLANs. With such a switch, you can create multiple broadcast domains by putting some interface into one VLAN and other interfaces into other VLANs.

**Reasons for VLANs**:
* Grouping users by department instead of physical location
* Segmenting devices into smaller LANs to reduce processing overhead for all devices on the LAN
* Reducing the workload of STP by limiting a VLAN to a single access switch
* Separating IP voice traffic from data traffic 
* Assisting troubleshooting by reducing the size of the failure domain

**Benefits of VLANs**:
**