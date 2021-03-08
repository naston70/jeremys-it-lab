# Native VLAN


Setting the native VLAN:
```
SW1(config)#int g0/0
SW1(config-if)# switchport trunk native vlan 1001
```


There are two methods of configuring the native VLAN on a router:
	1) Use the command: ```encapsulation dot1q vlan-id native``` on the router subinterface
	2) Configure the IP address for the native VLAN on the routers physical interface (encapsulation command is then not necessary)

#### Method 1)
```
R1(config)# int g0/0.10
R1(config-subif)#encapsulation dot1q 10 native
R1(config-subif)
```

#### Method 2)
```
R1(config)#no int g0/0.10
R1(config)# int g0/0
R1(config-if)#ip address 192.168.1.62 255.255.255.192
```

### Layer 3 - Multilayer Switches

- A multi-layer switch is capable of both switching AND routing
- It is Layer 3 aware
- You can assign IP addresses to its interfaces, like a router
- You can create virtual interfaces for each VLAN and assign IP addresses to those interfaces
- You can configure routes on it, just like a router
