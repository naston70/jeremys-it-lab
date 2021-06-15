## Device Management 

#### Syslog

- Logging messages on Cisco devices comply with the Syslog standard
- A Syslog message is generated when something happens on the device, such as an interface going down or an OSPF neighbor adjacency coming up


* The format of the messages is: 
    - seq no: time stamp: %facility-severity-MNEMONIC:description

* Example:
```
*Oct 3 00:44:12.627: %LINK-5-CHANGED: interface fastethernet0/0, changed state to administratively down
```

#### Syslog Severity Levels 

| Value | Severity      | Description                                      |
|-------|---------------|--------------------------------------------------|
| 0     | Emergency     | System is unusable. A panic condition            |
| 1     | Alert         | A condition that should be corrected immediately |
| 2     | Critical      | Critical conditions, hard drive errors           |
| 3     | Error         | Error conditions                                 |
| 4     | Warning       | Warning conditions                               |
| 5     | Notice        | Normal but significant conditions                |
| 6     | Informational | Informational messages                           |
| 7     | Debug         | Messages for debugging                           |

#### Logging Locations 

* Syslog messages can be logged to various locations:
    - **Console line** - events will be shown in the CLI when you are logged in over a console connection. All events logged by default
    - **VTY Terminal Lines** - events will be shown in the CLI when you are logged in over a Telnet or SSH session. Not enabled by default 
    - **The logging buffer** - events saved in RAM memory, you can view them with the 'show logging' command. All events logged by default 
    - **External Syslog servers

#### Logging Locations 

- You can specify the same or different severity levels to log for each location
- All messages of that severity level and higher will be logged 
- ie, if a logging level of 3 is set for the console, events with severity 0,1,2 and 3 will be logged there
- If a logging level of 7 is set for an external Syslog server, events from all severity levels 0-7 will be logged there

#### Internal Logging Locations Configuration 
```
#no logging console 
(disables logging to the console line)

#logging monitor 6 
(events with severity level informational and higher will be logged to the VTY lines)

#logging buffered debugging 
(events with severity level 7 and higher will be logged to the buffer)
```

#### Logging to an External Syslog Server 

* You can log to an external Syslog server to centralise event reporting 
* You will typically set verbose logging to provide detailed troubleshooting information 
```
#logging 10.0.0.100
#logging trap debugging
```

#### SIEM Security Information and Event Management
- A basic Syslog server provides a centralised location for Syslog logging messages 
- A Security Information and Event Management (SIEM) system provides a centralised location for all logging messages and will typically provide advanced analysis and correlation of events 

#### Logging Synchronous 
- When working in a CLI session, by default any Syslog messages will be printed into the middle of any commands being typed 
- This can be overridden with the ```logging synchronous``` 
- This causes a new line to be printed where you were in the command 

#### Debug and Terminal monitor

* Show and Debug commands can be used to view specific information over and above the standard Syslog messages 
* Show output shows a static point in time state
* Debug output dynamically updates in real time 
* In production environments a large amount of output can overwhelm the device 
* Debug output is logged to the console line and buffer by default 
* Use the ```#terminal monitor``` command to enable debug output to the VTY lines 


## Terminal Monitor and Logging Synchronous

Lab showing use of ```terminal monitor``` command to get debug output via vty 

```
logging synchronous
```
[command to prevent debug lines interrupting what is being entered]
```
#line 0 15 vty 
#logging synchronous
```
[to apply to telnet adn ssh connections] 

#### Syslog Lab Demo Commands 

```
telnet in to 10.0.0.1
login with password 

#show logging (to see current logging level)

#no logging console (turns off logging)
#logging monitor 5
#end 
#terminal monitor 

[configure logging to the buffer]
#logging buffer 7

[external logging]
#logging 10.0.0.100
#logging trap debugging
```

## SNMP - Simple Network Management Protocol

* Open standard for network monitoring 
* An SNMP Manager can collect and organize information from an SNMP agent, which is SNMP software which runs on managed devices such as routers and switches
* The SNMP Manager is commonly called an SNMP Server or NMS (network Management System)
* The SNMP Manager can pull information from the device 'Get' or the device can push it to the server 'Trap'
* The standard also includes support for modifying Agent information from the SNMP Manager to change device behaviour

#### MIB Management Base
* Data variables on SNMP managed systems are organized in a MIB (Management Information Base)
* The SNMP Manager and Agent need to share the MIB so they know which variables can be reported on 

#### SNMP Versions 
* Three significant versions of SNMP have been developed and deployed 
* SNMPv1 uses plain text authentication between the Manager and Agent using matching community strings
* SNMPv2 also uses plain text - community strings
* SNMPv3 supports strong authentication and encryption. It is the preferred version but not all devices support

