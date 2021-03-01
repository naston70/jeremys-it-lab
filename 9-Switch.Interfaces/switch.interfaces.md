# Interfaces

**Router** interfaces have the shutdown command applied by default, so will be in the administratively ```down/down`` state by default

**Switches** do NOT have the shutdown command applied so will be in the ```up/up``` state if connected to another device or ```down/down``` if not connected

### Useful Commands

```
SW1>en
SW1#sh ip int br 

Interface 				IP-Address		OK?		Method		Status		Protocol

FastEthernet0/1			unassigned		Yes		unset		up			up
```


```
SW1#show interfaces status

Port 		Name 		Status 		Vlan 	Duplex 		Speed 		Type
Fa0/1					connected	1		a-full		a-100		10/100BaseTX
```

Port field simply lists the interface
Name is simply a description
Status, connected and few other states
Vlan, Vlan the interface is in
Duplex, indicates whether device is capable of full duplex (auto by default on cisco)
a (auto) full (duplex)
Speed, auto negotiates the speed with device its connected to and speed. 
Type is the connection type 

### Full and Half Duplex

**Half duplex:** The device cannot send a receive data at the same time. If it is receiving a frame it must wait before sending a frame

**Full duplex:** The device can send and receive data at the same time. It does not have to wait

In a half duplex situation, within a collision domain, to avoid collisions occurring when frames are sent out at the same time CSMA/CD is used:

##### Carrier Sense Multiple Access with Collision Detection

* Before sending frames, devices 'listen' to the collision domain until they detect that other devices are not sending.
* If a collision does occur, the device sends a jamming signal to the other devices that a collision happened.
* Each device then will wait a random period of time before sending frames again
* The process repeats

Switches outperforming hubs removed most of the need for this

##### Speed/Duplex Autonegotiation

- Interfaces that can run at different speeds (10/100 or 10/100/1000) have default settings of ```speed auto```and ```duplex auto``

- Interfaces 'advertise' their capabilities to the neighbouring device, and they negotiate the best ```speed```and ```duplex```settings they are both capable of 
- 


