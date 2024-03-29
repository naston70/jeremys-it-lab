## Inter VLAN Routing

## Exam Topics
* Configure and verify IPv4 addressing and subnetting
* Configure and verify interswitch connectivity

Concepts:

Inter-VLAN communications cannot occur without a layer 4 device. Three options are available while implementing inter-vlan routing.

- Traditional or legacy inter-VLAN routing 
- Router on a Stick
- Multilayer switching 

## Legacy Inter-VLAN Routing 

Legacy Inter-VLAN routing requires multiple physical interfaces on both the router and the switch. When using a router to facilitate inter-VLAN routing, the router interfaces can be connected to seperate VLANs. Devices on those VLANs send traffic through the router to reach other VLANs. 

#### Router on a Stick

Today router software makes it possible to configure one router interface as multiple trunks by using subinterfaces. 

A physical interface can be logically subdivided into two logical interfaces. The one switch is configured to trunk multiple VLANs and each subinterface on the router is assigned a seperate VLAN. The router performs inter-VLAN routing by accepting VLAN-tagged traffic on the trunk interface coming from the adjacent switch. The router then forwards the routed traffic, VLAN-tagged for the destination VLAN, out the same physical interface that it used to receive the traffic. 

#### Multilayer Switching 

 Router on a stick works fine in a small business with one or two routers. But for the most scalable solution in enterprise networks today is to use a multilayer switch to replace both the router and switch. A Multilayer Layer switch performs both functions; switching traffic within the same VLAN and routing traffic between VLANs

 Multilayer switching is more scalable than any other routing implementation for two main reasons:
 
 - Routers have a limited number of available interface to connect to networks
 - Limited amounts of traffic can be accommodated on the physical line at one time 

With a multilayer switch, packets are forwarded down a single trunk line to obtain new VLAN tagging information. A multilayer switch does not completely replace the functionality of a router but can be thought of as a layer 2 device that is upgraded to have some routing capabilities. 

## Router on a Stick Configuration and Verification

When configuring inter-VLAN routing using the ROAS model, the physical interface of the router must be connected to a trunk link on the adjacent switch. On the router, subinterfaces are created for each unique VLAN on the network. Each subinterface is assigned an IP address specific to its subnet/VLAN and is also configured to tag frames for that VLAN. This way, the router can keep the traffic from the different subinterfaces seperated as it traverses the trunk link back to the switch. 

###### ROAS Configuration

1. Activate the physical interface that is trunking with the switch by using the **no shutdown** command

2. Enter subinterface configuration mode for the first VLAN. Convention is to use the VLAN number as the subinterface number

3. Configure the trunking encapsulation type by using the subinterface configuration command ```encapsulation [dot1q|isl] vlan-number```

4. Configure IP and subnet mask 

5. Repeat as need for additional VLANs

#### Verification of Inter-VLAN Routing Configuration

To verify the configuration, use the ```show vlans```, ```show ip route``` and ```show ip interface brief``` commands to make sure the new networks are in the routing table and the subinterfaces are up/up

## Multilayer Switching Inter-VLAN Routing Configuration and Verification

Most enterprise networks use multilayer switches to achieve high packet processing rates using hardware based switching. All Catalyst multilayer switches support the following types of Layer 3 switches:

- **Switched virtual interface (SVI)**: Virtual VLAN interface used for inter-VLAN routing 

- **Routed Port:** Similar to a physical interface on a Cisco IOS router

#### Creating Additional SVIs

The SVI for the default VLAN 1 already exists to permit remote switch administration.

Create an SVI by using the ```interface vlan [vlan-id]``` command. The vlan-id used corresponds to the VLAN tag associated with data frames coming from that VLAN. In addition, the switch must be configured to do Layer 3 routing with the ```ip routing```global configuration command. 

###### Advantages of SVIs
* They are much faster than ROAS because everything is hardware switched and routed
* No external links are needed from the switch to the router for routing 
* They are not limited to one link. Layer 2 EtherChannels can be used between the switches to get more bandwidth
* Latency is much lower because it does not need to leave the switch

#### Configuring a Switch to Use SVIs for Routing 
```
# ip routing
# vlan 10
# vlan 30
# interface vlan 10
# ip address 172.17.10.1 255.255.255.0
# interface vlan 30
# ip address 172.17.30.1 255.255.255.0
# interface f0/11
# switchport mode access
# switchport access vlan 10
# interface f0/6 
# switchport mode access
# switchport access vlan 30
```

As the ```ip routing``` command is configured, the switch has a routing table.

#### Configuring a Layer 3 Routed Port

To configure an interface as a routed port, turn off switching with the ```no switchport``` interface command. Then the IP address can be configured as normal. The ```ip routing```command was enabled in the previous step However the Layer 3 switch still needs a default route to send traffic to the Internet

```
# interface g0/1
# no switchport 
# ip address 192.0.0.2 255.255.255.0
# ip route 0.0.0.0 0.0.0.0 g0/1
```




