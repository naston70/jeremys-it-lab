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

Cisco IOS provides a feature called the Cisco Integrated Files System (IFS). This system enables you to create, navigate and manipulate directories on a Cisco device. Directories available depend on the platform. Syslog

#### IFS commands
```
show file system
```

Output shows columns with the amount of available and free memory, in bytes and the type of file system and its permissions. Permissions include read-only (ro) and (wo) and (rw). although several file systems are listed, TFTP, FLash and NVRAM are CCNA relevant.

The Flash file system has an (*) preceding it, which indicates that this is the current default file system. The
The ```dir``` command lists the main directory of the default file systems, whereas show flash: lists the entire contents of the default file system.

#### Listing Directory Contents for NVRAM 

The ```dir``` does show the configuration files stored in NVRAM. To see them, first cd directory to the nvram: and then list the contents using the dir command. 

#### URL Prefixes for Specifying File Locations

File locations are specified in Cisco IFS using the URL convention: tftp://192.168.1.25/configs/backup-config

Examples of URLS for accessing the local Cisco IFS include the following:
- flash:configs/backup-configs
- system:running-config
- nvram:startup-config 

#### Commands for Managing Configuration Files 

Knowing the URL structure is important because you use it when copying configuration files from one location to another. The Cisco IOS software ```copy``` command enables you to move configuration files from one component or device to another. 

###### ```copy``` Command Syntax

```
command source-url: destination url 
```

The source URRL is where you are copying from. The destination URL is where you are copying to. Such as ```copy running-config startup-config``` in the most verbose form is ```copy system:running-config nvram:startup-config``` 

Directories can be created and files saved to new directories if needed:

###### Copying Files to a Local Directory
```
# mkdir configs 
# system:running-config configs/backup-config 
```

Copy from RAM to TFTP:
```
#copy system:running-config tftp:
#copy run tftp 
```

Or from TFTP to RAM:
```
copy tftp: system:running-config 
```

The TFTP command requires more configuration, entered through prompts on the CLI.


## Managing Cisco IOS Images 

As a network grows, storing Cisco IOS Software images and configuration files on the TFTP server gives you control over the number and revision level of Cisco IOS images and configuration files that must be maintained. The ```show version``` command will verify which version is running. 


###### Backing Up a Cisco IOS images

Make sure that a TFTP server is configured and running on the network. Then follow these steps to copy a Cisco IOS Software image from Flash memory to the network TFTP server:

1. Ping the TFTP server to ensure access 
2. Copy the current system file from the router to network TFTP by using the ```copy flash: tftp:``` command in privileged EXEC mode. Then further prompts for IP, name of the source and destination system image files

###### Restoring a Cisco IOS Image

The ```dir``` or ```show flash:``` command can verify that the router has sufficient disk space to accommodate the new Cisco IOS software image. They can also help to determine:
- The total amount of Flash memory on the router
- The amount of Flash memory available 
- The names of all the files stored in the Flash memory and the amount of Flash occupied 

###### Upgrading the Cisco IOS image from a TFTP Server 
```
# copy tftp flash
```

Will lead to prompts for the address and filename. 

#### Password Recovery

Password recovery procedures for any Cisco switch or router are available online. This is why physical security is essential for all networking devices. Routers and switches should be behind closed doors. The following steps are common to most Cisco routers. Switches have similar processes:

1. Use the power switch to turn off the router and then turn the router back on.
2. Press the break key specified by your terminal software within 60 seconds of powerup to access the ROMmon prompt. 
3. Enter ```confreg 0x2142`` at the ROMmon prompt. This causes the router to bypass the startup configuration, where the forgotten password is stored.
4. Enter ```reset``` at the prompt. The router reboots, but it ignores the saved configuration. However, the file still exists in NVRAM.
5. `Ctrl+C` will skip the initial setup procedure 
6. Enter enable at the Router> prompt to enter privileged EXEC mode, where you should be able to see the Router# prompt.
7. Enter ```copy startup-config running-config``` to copy the backup NVRAM config file into memory.
8. Enter ```configure terminal```.
9. Enter the ```enable secret password``` command to change the enable secret password.
10. Issue the ```no shutdown``` command on every interface that you want to activate.
11. From global configuration mode, enter ```config-register 0x2102``` to restore the original configuration registry setting 
12. Press Ctrl+Z or enter end to leave configuration mode.
13. Enter copy running-config startup-config to commit the changes. You can issue the show ip interface brief command to confirm that your interface configuration is correct. Every interface that you want to use should display up and up


