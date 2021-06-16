## Syslog

- Syslog is an industry standard protocol for message logging
- On network devices, Syslog can be used to log events 
- The messages can be displayed in the CLI, saved in RAM or sent to an external Syslog server
- Syslog and SNMP are both used for monitoring and troubleshooting of devices. They are complementary, but their functions are different.

#### Syslog Message Format

```
seq:time stamp: :%facility-severity-MNEMONIC:description
```

seq: a sequence number indicating the order of messages
time stamp: a time stamp indicating the time the message was created
facility: a value that indicates which process on the device generated the message
severity: a number that indicates the severity of logged event 
MNEMONIC: a short code for the message, indicating what happened
description: detailed information about the event being reported

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

0     1       2     3        4    5    6         7
Every Awesome Cisco Engineer Will Need Ice-cream Daily

#### Syslog Logging Locations

* Console Line: Syslog messages will be displayed in the CLI when connected to the device via console port. By default, all messages are displayed

* VTY lines: Sylog messages will be displayed in the CLI when connected to the device via telnet/ssh - disabled by default

* Buffer: Syslog messages will be saved to RAM. By default, all messages are displayed 

* External server: You can configure the device to send Syslog messages to an external server
    - syslog servers will listen for messages on UDP port 514
