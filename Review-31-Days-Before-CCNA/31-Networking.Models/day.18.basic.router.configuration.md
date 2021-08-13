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

R1(config)# line console 0
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

