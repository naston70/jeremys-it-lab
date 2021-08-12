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
