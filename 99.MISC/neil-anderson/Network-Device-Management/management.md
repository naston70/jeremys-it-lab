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
- If a logging level of 7 is set for an external syslog server, events from all severity levels 0-7 will be logged there

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


