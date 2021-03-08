# DTP and VTP

DTP - Dynamic Trunking Protocol

- DTP is a Cisco proprietary protocol that allows Cisco switches to dynamically determine their interface stattus (access or trunk) without manual configuration
- DTP is enabled by default on all Cisco switch interfaces
- So far, in this course, switchports have been configured using:
	- switchport mode access OR
	- switchport mode trunk
- For security purposes, manual configuration is recommended. DTP should be disabled on all ports

On a switch:
```
SW2(config-if)#switchport mode?
	access
	dot1q-channel
    dynamic
    private-vlan
    trunk
```

Looking at the dynamic mode, which is DTP:
```
SW2(config-if)#swtchport mode dynamic ?
	auto
	desirable
```

* A switchport in **dynamic desirable** mode will actively try to form a trunk with other Cisco switches. It will form a trunk if connected to another switchport in the following modes:
	* switchport mode trunk
	* switchport mode dynamic desirable
	* switchport mode dynamic auto


* A switchport in **dynamic auto** mode will not actively try to form a trunk with other Cisco switches, however it will form a trunk if the switch connected to it is actively trying to form a trunk. It will form a trunk with a switchport in the following modes:
	* switchport mode trunk
	* switchport mode dynamic desirable

DTP modes and outcomes:

| Administrative  mode | Trunk | Dynamic  Desirable | Access | Dynamic Auto |
|----------------------|-------|--------------------|--------|--------------|
| Trunk                | Trunk | Trunk              | X      | Trunk        |
| Dynamic Desirable    | Trunk | Trunk              | Access | Trunk        |
| Access               | X     | Access             | Access | Access       |
| Dynamic Auto         | Trunk | Trunk              | Access | Access       |
