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