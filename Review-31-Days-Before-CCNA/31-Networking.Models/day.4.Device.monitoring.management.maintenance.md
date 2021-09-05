## Device Monitoring, Management and Maintenance

Exam Topics

- Explain the function of SNMP in network operations
- Describe the use of syslog features including facilities and levels
- Configure and verify NTP operating in a CLient and Server mode 
- Describe the capabilities and function of TFTP/FTP in the network

## SNMP Operation 

SNMP is an application layer protocol that provides a message format for communication between managers and agents.

The SNMP system consists of three elements:
    - SNMP manager 
    - SNMP agents
    - Management Information Base (MIB)

#### SNMP Messages 

The SNMP manager is part of a network management system (NMS) and runs SNMP management software. SNMP agents are managed devices. The MIB stores SNMP variables. SNMP uses three basic messages between SNMP managers and agents: get, set and trap messages. The SNMP manager uses get messages to poll a device for information and set messages to changes a device parameter. An SNMP agent can use SNMP traps to independently notify the NMS when a problem occurs. For example, SNMP can monitor the CPU utilization on a Cisco router. The NMS can sample this value periodically and warn when the value deviates from the baseline. An SNMP agent can also be configured to send a trap message when CPU utilization is driving away from normal values for the network operations

#### get and set SNMP Operations

**get-request:** retrieves a value from a specific variable 

**get-next-request:** retrieves a value from a variable within a table. The SNMP manager does not need to know the exact variable name. A sequential search is performed to find the needed variable from within a table 

**get-bulk-request:** retrieves large blocks of data, such as multiple rows in a table, that would otherwise require the transmission of many small blocks of data.

**get-response:** replies to a get-request, get-next-request, or set-request sent by an NMS 

**set-request:** stores a value in a specific variable


#### SNMP Versions

Several versions of SNMP exist:
    - SNMPv1: the original SNMP defined in RFC 1157
    - SNMPv2: defined in RFCs 1901 to 1908. Utilizes a community string based admin framework 
    - SNMPv3: Interoperable standards-based protocol originally defined in RFC's 2273 to 2275. Provides secure access to devices by authentication and encrypting packets over the network

SNMPv1 and SNMPv2c use community strings that control access to the MIB. Community strings are plaintext passwords. Two types of community strings exist:
    * Read-only (ro): provides access to the MIB variables but does not allow these variables to be changed
    * Read-write (rw): provides read and write access to all objects in the MIB 

#### The Management Information Base

The MIB organizes variables hierarchically. MIB variables enable the management software to monitor and control the network device. Formally. the MIB defines each variable as an object ID (OID). OIDs uniquely identify managed objects in the MIB hierarchy. The MIB organizes the OIDs based on RFC standards into a hierarchy of OIDs usually shown as a tree.

RFCs define some common public variables, below shows portions of the MIB structure defined by Cisco:

###### Management Information Base Object IDs  

iso(1), org(3), dod(6), internet(1), private(4). enterprises(1), cisco(9)

from cisco(9) - local variables(2) & interface group(2) 
              - cisco management(9) & cisco flash group(10)

The OID can be described in words or numbers to help locate a particular variable in the tree. 

## Configuring SNMP 