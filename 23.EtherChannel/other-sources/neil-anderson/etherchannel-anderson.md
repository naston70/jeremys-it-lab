## EtherChannel

#### Why we have EtherChannel?

Review - Campus Design

- End hosts do not constantly send traffic onto the network, most of the time the network connection is sitting idle
- Due to this you can connect less uplinks to each higher layer than the number of hosts you have and still maintain acceptable network performance
**Oversubscription:**
* A starting recommendation for oversubscription is 20:1 from the access layer to the distribution layer
* Recommendation is 4:1 for the distribution to core layer links
* These are only general values, traffic on each network should be analyzed to verify links are not congested

- Switches often have dedicated uplink ports with higher bandwidth than their access ports
- ie, a 48 port 1Gbps switch with a pair of 10Gbps uplinks
- This can help with the subscription ratio 
- 48 x 1Gbps clients = 48Gbps
- 2 x 10Gbps uplinks = 20Gbps
- Subscription ratio of 2.4 : 1
- However, in this case, when enabling two uplinks there is a problem. STP will shutdown one link

#### Spanning Tree Load Balancing

* Spanning Tree instances provide redundancy, but not load balancing 
* If a switch has multiple equal cost paths via the same neighbor switch towards the Root Bridge, it will select the port with the lowest Port ID.

#### EtherChannel
- EtherChannel-groups multiple physical interfaces into a single logical interface
- Spanning Tree sees the EtherChannel as a single interface, so it does not block any ports 
- Traffic is load balanced across all the links in the EtherChannel
- If an interface goes down its traffic will fail over to the remaining links

#### NIC teaming
- combines multiple physical network cards into a single logical interface 

#### EtherChannel Load Balancing 
(eg from udemy)

* A flow is a communication from a client to a server
* If a PC opens a web session to a server, and another opens an FTP session to another server, there are two flows going through the switch 
* A single flow is load balanced onto a single port channel interface 
* ie the packets in one flow stay on one interface and the other flow on another interface  
* Packets from the same flow are not load balanced round robin across all the interfaces in the port channel 
* Round robin load balancing could cause packets to arrive out of order and possibly break some applications

- Any single flow receives the bandwidth of a single link in the port channel as a maximum
Etherchannel provides redundancy as well as load balancing

#### Etherchannel Protocols

- LACP - Link Aggregation Control Protocol
    * open standard
    * the switches on both sides negotiate the portchannel creation and maintenance
    * this is the preferred method

- PAGP Port Aggregation Protocol
    * cisco proprietary
    * switches on both sides negotiate the port channel creation and maintenance
    * not recommended due to its proprietary nature 

- Static Etherchannel
    * The switches do not negotiate creation and maintenance but settings must still match on both sides for the port channel to come uplinks
    * Use if LACP is nt supported on both sides

- All protocols are configured with the ```channel-group```command 

#### Etherchannel Parameters
- The switches on both sides must have matching configuration
- The member interfaces must have the same settings on both sides:
    * Speed and duplex
    * Access or Trunk
    * Native VLAN and allowed VLANs on Trunk
    * Access VLAN on access ports 

#### LACP Configuration 
- LACP interfaces can be set as either Active or Passive
- If one switch is active and the other passive, the port channel will come up
- If both sides are Passive, the port channel will not come up 
- If both sides are Active, the port channel will come up
- It is recommended to set both sides as Active

```
#interface range f0/23 - 24
#channel-group 1 mode active
(this creates interface port-channel 1)

#interface port-channel 1
#switchport mode trunk
(configure the interface settings on the port channel)
```

Matching settings would have to added on the other router

#### PAgP Configuration

- PAgP interfaces can be set as either Desirable or Auto
- If one side is desirable and the other Auto, the port channel will come upIf both sides are Auto, the port channel will not come up 
- If both sides are desirable, the port channel will come up 
- If both sides are configured as desirable you dont need to consider which side is which

```
#interface range f0/23 - 24
#channel-group 1 mode desirable 
(this creates interface port-channel 1)

#interface port-channel 1
#switchport mode trunk
(configure the interface settings on the port channel)
```


#### Static Configuration
 Exactly the same config apart from the mode:

```
#interface range f0/23 - 24
#channel-group 1 mode on
(this creates interface port-channel 1)

#interface port-channel 1
#switchport mode trunk

(configure the interface settings on the port channel
```

#### Etherchannel - show etherchannel summary 
```
#show etherchannel summary 
```

Most common error is both sides do not have a matching configuration 
```
#show spanning-tree vlan 1
```

Use to check if portchannel is up and working

#### Etherchannel across redundant switches

* Matching etherchannel settings have to be configured on the switches on both sides of the link 
* You can configure seperate port channels from a switch to redundant switches 
* spanning-tree will see the two port channels as two seperate interfaces and block one path if a loop is formed
* This brings back the problem of only using half of the available bandwidth  

* Cisco support multi-chasis etherchannel technologies on some switches
* These switches support a shared etherchannel from different switched
* The switches must have the same settings
* STP is still enabled but does not detect any loops
* This supports full load balancing and fail over 

- StackWise on catalyst switches 
- VSS Virtual Switching System
- vPC Virtual Port Channel

## Layer 3 EtherChannel

config:
```
#int range g0/1 - 2
#no switchport
#channel-group 1 mode [active | passive | desirable | auto | on]

#interface portchannel 1
#ip address 192.168.0.1 255.255.255.252
#no shutdown
```

Modern networks can remove Layer 2 switches and have Layer 3 switches for access and distribution layers. This removes the use of STP and allows for Layer 3 load balancing
