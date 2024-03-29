## Switch Configuration Basics

Topics:
- Identify interface and cable issues
- Configure and verify IPv4 addressing and subnetting

#### Accessing and Navigating

Two ways to configure Cisco devices:

* Console terminal: use a rollover cable or mini-usb 
* Remote terminal: use an external modem connected to the aux port to remotely configure 

After the device is configured it can be accessed using three additional methods:

* Establish a terminal vty session using telnet
* Configure the device through the previous connection
* Download a configuration file using a network management software

###### CLI EXEC Sessions

Cisco IOS seperates the EXEC session into two basic levels
- User EXEC mode: Access to a limited number of basic commands
- Privileged ECEC mode: Full access to all device commands, including configuration and management

#### Half-Duplex, Full-Duplex and Port Speed

Half-Duplex communication is unidirectional data flow in which a device can either send or receive on an Ethernet LAN - but not both at the same time. Todays LAN networking devices and end device NIC's operate at full-duplex as long as the device at the other end is also capable of full-duplex communication. This increases effective bandwidth as both ends can send and receive simultaneously. This microsegmented LAN is collision free. Gigabit and 10 gigabit NICs require full-duplex to operate. Port speed is simply the bandwidth rate of the port.

###### Auto-MDIX (Automatic-Dependent Interface Crossover)

Using auto-mdix eliminates the problem of needing to choose a crossover or straight through cable. When auto-mdix is enabled the interface automatically detects which cable is required and configures the connection appropriately. When using auto-mdix on an interface, the interface speed and duplex must be set to auto so the feature can operate 

#### Verifying Network Connectivity

The ```ping``` command can systematically test connectivity by looking for answers to the following questions, in this order:

Step 1. Can an end device ping itself?
Step 2. Can an end device ping its gateway?
Step 3. Can an end device ping the destination?

By using ping in this ordered sequence, you can isolate problems more quickly. If local connectivity is not an issue, using ```traceroute ``` can help isolate the point in the path from source to destination where the traffic stops.

#### Troubleshoot Interface and Cable Issues

The physical layer is often the reason a network issue exists, power outage, disconnected cable, power-cycled devices, hardware failures and so on. 

###### Media Issues
Besides failing hardware, common physical layer issues occur with media.

- New equipment introduces EMI 
- Cable runs too close to powerful motors
- Poor cable management puts a strain on some RJ-45 connectors, causing one or more wires to break
- New applications change traffic patterns
- When new equipment is connected to a switch the connection operates in half duplex mode or a duplex mismatch occurs - which leads to excessive collisions. 

###### Interface and Switch Configuration

In general interfaces are either up or down. However when an interface is down, the code in the ```show interfaces``` command provides more information to help determine the problem 

Line Status       : Down
Protocol Status   : Down 
Interface Status  : Disabled
Typical root cause: The interface is configured with the ```shutdown``` cmd 

Line Status       : Down
Protocol Status   : Down 
Interface Status  : notconnect
Typical root cause: No cable exists, is bad, mismatched speeds or other end device is powered off / interface is down 

Line Status       : Down
Protocol Status   : Down (err-disabled)
Interface Status  : err-disabled
Typical root cause: Port Security has disabled the interface. 

Line Status       : Up
Protocol Status   : Up
Interface Status  : connect 
Typical root cause: Interface is working

###### Duplex and Speed Mismatches 

One of the most common problems is issues with speed and/or duplex mismatches. On switches and routers the ```speed {10|100|1000}``` interface subcommand and the ```duplex {half|full}``` interface subcommand set these values. 
The command ```show interfaces status``` and ```show interfaces``` list both the speed and duplex settings on an interface. 
Both commands show the duplex and speed settings but the ```show interface status``` command is preferred for troubleshooting mismatches because it shows exactly how the switch determined the duplex and speed of the interface.

The 'a' in 'a-full' simply means the switch auto-negotiated full duplex. The full or half would mean the switch has been configured to those settings. 
Finding a duplex mismatch can be more difficult than finding a speed mismatch because if duplex settings do not match on the ends of an Ethernet segment, the switch interface will still be in an up/up state. The interface will work but the network might work poorly. To identify duplex settings check the duplex setting on each end of the link and watch for incrementing collision and late collision counters. 

###### Common Layer 1 Problems on 'UP' Interfaces

When an interface is 'UP' it may not be operating in its optimal state. For this reason Cisco IOS tracks certain counters to help identify problems that can occur even though the interface is in a connect state.

Type of problem: Excessive noise
Counter values : Many input errors, few collisions
Common causes  : Wrong cable category, EMI, damaged cables

Type of problem: Collisions 
Counter values : More than 0.1% of all frames are collisions
Common causes  : Duplex mismatch, jabber, DOS attack

Type of problem: Late collisions
Counter values : Increasing late collisions 
Common causes  : Collision domain or single cable too long, duplex mismatch
