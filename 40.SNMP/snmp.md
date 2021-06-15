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






