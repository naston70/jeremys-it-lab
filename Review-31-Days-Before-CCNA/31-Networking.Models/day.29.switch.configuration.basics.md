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