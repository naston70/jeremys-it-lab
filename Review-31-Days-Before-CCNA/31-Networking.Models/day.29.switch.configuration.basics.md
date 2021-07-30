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
