## LAN Security and Device Hardening

## Exam Topics
- Configure device access control using local passwords
- Configure network devices for remote access using SSH
- Differentiate authentication, authorizing and accounting concepts
- Configure Layer 2 security features (DHCP snooping, dynamic ARP inspection and port security)

## Endpoint Security 

Endpoints are hosts including laptops, desktops, servers, and IP phones. In addition, a network that has a BYOD policy includes employee owned devices. Endpoints are particularly susceptible to malware-related attacks that originate through email or web browsing. If an end point is infiltrated, it can become a point from which a threat actor can gain access to critical system devices, such as servers and sensitive information. 

Endpoints are best protected by host-bases Cisco Advanced Malware Protection (AMP) software. AMP products include endpoint solutions such as Cisco AMP for Endpoints. In addition, content security appliances provide fine-grained control over email and web browsing for an organizations users. 

Cisco has two content security appliance products:
- Cisco Email Security Appliance (ESA)
- Cisco Web Security Appliance (WSA)

#### Cisco ESA 

Cisco ESA is a special device designed to monitor emails primary protocol, SMTP, Cisco ESA can do the following:

- Block known threats
- Remediate against stealth malware that evades initial detection
- Discard emails with bad links
- Block access to newly infected sites
- Encrypt content in outgoing email to prevent data loss

#### Cisco WSA

Cisco WSA combines advanced malware protection application visibility and control, acceptable use policy controls and reporting. Cisco WSA provides complete control over how users access the Internet. Certain features and applications such as chat, messaging, video and audio can be allowed, restricted with time and bandwidth limits or blocked, according to the organizations requirements. WSA can perform blacklisting of URLs, URL filtering, malware scanning, URL categorization, Web application filtering and encryption and decryption of web traffic.  

## Access Control 

Many types of authentication can be performed on networking devices to control access and each method offers varying levels of security

#### Local Authentication 

The simplest method of remote access authentication is to configure a login and password combination on console, vty lines and aux ports. This method however provides no accountability and the password is seen in plaintext. Anyone with the password could gain access to the device.
```
# line vty 0 4
# password ci5co
# login
```

Instead of using a shared password with no usernames, it is possible ti use the:
```
# username [username]
# secret [password]
```

command to configure local username/password pairs. Require a username/password paid with the **login local** line configuration command. Use the **no password** line configuration command to remove any configured passwords. 

#### SSH Configuration 

Secure Shell (SSH) is considered a security best practice as Telnet (Port 23) uses insecure plaintext transmission of both login and data across the connection. SSH (port 22) is a more secure form of remote access:

- It requires a username and password, both of which are encrypted during transmissions
- The username and password can be authenticated using the local database method
- It provides more accountability because the username is recorded when a user logs in
###### Configuring SSH Remote Access on a Switch
```
# show ip ssh
# conf t
# ip domain-name [example.com]
# crytpo key generate rsa
How many bits in the modulus [512]:1024
...
# line vty 0 15
# login local
#transport input ssh
#username abc123 secret cisco123
```

#### Steps of SSH Configuration

1. Verify that the switch supports SSH using the show ip ssh command. If the command is not recognized, you know that SSH is not supported.

2. Configure a DNS domain name with the ip domain-name global configuration command.

3. Configure the switch using the crypto key generate rsa command to generate an RSA key pair and automatically enable SSH. When generating RSA keys, you are prompted to enter a modulus length. Cisco recommends a minimum modulus size of 1024 bits

4. Change the vty lines to use usernames, with either locally configured usernames or an authentication, authorization, and accounting (AAA) server. In the previous example, the login local vty subcommand defines the use of local usernames, replacing the login vty subcommand.

5. Configure the switch to accept only SSH connections with the transport input ssh vty subcommand. (The default is transport input telnet.)

6. Add one or more username password global configuration commands to configure username/password pairs.

7. If desired, modify the default SSH configuration to change the SSH version to 2.0, the number of authentication tries, and the timeout

8. Verify your SSH parameters by using the show ip ssh command

#### Switch Port Hardening 

Router interface must be activated with the **no shutdown** command before they become operational. The opposite is true for cisco catalyst switches; an interface becomes active when a device is connected to the port. Cisco chose a default configuration that includes interfaces that work without any configuration, including automatically negotiating speed and duplex. In addition all interfaces are assigned to the default VLAN 1.

This default configuration exposes switches to some security threats. The following are security best practices unused interfaces:

