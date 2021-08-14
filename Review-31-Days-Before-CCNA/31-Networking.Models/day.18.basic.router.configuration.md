## Basic Router Configuration

#### Exam Topics

- Describe characteristics of network topology architectures
- Identify interface and cables issues
- Configure and verify IPv4 addressing and subnetting
- Configure and verify IPv6 addressing and prefix

#### Basic Router Configuration with IPv4

When configuring a router, certain basic tasks are performed:
* Naming the router
* Setting passwords
* Configuring interfaces
* Configuring a banner
* Saving changes on a router

| Configuration Task         | Command                            |
|----------------------------|------------------------------------|
|                            |                                    |
| Naming the router          | hostname [name]                    |
| Setting passwords          | enable secret [password]           |
| Configuring a MOTD         | banner [motd]                      |
| Configuring an interface   | interface [type][number]           |
| Saving changes on a router | copy running-config startup-config |
| show commands              | show running-config etc            |


#### Configuration Example

Walkthrough of a router configuration:
```
Router> enable
Router# config t 

Router(config)# hostname R1
R1(config)# enable secret class


#### Configure the console password and require that it be entered with the login password:

eR1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login

#### Configuring SSH and disabling Telnet are best practice, so configure the Vty lines to use only SSH

R1(config)# line vty 0 15
R1(config-line)# transport input ssh
R1(config-line)# login local
R1(config-line)# exit
R1(config)# username admin password cisco

#### Encrypt all plaintext passwords in the running configuration by using the service-password encryption

R1(config)# service-password encryption 

#### Configure the MOTD:
R1(config)# banner motd # Welcome! #

#### configure interfaces

R1(config)# interface Serial0/0/0
R1(config-if)# ip address 192.168.2.1 255.255.255.0
R1(config-if)# description Link to R3
R1(config-if)# no shutdown

#### Add routes if required.
R1(config-if)# no shutdown
R1(config-if)# copy running-config startup-config

```

#### Verification Example

The command ```show running-config``` can be used to verify the full current configuration on the router. However a few other basic commands can help verify configuration and help with troubleshooting any issues.

To check that networks are in the routing table use ```show ip route``` 
If a network is missing, check the interface status with ```show ip interface brief``` 
The output from ```show ip interface brief``` command provides three important pieces of information:
- IP address
- Line status
- Protocol status

The IP should be correct and the status codes should be up and up.

#### Interface Status Codes 

| Code            | Location    | General Meaning                        |
|-----------------|-------------|----------------------------------------|
|                 |             |                                        |
| Line status     | first code  | Refers to the Layer 1 status           |
| Protocol status | second code | Refers generally to the Layer 2 status |

#### Combinations of Interface Status Codes

| line and protocol status   | Typical Reasons                                  |
|----------------------------|--------------------------------------------------|
|                            |                                                  |
| administratively down/down | interface has a shutdown command configured      |
| down / down                | interface has a no shutdown command configured   |
| up / down                  | almost always refers to data link layer problems |
| up / up                    | all is well and the interface is functioning     |

## Basic Router Configuration with IPv6

###### Command Syntax

You enable IPv6 routing by using the following command in global configuration mode:
```
R1(config)# ipv6 unicast-routing
```

Among other actions, this command configures the router to begin listening for and responding to Neighbor Discvoery messages on all active IPv6 interfaces.

To configure an IPv6 address on a routers interface, you have one of several options:

- Configure the interface to use the EUI-64 method of addressing:
```
Router(config)# ipv6 address [ipv6-prefix/prefix-length] eui-64 
```

- Configure the full global unicast address. To manually configure a full IPv6 address, use the following command syntax:
```
Router(config)# ipv6 address [ipv6-address|prefix-length]
```

- Configure the interface as unnumbered
- Configure the interface as a DHCPv6 client

#### Configuration example

The preferred IPv6 configuration method often is to manually configure the full IPv6 address because you can control the number of hexadecimal digits you must type when testing connectivity or troubleshooting a problem. This is seen by comparing the EUI-64 method to a full configuration.
```
R1(config-if)# interface g0/0
R1(config-if) ipv6 address 2001:db8:acad:1::/64 eui-64

R1(config-if)# interface g0/1
R1(config-if) ipv6 address 2001:db8:acad:2::/64 eui-64

R1(config-if)# serial s0/0/0
R1(config-if) ipv6 address 2001:db8:acad:3::/64 eui-64

R1(config-if)# do show ipv6 interface brief

R1(config-if)# do show ipv6 interface brief

GigabitEthernet0/0 [up/up]
    FE80::2D0:97FF:FE20:A101
    2001:DB8:ACAD:1:2D0:97FF:FE20:A101

GigabitEthernet0/1   [up/up]
    FE80::2D0:97FF:FE20:A102
    2001:DB8:ACAD:2:2D0:97FF:FE20:A102

Serial0/0/0          [down/down]
   FE80::20C:CFFF:FE77:A401
   2001:DB8:ACAD:3:20C:CFFF:FE77:A401
<output omitted>
```

