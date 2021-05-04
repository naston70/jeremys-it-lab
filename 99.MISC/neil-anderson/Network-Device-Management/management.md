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