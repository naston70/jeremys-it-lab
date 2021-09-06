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

#### Configuring SNMP

Configuring SNMPv2c on a Cisco router or switch requires only one global configuration command: ```snmp server community```. Then the following steps:

1. Configure the community string and access-level (read-only or read-write) with the ```snmp-server community [string] {ro|rw}``` global command

2. (Optional) Document the location of the device by using the ```snmp-server location [text-describing-location]``` global configuration command

3. (Optional) Document the admin of the device by using the ```snmp-server contact [contact-name]``` global configuration command

4. (Optional) Restrict SNMP access to NMS hosts that are permitted by an access control list (ACL) by defining an ACL and referencing the ACL on the ```snmp-server community [string acl]``` global configuration command 

###### Configuring SNMPv2c for Read-Only Access
```
(config)# ip access-list standard SNMP_ACCESS
(config-std-nacl)# permit host 172.16.30.110
(config-std-nacl)# exit 
(config)# snmp-server community 4dm!n0nly RO SNMP_ACCESS
(config)# snmp-server location London
(config)# snmp-server contact London Bob
(config)# end
```

#### Verifying SNMP
```
# show snmp
```

The ```show snmp``` command does not display information related to the SNMP community string or the associated ACL. Use the ```show snmp community ``` command to display the community string and related ACL (if applied)

## Syslog 

Syslog is a term used to describe a standard that the IETF first documented in RFC 3164 in 2001. It is a popular protocol that many networking devices use, including routers, switches, application servers, firewalls and other network appliances. These devices can send their messages across the network, to be stored on syslog servers for later access by network administrators.

#### Syslog Operation

Syslog uses UDP/514 to send event notification messages across IP networks to event messages collectors. The syslog logging service provides three primary capabilities:
* Gathering logging information for monitoring and troubleshooting
* Selecting the type of logging information that is captured
* Specifying the destinations of captured syslog messages to

On Cisco network devices, the syslog protocol starts by sending system messages and debug output to a local logging process internal to the device. It is possible to remotely monitor system messages by viewing the logs on a syslog server or by access the device through Telnet, SSH or the console port. 

Cisco devices produce syslog messages as a result of network events. Every syslog message contains a severity level and a facility. 

###### Syslog Severity Levels
| Severity Name | Severity Level | Explanation             |
|---------------|----------------|-------------------------|
|               |                |                         |
| Emergency     | 0              | System unusable         |
| Alert         | 1              | Immediate action needed |
| Critical      | 2              | Critical condition      |
| Error         | 3              | Error condition         |
| Warning       | 4              | Warning condition       |
| Notification  | 5              | Normal but significant  |
| Informational | 6              | Information message     |
| Debugging     | 7              | Debug messages          |
|               |                |                         |


In addition to specifying the severity, syslog messages contain information on the facility. Syslog facilities are service identifiers that identify and categorize system state data for error and event message reporting. The logging facility options that are available are specific to the networking device. Common syslog message facilities reported on Cisco IOS routers include the following:
IP, OSPF Protocol, SYS operating system, IPsec, Interface IP.

#### Syslog Message Format 

[seq no][timestamp][facility][severity][mnemonic][description]

#### Configuring and verifying Syslog

By default, Cisco routers and switches send log messages for all severity levels to the console. On some Cisco IOS versions, the device also buffers log messages by default. To enable these two settings, use the ```logging console```and ```logging buffered``` global configuration commands respectively. The ```show logging``` command displays the default logging service settings on a Cisco router. To configure the router to send system messages to a syslog server, complete these steps:

1. Configure the IP address of the syslog server in global configuration mode: ```(config)# logging 192.168.1.101``` 

2. Control the messages that will be sent to the syslog server with the ```logging trap [level]``` global configuration command. ie; ```logging trap 4```

3. Optionally, configure the source interface with the ```logging source-interface [interface-type][interface number] global configuration command. This specifies that syslog packets contain the address of a specific address, regardless of which interface the packet uses to exit the router. 

## Network Time Protocol 

A log message typically lists the data and time as part of the message so that a network engineer who looks back at the message knows exactly when that message occurred.
NTP provides a way to synchronize the time-of-day clock so that timestamps are consistent across devices, making troubleshooting easier. 

To configure a router or switch to synchronize its time with an existing NTP server, use the ```ntp server``` command.
```
# ntp server 172.1.1.5

# show ntp status
# show ntp associations
```

#### Cisco IOS File System and Devices
