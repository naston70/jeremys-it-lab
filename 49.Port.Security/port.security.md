## Port Security

What is Port Security?

- Port security is a feature of Cisco switches
- It allows you to control which source MAC addresses are allowed to enter the switchport
- If an unauthorized source MAC address enters the port, an action will be taken
	- The default action is to place the interface in the 'err-disabled' state
	
- When you enable port security on an interface with default settings, one MAC address is allowed
	* You can configure allowed MAC addresses manually
	* If not, the switch will allow the first source MAC address that enters the switch 

- You can change the maximum number of allowed MAC addresses

##### Why Port Security?

* Port security allows a network admin to control which devices are allowed access to the network
* However, MAC address spoofing is a simple task
* Rather than manually specifying the MAC addresses allowed on each port, port security's ability to limit the number of MAC addresses allowed on an interface is more useful 

* Limiting the number of MAC addresses on an interface can protect against attacks, such as DHCP starvation by only only a MAX number of MAC addresses through the interface


#### Violation Modes

* Shutdown (default):
	- effectively shuts down the port by placing it in an err-disabled state
	- generates a Syslog and/or SNMP message when the interface is disabled
	- the violation counter is set to 1 when the interface is disabled 

* Restrict:
	- the switch discards traffic from unauthorized MAC addresses
	- the interface is not disabled 
	- generates a Syslog and/or SNMP message each time an unauthorized MAC is detected
	- violation counter is incremented by 1 
	
* Protect
	- switch discards traffic from unauthorized MAC addresses
	- the interface is not disabled 
	- it does not generate Syslog/SNMP messages for unauthorized traffic