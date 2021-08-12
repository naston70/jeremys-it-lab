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


