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