* Administratively disable the interface by using the **shutdown** interface subcommand
* Prevent VLAN trunking by making the port a nontrunking interface uses the **switchport mode** access interface subcommand
* Assign the port to an unused VLAN by using the **switchport access vlan [number] interface subcommand
* Set the native VLAN not to be VLAN 1 but instead to be an unused VLAN, using the **switchport trunk native vlan [vlan-id]** interface subcommand.

Even when you shut down unused ports on the switches, if a device is connected to one of those ports and the interface is enabled, trunking can occur. In addition, all ports are in VLAN 1 by default. A good practice is to put all unused ports in a black hole VLAN. 
```
# vlan 999
# name BlackHole
# interface range fa0/20 - 24 
# shutdown
```


## AAA 

Configuring usernames and passwords on every device is not very scalable. A better option is to use an external server to centralize and secure all username/password pairs. To address this issue, Cisco devices support the AAA framework to help secure device access. 

Cisco devices support two AAA authentication protocols

- Terminal Access Control Access Control System Plus
- Remote Authentication Dial In User Service

The choice of TACACS+ or RADIUS depends on the needs of the organization. Ie, a large ISP might select RADIUS because it supports the detailed accounting required for billing users. AN org with various user groups might select TACACS+ because it requires authorization policies to be applied on a per-user or per-group basis

###### TACACS+ vs RADIUS

| Feature              | TACACS+         | RADIUS    |
|----------------------|-----------------|-----------|
| Most often used for  | Network devices | Users     |
| Transport Protocol   | TCP             | UDP       |
| Auth port numbers    | 49              | 1645,1812 |
| Encrypts password?   | Yes             | Yes       |
| Encrypts packet?     | Yes             | No        |
| Supports subsetting  | Yes             | No        |
| Defined by:          | Cisco           | RFC 2865  |

Both TACACS+ and RADIUS use a client/server model, where an authenticating device is the client talking to an AAA server. 

## 802.1X

IEEE 802.1X is a standard port-based access control and authentication protocol. It is ideal for restricting unauthorized access through publicly available LAN devices, such as switches and wireless access points. 

802.1X defines three roles for devices in the network:

* **Client (supplicant):** This is usually the 802.1X-enabled port on the device that requests access to LAN and switch services and responds to requests from the switch. 
* **Switch (authenticator):** The switch controls physical access to the network, based on the authentication status of the client. The switch acts as a proxy between status of the client. The switch acts as a proxy between the client and the authentication server. It requests identifying information from the client, verifies that information with the authentication server, and relays a response to the client
* **Authentication server:** The authentication server performs the actual authentication of the client. The authentication server validates the identity of the client and notifies the switch about whether the client is authorized ot access the LAN and switch services. 

The 802.1X process is summarized as follows:

* The RADIUS authentication server is configured with usernames and passwords
* Each LAN switch is enabled as an 802.1X authenticator, is configured with the IP address of the authentication server and 802.1X enabled on all required ports 
* Users that connect devices to 802.1X- enabled port must know the username/password before they can access the network

## Port Security 

If you know which devices should be cabled and connected to particular interfaces on a switch, you can use port security to restrict that interface so that only the expected devices can use it. This reduces exposure to some type of attacks in which the attacker connects a laptop to a wall socket or uses the cable attached to another end device to gain network access.

#### Port Security Configuration 

Port security involves several steps. The port needs to be made an **access port**, which means it cannot do nay trunking. Port security needs to be enabled and the Media Access Control addresses of the allowed devices added to that port.

1. Configure the interface for static access mode by using the **switchport mode access** command
2. Enable port security by using the **switchport port-security** command before
3. (Optional) Override the maximum number of allowed MAC addresses associiated with the interface by using the **switchport port-security maximum [number]** interface subcommand
4. (Optional)Override the default action when there is a security violation by using the **switchport port-security violation {protect|restrict|shutdown}** command 
5.(Optional) Predefine any allowed source MAC addresses for this interface by using the **switchport port-security mac-address [mac-address]** interface
6. (Optional) Instead of step 5, configure the interface to dynamically learn and configure the MAC addresses of currently connected hosts by configuring the **switchport port-security mac-address sticky** command 

When an unauthorized device attempts to send frames to the switch interface, the switch can issue informational messages, discard frames from that device or even discard frames from all devices by effectively shutting down the interface. Exactly which action the switch port takes depends on the option configured in the **switchport port-security violation** command

| option                      | protect | restrict | shutdown |
|-----------------------------|---------|----------|----------|
| discards offending traffic  | Yes     | Yes      | Yes      |
| sends log and SNMP messages | No      | No       | Yes      |
| Disables the interface      | No      | No       | Yes      |

