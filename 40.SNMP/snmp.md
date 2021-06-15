## SNMP - Simple Network Management Protocol

* SNMP is an industry standard framework and protocol originally released in 1988
* SNMP can be used to monitor the status of devices, make configuration changes, etc

* There are two main types of devices in SNMP:
    1) Managed Devices:
    - These are the devices being managed using SNMP
    - For example, network devices like routers and switches

    2) Network Management Systems (NMS)
    - The device/devices managing the managed devices 
    - This is the SNMP 'server'

#### SNMP Operations

- There are three main operations used in SNMP:
1. Managed devices can notify the NMS of events
2. The NMS can ask the managed devices for information about their current status
3. The NMS can tell the managed devices to changes aspects of their configuration

#### SNMP Components
- The **SNMP Agent** is the SNMP software running on the managed devices that interacts with the SNMP Manager on the NMS -> it sends notifications to/receives messages from the NMS 
- The **Management Information Base (MIB)** is the structure that contains the variables that are managed by SNMP.
    * Each variable is identified with an object ID (OID)
    * Example variables: interface status, traffic throughput, CPU usage, temperature etc

- SNMP Object IDs are organized in a hierarchical structure.
- .1 .3  .6  .1  .2  .1  .1  .5
- iso, organizaion, dod, internet, mgmt, mib-2, system, sysName

An NMS would ask: 'What value do you have for OID .1.3.6.1.2.1.1.5'
and the device would reply: 'My value for OID .1.3.6.1.2.1.1.5 is SW1'

#### SNMP Versions

- Many versions of SNMP have be proposed/developed, however only three major versions have achieved wide-spread use:

* SNMPv1:
    - Original 

* SNMPv2c:
    - Allows the NMS to retrieve large amounts of information with a single request, so it is more efficient
    - 'c' refers to the community strings used as passwords in SNMPv1, removed from SNMPv2, and then added back for SNMPv2c

* SNMPv3
    - A much more secure version of SNMP that supports strong encryption and authentication

#### SNMP Messages

Message Class:

**Read**: messages sent by the NMS to read information from managed devices
*Messages*: ```Get, GetNext, GetBulk``` 

**Write**: messages sent by the NMS to change information on the devices
*Messages*: ```Set```

**Notification**: Messages sent by the devices to alert the NMS of an event
*Messages*: ```Trap, Inform```

**Response**: Messages sent in response to a previous messages/request
*Messages*: ```Response```

#### SNMP SUMMARY

- SNMP helps manage devices over a network

- **Managed Devices** are the devices being managed using SNMP, such as network devices (routers, firewalls, switches)
- **Network Management Stations (NMS)** are the SNMP 'servers' that manage the devices
    * NMS receives notifications from managed devices
    * NMS changes settings on managed devices 
    * NMS checks status of managed devices 

- Variables such as interface status, temp, loads, host name, etc are stored in the MIB - management information base and identified using Object IDs 
- Main versions: SNMPv1, SNMPv2c and SNMPv3
- SNMP messages: Get, GetNext, Set, Trap. Inform, Response 