Notice the number of hexadecimal digits in the IPv6 addresses in the output from the ```show ipv6 interface brief``` command. These long addresses are not simple to work with, ping for example.

Furthermore, notice that the link-local addresses are also complex. To reduce the complexity of the routers configuration, verification and troubleshooting, it is good practice to manually configure the link-local address as well as the IPv6 global unicast address. 

#### Full IPv6 Address and link-local Address Configuration

Below the example is reconfigured with simpler IPv6 addresses with FE80::1 as the link-local address on all interfaces. Remember the link-local address needs to be unique only on that interfaces link. 
```
R1(config-if)# interface g0/0
R1(config-if)# no ipv6 address 2001:db8:acad:1::/64 eui-64
R1(config-if)# ipv6 address 2001:db8:acad:1::1/64
R1(config-if)# ipv6 address FE80::1 link-local

R1(config-if)# interface g0/1
R1(config-if)# no ipv6 address 2001:db8:acad:2::/64 eui-64
R1(config-if)# ipv6 address 2001:db8:acad:2::1/64
R1(config-if)# ipv6 address FE80::1 link-local

R1(config-if)# serial s0/0/0
R1(config-if)# no ipv6 address 2001:db8:acad:3::/64 eui-64
R1(config-if) ipv6 address 2001:db8:acad:3::1/64
R1(config-if) ipv6 address fe80::1 link-local

R1(config-if)# do show ipv6 interface brief
GigabitEthernet0/0     [up/up]
   FE80::1
   2001:DB8:ACAD:1::1
GigabitEthernet0/1     [up/up]
   FE80::1
   2001:DB8:ACAD:2::1
Serial0/0/0           [down/down]
   FE80::1
   2001:DB8:ACAD:3::1
<output omitted>
```

Simplifying the IPv6 addressing implementation can make verification and troubleshooting much easier.

## Verifying IPv4 and IPv6 Network Connectivity

#### Small Office or Home Office Routers Connection Options

- **Cable:** Typically offered by cable television service providers, cable transmits the Internet data signal on the same cable that delivers cable television. It provides high bandwidth, high availability, and an always-on connection to the Internet 
- **DSL:** Digitial Subscriber Line, which runs over telephone lines, provides high bandwidth, high availability, and an always on connection to the Internet
- **Cellular:** Cellular Internet access uses a cell phone network to connect. Wherever you can get a cellular signal, you can get cellular Internet access. Performance is limited by the capabilities of the phone and the cell tower to which it is connected.

- **Satellite:** Satellite Internet access is used in areas that would otherwise have no Internet connectivity at all. Satellite dishes require a clear line of sight to the satellite.

- **Dial-up telephone:** Dial-up is a low-bandwidth option that uses any phone line and a modem. Dial-up is considered a legacy technology, but you might see it on the exam.

A SOHO router is typically used to create the connection to the home user and small office connections. SOHO routers typically have two features that an enterprise router would be less likely to have:

- SOHO router almost always use the Internet and VPN technology for their WAN connections to send data back and forth to the rest of the enterprise
- A SOHO router us almost always a multifunction device that does routing, LAN switching, VPN, wireless and other features

#### Basic IP Addressing Troubleshooting 

If you are sure you manually configured the correct IP address and subnet mask/prefix, then any basic IP addressing issue is likely to be the result of a misconfigured default gateway or duplicate addresses

#### Default Gateway

A misconfigured default gateway is one of the most common problems in either a static or dynamically assigned IP addressing scheme. For a device to communicate across multiple networks, it must be configured with an IP address, a subnet mask or network prefix and a default gateway. 

The default gateway is used when the host wants to send a packet to a device on another network. The default gateway address is generally the router interface address attached to the local network to which the host is connected.

To resolve a default gateway that was manually configured incorrectly, consult the topology and addressing docs to verify what the devices default gateway should be; it is normally a router attached to the same LAN. 

#### Duplicate IP Addresses




