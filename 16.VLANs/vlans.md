# VLAN's

What is a LAN?

- Can be described as a group of devices in a single location

- A more specific definition: A LAN is a single **broadcast domain**, including all devices in that broadcast domain.

- A **broadcast domain** is the group of devices which will receive a broadcast frame (FFFF.FFFF.FFFF) sent by any one of the members. 

Why use VLANs?

Performance through less broadcast traffic, security through being able to set security policy

A switch will NOT forward traffic between VLANs, including **broadcast / unknown unicast** traffic. It will only forward on other interfaces in the same VLAN

A Layer 2 switch does not perform **inter-VLAN routing.** It must send the traffic through the router.

VLANs...

* are configured on switches on a per-interface basis.
* logically seperate end hosts at Layer 2

Swtiches do not forward traffic directly between hosts in different VLANs

##### VLAN CONFIG - Basics

To see which VLANs exist on a device and the interfaces they are on:
```
SW1# show vlan brief
```
To create a VLAN on a range of interfaces:
```
SW1(config)# interface range g1/0 - 3
SW1(config-if-range)# switchport mode access
SW1(config-if-range)# switchport access VLAN 10
```

An access port is a switchport belonging to a single VLAN and usually connects to end hosts, like PC's.
Switchports which carry multiple VLANs are called 'trunk ports'

To change name of VLAN (also creates the VLAN if doesnt exist:
```
SW1(config)#vlan 10
SW1(config)#name ENGINEERING
```