#### SNMP Community Strings

* SNMPv2 uses Community strings rather than a user name and password to authenticate the SNMP manager and Agent to each other 
* Matching community strings need to be set on both sides for the manager and agent to communicate 
* The read only (ro) community is used by the Manager to read information
* The read write (rw) community is used by the Manager to set information

#### SNMPv2c Configuration Example:
```
#snmp-server contact rob@example.com
#snmp-server location example lab 
[optional, identifies the Agent to the Manager]

#snmp-server community roblab1 ro 
#snmp-server community roblab2 rw

#snmp-server host 10.0.0.100 example1 
#snmp-server enable traps config 
[when a Configuration change is made a trap will be sent ot the NMS system 10.0.0.100 using the ro Community string]
```

#### SNMP Security Best Practice 

* Most devices use a default ro Community string of 'public' and a default Community string of 'private'
* Attackers can use this to read or set information on your devices 
* Best practice is to disable SNMP on devices where it is not used
* Use SNMPv3 with secure passwords on devices where it is used
* If SNMPv3 is not supported, use no default Community strings 

## SNMP LAB DEMO 
```
#conf t

#snmp-server contact rob@example.com
#snmp-server location example lab 

#snmp-server community roblab1 ro 
#snmp-server community roblab2 rw

#snmp-server host 10.0.0.100 example1 
#snmp-server enable traps config 

```

## SNMPv3 Configuration

* The SNMP Manager and Agent recognise each other through simple unencrypted community strings in SNMP version 1 and 2
* SNMPv3 supports authentication and encryption
* The SNMPv3 security model works with users and groups 
* A matching user account is set up on the NMS server and network device 
* Settings are derived from the group the use is a member of 

#### SNMPv3 Security Levels 
* 3 different levels are available . They are configured at the group level:
    - **noAuthnoPriv** - no authentication password is exchanged and the communications between the agent and server are not encrypted. The username serves as replacement for community string 
    - **AuthnoPriv** - Password authentication is used. No encryption is used for communications between the devices 
    - **AuthPriv** - Password authentication is used. communications between the agent and server are also encrypted  

#### SNMPv3 Configuration - Group
```
#snmp-server group example-group v3 ?
    auth        group using authNoPriv Security Level 
    noauth      group using the noAuthnoPriv Security Level
    priv        group using SNMPv3 authPriv security level 
```

```
(config)#snmp-server group example-group v3 priv ?
access      specify an access-list associated with this group
context     specify a context to associate these views for the group 
match       context name match criteria 
notify      specify a notify view for the group 
read        specify a read view for the group 
write       specify a write view for the group 
```
* Access: can be used to reference an access-list which limits the device to communicating with the IP address of the NMS server only 
* Contexts: are used on switches to specify which VLANs are accessible via SNMP 
* Views: can be used to limit what information is accessible to the NMS server
    - If a read view is not specified then all MIB objects are accessible to read
    - If a write view is not specified then no MIB objects are accessible to write
    - The NMS server gets read only access to all MIBs by default
    - The notify view is used to send notification to members of the group. If you don't specify any then it will be disabled by default 

First the group is configured, the next thing to be done is to configure the user:
#### SNMPv3 Configuration - User 
```
#snmp-server user example-user example-group v3 auth ?
    md5         use hmac md5 algorithm for authentication
    sha         use hmac sha algorithm for authentication (slower but more secure)

#snmp-server user example-user example-group v3 auth sha AUTHPW priv ?
    3des        168 bit 3DES algorithm for encryption
    aes         AES algorithm for encryption 
    des         56 bit DES algorithm for encryption 

[then the encryption level for AES encryption 128,192,256 as using AES]

FULL COMMAND:
#snmp-server user example-user example-group v3 auth sha AUTHPW priv aes 128 PRIVPW
```

## Syslog vs SNMP 

* Both Syslog and SNMP provide logging functionality
* Syslog can often provide more granular detail than SNMP but it has support for the device pushing information only (not pulling or setting from the server)
* NMS servers will typically support both Syslog and SNMP 

- There is some overlap between NMS and Security Information and Events Management products. Both can gather logging information from network infrastructure devices such as routers, switches and firewalls using protocols such as Syslog, SNMP and Netflow 

#### NMS vs SIEM
* A product which is marketed as an NMS will have a focus on collating network information and provide reports, early warning of and easier troubleshooting of network events 
* A product which is marketed as a SIEM will have a focus on collating security information and provide reports, early warnings of and easier troubleshooting of security events 



