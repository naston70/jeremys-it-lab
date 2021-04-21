## DHCP Snooping

Arises when a rogue DHCP server is connected to a network. PC's can get wrong information, usually caused by users connecting devices but can also be an attack.

When DHCP snooping is enabled, DHCP server responses are dropped if they do not arrive on a trusted port.

(Switch config for when the dhcp server is coming in from f0/1)
```
#ip dhcp snooping
#ip dhcp snooping vlan 10
#int f0/1
#ip dhcp snooping trust
```

## Dynamic ARP Inspection - DAI

Man in the Middle ARP spoofing - attacker sends a gratuitous ARP claiming a MAC causing devices to update their ARP cache. Traffic goes through the attacker. Can also be used for DDoS. 

- When you enable DHCP snooping, the switch inspects the DHCP traffic and keeps track of which IP addresses were assigned to which MAC addresses
- ie PC1 with MAC 1.1.1 was assigned IP 10.10.10.10
- If invalid ARP traffic tries to pass through the switch, ie 3.3.3 saying its IP is 10.10.10.10, the switch drops the traffic

DAI is not performed on trusted ports. Enable this for non DHCP clients

(config)
```
#int f0/1
#ip arp inspection trust 
#ip arp inspection vlan 10
```

## 802.1X Identity Based Networking

- When 802.1X is enabled, only authentication traffic is allowed on switch ports until the host and user are authenticated
- When the user has entered a valid username and password, the switch port transitions to a normal access port in the relevant VLAN 

## Port Security - Preventing Unauthorised Devices 

- Best practice is to administratively shutdown unused switch ports
- This stops somebody getting access to the network if they physically connect to the port

- Port Security enables an administrator to specify which MAC address or addresses can send traffic to an individual switch port
- This can be used to lock a port down to a particular host or hosts
-  As it is easy to spoof a mac address the locking of ports down to a specific host is not usually Port Security's main role in production networks
-  Port Security can also configure individual switch ports to allow only a specified number of source MAC addresses to send traffic in to the port
-  It can learn connected MAC addresses
-  This is useful to prevent users from adding WAP's or other shared devices 
-  Configured at the port level:
Configuration (with no additional parameters):
```
#int f0/2
#switchport port-security
```
Usually enabled on all ports on the switch.
* If Port Security is configured with no additional parameters then only one MAC address is allowed to transmit on the port 
* The current MAC address device can be disconnected and replaced, the port is not locked down to a particular device
* If a shared device is connected and multiple hosts try to transmit the port will be shut down

#### Port Security Verification 
```
show port-security interface f0/2
```

Shows if enabled, the violation modes, max MAC addresses, total MAC addresses, the MAC and VLAN and a security violation count 

#### Security Violation Actions

There are three options wen an unauthorised MAC address sends traffic in to the port:

* Shutdown (default): The interface is placed into the error-disabled state, blocking all traffic
* Protect: Traffic from unauthorised addresses is dropped. Traffic from allowed addresses is forwarded
* Restrict: Traffic from unauthorised addresses is dropped, logged and the violation counter incremented. Traffic from allowed addresses is forwarded

To change the violation action:
```
#int f0/2
#switchport port-security violation protect 
or
#switchport port-security violation restrict 
```

- If the Violation Action is set to Shutdown and a violation occurs, the port will move to an error-disabled state
- To bring an error-disabled interface back into service:
    * Physically remove the host with the offending MAC address 
    * Manually shutdown and no shutdown the interface 
- This can also be achieved with Auto-Recovery
- An error-disabled port can be brought back into service automatically after they have been disabled for a configurable period of time 
```
#errdisable recovery cause psecure violation
#errdisable recovery interval 600
```

Done at a global config level.

#### Locking Ports to Hosts with Port Security 

- When Port Security is enabled the maximum number of MAC address allowed to send traffic into the interface is one by default
- This can be increased if multiple hosts share the port, for example an IP phone with a PC plugged into the back of it.
```
#interface f0/2
#switchport port-security maximum 2
```

#### Manually Adding MAC Addresses
- You can statically configure allowed MAC address if you want to lock the port down to a particular host 
```
#int f0/10
#switchport port-security
#switchport port-security mac-address 1111.1111.11af 
#switchport port-security maximum 1
```

#### MAC Address Learning