example: port security configuration in which each access interface is allowed a max of 3 MAC addresses. If a fourth MAC address is detected, only the offending devices traffic is discarded. If the violation option is not explicitly configured, the traffic for devices that are allowed on the port is discarded because the port would be shutdown by default 
```
# interface range fa 0/5 - fa 0/24 
# switchport mode access
# switchport port-security 
# switchport port-security maximum 3 
# switchport port-security violation restrict 
# switchport port-security mac-address sticky 
```

To verify port security configuration, use the more general **show port-security** command or the more specific **show port-security interface [type number]**

#### Port Security Aging 

Port security aging can be used to set the aging time for static and dynamic secure addresses on a port. Two types of aging are supported per port:

* **Absolute:** The secure addresses on the port are deleted after the specified aging time. 
* **Inactivity:** The secure addresses on the port are deleted only if they are inactive for the specified aging time.

Use the **switchport port-security aging** command to enable or disbale static aging for the secure port or to set the aging or type:
```
# switchport port-security aging {static|time} type {absolute|inactivity}
```

| Parameter       | Description                                                   |
|-----------------|---------------------------------------------------------------|
| static          | enable aging for statically configured secure addresses       |
| time            | Specify again. 0-1440 mins. 0 = disabled                      |
| type absolute   | Set absolute aging time. All address age out after set time   |
| type inactivity | Set inactivity aging time. Address age out if no data in time |


#### Port Restoration After a Violation

When port security is activated on an interface, the default action when a violation occurs is to shut down the port. A security violation can occur in one of two ways:

- The maximum number of secure MAC addresses has been added to the address table for that interface, and a station whose MAC address is not in the address table attempts to access the interface
- An address learned or configured on one secure interface is seen on another secure interface in the same VLAN 

When a violation occurs, a syslog messages is sent to the console, stating that the interface is now in the **err-disable** state. The console messages include the port number and the MAC address that caused the violation

You can use the **show interface [type number] status** or **show port-security interface [type number]** to verify the current state of the port. To restore the port, you must first manually shutdown the interface and then reactivate it.

## LAN Threat Mitigation

#### Native and Management VLAN Modification 

The IEEE 802.1Q specification defines a native VLAN to maintain backward compatibility with untagged traffic that is common in legacy LAN scenarios. A native VLAN serves as a common identifier on opposite ends of a trunk link. VLAN 1 is the native VLAN by default.

A management VLAN is any VLAN configured to access the management capabilities of a switch. VLAN 1 is the management VLAN by default. The management VLAN is assigned an IP address and subnet mask, allowing the switch to be managed through HTTP, Telnet, SSH or SNMP.

It is best practice to configure the native VLAN as an unused VLAN distinct from VLAN 1 and other VLANs. In fact, it is not unusual to dedicate a fixed VLAN to server the role of the native VALN for all trunk ports in the switched domain. Likewise the management VLAN should be configured as something other than VLAN 1, native and management vlans can be configured as the same VLAN.
```
# vlan 86
# name Management&Native
# interface vlan 88
# ip address 10.10.88.10 255.255.255.0
# no shutdown
# ip default-gateway 10.10.88.254
# interface range fa0/20 - 24 
# switchport mode trunk
# switchport trunk native vlan 88
```

First the VLAN is created. Next, by activating the interface VLAN 88, the switch can be remotely managed. Finally the trunk ports are statically configured and VLAN 86 is set as the native VLAN for all untagged traffic

#### VLAN Attacks

VLAN attacks can be launched in one of three ways:

* **Spoof dynamic trunking protocol (DTP) messages:** Spoofing DTP messages from the attacking host can cause the switch to enter trunking mode. From here, the attacker can send traffic tagged with the target VLAN, and the switch then delivers the packets to the destination. 
* **Introducing a rogue switch and enabling trunking:** After doing this, an attacker can access all the VLANs on the victim switch from the rogue switches
* **Mounting a double-tagging attack:** This type of VLAN hopping attack takes advantage of the way hardware on most switches operates. A threat actor in specific situations could embed a hidden 802.1Q tag inside the frame which already has one. This tag allows the frame to go to a VLAN that the original tag didnt specify

#### VLAN Attack Mitigation

To stop VLAN hopping attacks:

1. Disable DTP negotiations on non trunking ports by using the switchport mode access interface configuration command. 
2. Disable unused ports and put them in an unused VLAN
3. Manually enable the trunk link on  trunking port by using the **switchport mode trunk** command
4. Disable DTP negotiations on trunking ports by using the **switchport nonegotiate** command
5. Set the native VLAN to a VLAN other than VLAN 1 by using the ```switchport trunk native vlan [vlan-number]``` command

## DHCP Attacks






