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
R1(config)#int g0/0
R1(config-if)#ip address 192.168.1.62 255.255.255.192
```

#### Layer 3) - Multilayer Switches

- A multi-layer switch is capable of both switching AND routing
- It is Layer 3 aware
- You can assign IP addresses to its interfaces, like a router
- You can create virtual interfaces for each VLAN and assign IP addresses to those interfaces
- You can configure routes on it, just like a router 
- It can be used for inter-VLAN routing

A multilayer switch is the preferred method for inter-VLAN routing

When using ROAS configuration traffic between VLANs will be routed from the switch to the router then sent back to the switch. 

Preferred method:

- SVI's (Switch Virtual Interfaces) are the virtual interfaces you can assign IP addresses to in a multilayer switch.
- Configure PC's to use the SVI (NOT the router) as their gateway address
- To send traffic to different subnets/VLANs, the PCs will send traffic to the switch and the switch will route the traffic

Steps below from day 17 .pkt network

Removing a ROAS config:
```
R1(config)#no interface g0/0.10
R1(config)#no interface g0/0.20
R1(config)#no interface g0/0.30

R1(config)#default interface g0/0
```

Once the sub interfaces have been removed a normal ip can be assigned to the interface.

On the pre-existing switch, SW2:
```
## return the port to default 

SW2(config)# default interface g0/1
SW2(config)# ip routing 
SW2(config)# interface g0/1
SW2(config-if)# no switchport
SW2(config-if)# ip address 192.168.1.193 255.255.255.252
```

The ```ip routing``` enables Layer 3 routing on the switch, it lets it build its own routing table.
Another important command is the ```no switchport``` cmd, this configures the interface as a 'routed port'. A layer 3 port not a Layer 2 switchport.

Once this is done it is possible to assign an ip to the interface as usual
```
# ip address 192.168.1.193 255.255.255.252
```

Finally a default route pointing to the router:
```
SW2(config-if)#exit
SW2(config)#ip route 0.0.0.0 0.0.0.0 192.168.1.194
SW2(config)#do show ip route
```

To confirm the route ``` do show ip route```

Configuring the SVI is straightforward:
```
SW2(config)#interface vlan10
SW2(config-if)#ip address 192.168.1.62 255.255.255.192
SW2(config-if)#no shutdown
SW2(config-if)#interface vlan20
SW2(config-if)#ip address 192.168.1.126 255.255.255.192
SW2(config-if)#no shutdown
SW2(config-if)#interface vlan30
SW2(config-if)#ip address 192.168.1.190 255.255.255.192
SW2(config-if)#no shutdown
```

SVI's are shutdown by default. If the VLAN doesnt exist on the switch it will be in a down down state

What is required for SVI to be up/up:
	- The VLAN must exist on the switch
	- The switch must have at least one access port in the VLAN in an up/up state, AND/OR one trunk port that allows the VLAN that is in an up/up state.
	- The VLAN must not be shutdown
	- The SVI must not be shutdown






