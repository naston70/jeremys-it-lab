## Security Fundamentals

1. Which term describes the outside of the corporate firewall? 
- A. DMZ
- B. Perimeter 
- C. Internal
- D. Trusted

A. B, outside of the corporate firewall, generally holds equipment necessary for routing to the ISP.

2. Which term describes the area accessible to the Internet yet protected by the corporate firewall?
- A. DMZ
- B. Perimeter 
- C. Internal 
- D. Trusted

A. A - The DMZ is an area protected by the corporate firewall. The DMZ area is in between the perimeter network and the internal network.

3. Which type of device can prevent an intrusion on your network? 
- A. Honey pots
- B. IDS 
- C. IPS 
- D. HIDS

A. C

4. When dealing with firewalls, the term trusted network is used to describe what?
- A. Internal network
- B. The Internet
- C. The DMZ
- D. A network with SSL

A. A.

5. Which is a common attack method used to overwhelm services with traffic from multiple Internet sources?
- A. Denial of service
- B. Distributed denial of service 
- C. IP address spoofing
- D. Session hijacking

A. B.

6. Which type of device can detect an intrusion on your network? 
- A. Honey pots
- B. IDS
- C. IPS
- D. HIDS

A. B.

7. Which method can be used to stop ping sweep scans?
- A. Deploying host intrusion detection systems
- B. Deploying network intrusion detection systems
- C. Blocking RFC 1918 addresses at the perimeter
- D. Blocking ICMP echo requests and echo replies at the perimeter

A. D

8. Which appliance can be used to mitigate denial of service attacks? 
- A. Honey pots
- B. IDS 
- C. IPS 
- D. HIDS

A. C, an IPS will help mitigate denial of service attacks. 

9. Which is a common attack method used to attempt to gain access to a system using a false identity?
- A. Denial of service
- B. Distributed denial of service 
- C. IP address spoofing
- D. Session hijacking

A. C.

10. Which method would prevent tampering of data in transit? 
- A. Access control lists (ACLs)
- B. Spoofing mitigation
- C. SSL
- D. Encryption of the data

A. C. SSL offers both Encryption and authentication of the data via certificate signing. This would prevent tampering end to end. 

11. A rouge wireless access point (WAP) is created with the same SSID as the corporate SSID. The attacker has employees connect to the SSID and watches the information as it’s relayed to the original SSID. What type of attack is described here?
- A. Smurf attack
- B. Compromised key attack 
- C. Sniffer attack
- D. Man in the middle attack

A. D.

12. What can you use to protect against spoofing of internal IP addresses on the perimeter of your network?
- A. ACLs
- B. Intrusion detection systems
- C. SSL
- D. Host intrusion detection systems

A. A, ACLs are an effective way to mitigate spoofing of internal IPs from outside the trusted network. ACLs are used to control traffic by either allowing, denying or logging traffic depending on specific conditions. 

13. Which is a requirement for the use of DHCP snooping to protect a device?
- A. The device is on a layer 2 switched port on the same VLAN.
- B. The DHCP server is running on the layer 2 switch.
- C. The device is on a layer 3 routed port on the same VLAN.
- D. Configuration of a dedicated IP address for monitoring DHCP transactions.

A. A, a requirement of DHCP snooping is that the device is on the VLAN and that DHCP snooping is monitoring

14. What attack vector can be used for a man in the middle attack? 
- A. DHCP
- B. DNS
- C. Wireless
- D. All of the above

A. D. 

15. Which attack can be used on a native VLAN?
- A. Double tagging
- B. VLAN traversal 
- C. Trunk popping 
- D. Denial of service

A. A, double tagging is an attack that can be used against the native VLAN. The attacker will tag the native VLAN on a frame and then tag another inside that frame for the VLAN that the attacker intends to compromise. When the switch receives the first frame, it removes the default VLAN tag and forwards it to other switches via a trunk port. 

16. Which command is used to configure the port of a switch as trusted for DHCP snooping?
- A. Switch(config-if)#ip dhcp snooping trust
- B. Switch(config-if)#dhcp snooping trust
- C. Switch(config)#ip dhcp snooping trust interface gi 2/3 
- D. Switch(config-if)#ip dhcp trust

A. A. [ip dhcp snooping trust]

17. Why should you always change the native VLAN?
- A. The native VLAN contains frames from all VLANs.
- B. The native VLAN is configured on all switches for logging. 
- C. The native VLAN is the default on all switch ports.
- D. The native VLAN provides no encryption.

A. C, The native VLAN is the default configuration on all switches. It is very possible that a user could be configured by accident for the native VLAN of 1. This would allow management access to switching and routing

18. What can protect users from a phishing attack that is sent via email? 
- A. Training
- B. Anti-malware software 
- C. Antivirus software
- D. Certificates

A. A.

19. Your company provides medical data to doctors from a worldwide database. Because of the sensitive nature of the data, it’s imperative that authentication be established on each session and be valid only for that session. Which of the following authentication methods provides credentials that are valid only during a specific period of time?
- A. Token
- B. Certificate 
- C. Smart card 
- D. License

A. A.

20. A user has brought an email to your attention that is not from his bank, but it looks like his bank’s website when he clicks on the link. What is this most likely?
- A. Spam
- B. Password cracking 
- C. Phishing
- D. Worm

A. C.

21. What type of filters can be placed over a monitor to prevent the data on the screen from being readable when viewed from the side?
- A. Security
- B. Privacy
- C. Degaussing 
- D. Tempered

A. B, privacy filters are either film or glass add-ons that are placed over a monitor. They prevent the data on the screen from being readable when viewed from the sides. 

22. Which form of social engineering is nothing more than looking over someone’s shoulder while they enter or view sensitive information?
- A. Shoulder surfing 
- B. Phishing
- C. Tailgating
- D. Whaling

A. A. 

23. Several office-level users have administrative privileges on the network. Which of the following is the easiest to implement to immediately add security to the network?
- A. Biometric authentication 
- B. Hardware tokens
- C. Active Directory
- D. Least privilege

A. D, by implementing least privilege and removing the administrative privileges from the office workers.

24. You need to protect your users from Trojans, viruses, and phishing emails. What should you implement?
- A. Multifactor authentication 
- B. Software firewalls
- C. Anti-malware software
- D. Antivirus software

A. C, Anti-malware software covers a wide array of security thrieats to users, including trojans, viruses and phishing emails.

25. What is a method for stopping tailgating?
- A. User authentication 
- B. Mantraps
- C. Strong passwords 
- D. Change SSIDs

A. B, using mantraps (small rooms that limit access to one or a few individuals) is a great way to stop tailgating.

26. Which command will configure the enable password for a router or switch?
- A. Router(config)#password enable Password20! 
- B. Router(config)#enable Password20!
- C. Router(config)#enable secret Password20! 
- D. Router(config)#secret enable Password20!

A. C. 

27. You need to set the login password for Telnet. Which command will you type first?
```
A. Switch(config)#interface vlan 1 
B. Switch(config)#line console 1 
C. Switch(config)#line aux 1
D. Switch(config)#line vty 0 5
```

A. D. 

28. You have set the enable password using enable password Password20!. However, when you try to get to a privileged exec prompt, the router states that you are using an incorrect password. What is the problem?
- A. You originally entered the wrong password.
- B. The enable secret password is set to something else.
- C. The password Password20! contains a special character. 
- D. The password is too long and has been truncated.

A. B 

29. Which command(s) will set a password and require login for a line?
```
A. Router(config-line)#set password Password20! 
Router(config-line)#request login

B. Router(config-line)#password Password20! 
Router(config-line)#login password

C. Router(config-line)#password Password20! 
Router(config-line)#login

D. Router(config-line)#login password Password20!
```

A. C. 

30. You Telnet to a switch and receive the error Password required, but none set.[Connection to 192.168.1.1 closed by foreign host]. What is the problem?
- A. The enable secret is not set.
- B. The enable password is not set.
- C. The line login password is not set. 
- D. The line is administratively down.

A. C. 

31. What is required before generating the encryption keys for SSH on a router or switch?
- A. Setting the time and date
- B. Setting the hostname and domain name 
- C. Setting the key strength
- D. Setting the key repository

A. B.

32. Which command will enable SSH version 2 for logins?
- A. Router(config)#ip ssh version 2
- B. Router(config-line)#version 2
- C. Router(config-ssh)#version 2
- D. Router(config)#ssh version 2

A. A.

33. Which command will configure the router or switch to allow SSH as a
protocol for management with a fallback of Telnet? 
- A. Switch(config)#login ssh telnet
- B. Switch(config-line)#login ssh telnet
- C. Switch(config-line)#transport ssh telnet 
- D. Switch(config)#transport ssh telnet

A. C.

34. Why should Telnet be replaced with SSH?
- A. Telnet has weak encryption.
- B. SSH allows for file copy.
- C. SSH makes it easier to create ACLs for access. 
- D. SSH is encrypted.

A. D.

35. Which command will create and apply an access list to secure router or switch management?
```
A. Switch(config)#access-list 1 permit host 
Switch(config)#interface vlan 1 
Switch(config-if)#ip access-group 1 in

B. Switch(config)#access-list 1 permit host 
Switch(config)#line vty 0 5 
Switch(config-line)#ip access-group 1 in

C. Switch(config)#access-list 1 permit host 
Switch(config)#line vty 0 5 
Switch(config-line)#ip access-class 1 in

D. Switch(config)#access-list 1 permit host 
Switch(config)#ip access-group 1 in
```

A. C, apply with the [ip access-class 1 in] command which differs from the ip access-group which is used on interfaces

36. You have created the SSH encryption keys, but you cannot enable SSH version 2. What is the problem?
- A. The time and date need to be corrected.
- B. The key strength needs to be 768 bits or higher. 
- C. The DNS server is not configured.
- D. There is no host record for the switch or router.

A. B.

37. Which command will configure a local user for SSH access?
- A. Router(config)#username user1 password Password20!
- B. Router(config)#account user1 Router(config-acct)#password Password20!
- C. Router(config)#user user1 Password20!
- D. Router(config)#user-account user1 password Password20!

A. A.

38. You configured the password for Telnet access, but when you perform a show running-configuration, the password shows in clear text. Which command should be run?
- A. Router(config)#password encryption
- B. Router(config)#service password-encryption 
- C. Router(config)#service encryption
- D. Router(config)#password-encryption service

A. B.

39. Which command will generate the encryption keys for SSH? 
- A. Router(config)#generate crypto key rsa
- B. Router(config)#crypto key generate rsa
- C. Router(config)#crypto generate key rsa
- D. Router#crypto key generate rsa

A. B.

40. Which command will disable auto-disconnect for idle privileged exec
sessions?
- A. Switch(config-line)#exec-timeout 0 0 
- B. Switch(config)#exec-timeout 0
- C. Switch(config-line)#timeout 0 0
- D. Switch(config-line)#no exec-timeout

A. A.

41. B.

42. You want to turn on local authentication so that a user must supply a username and password when managing the switch. You have created the username and password combinations on the switch. Which command will direct SSH and Telnet to use this authentication model?
- A. Switch(config)#new aaa model
- B. Switch(config)#local authentication
- C. Switch(config-line)#local authentication 
- D. Switch(config-line)#login local

A. D. 

43. During a recent external security audit, it was determined that your enable password should be secured with SHA-256 scrypt. Which command will change the password strength on the switches and routers?
- A. Switch(config)#enable secret 9
- B. Switch(config)#service password-encryption scrypt
- C. Switch(config)#enable secret algorithm-type scrypt
- D. Switch(config)#enable algorithm-type scrypt secret Password20!

A. D. 

44. What is the default encryption method for passwords when you configure a line password?
- A. MD5
- B. SHA-128 
- C. SHA-256 
- D. Clear text

A. D. 

45. You need to change the default idle time before disconnection of privileged exec mode for network administrators. Which command
will change it to 30 minutes?
- A. Switch(config)#exec-timeout 30 0
- B. Switch(config-line)#exec-timeout 30 0 
- C. Switch(config-line)#exec-timeout 0 30 
- D. Switch(config-line)#timeout 30 0

A. B.

46. You need to disconnect a network admin from the switch or router. Which command would you use?
- A. Switch(config)#no enable secret 
- B. Switch#no line vty 2
- C. Switch#disconnect line vty 2
- D. Switch#clear line vty 2

A. D, [clear line vty 2] will disconnect a remote admin connected to the switch

47. Which banner can deliver a message only to authenticated users regardless of connection type?
- A. MOTD banner 
- B. Login banner
- C. Exec banner
- D. Incoming banner

A. C, the exec banner will display a message to authenticated users who have successfully logged in.

48. Which technology will give selective access to the network based upon authentication?
- A. 802.1Q 
- B. ACLs 
- C. 802.1X 
- D. Firewall

A. C, 802.1X allows selective access to a network at layer 2. It allows this on the switch because the switch acts as an Authenticator to an AAA server, only allowing access after the user or device has been authenticated.

49. What is the end device that sends credentials for 802.1X called?
- A. Authenticator
- B. Supplicant 
- C. AAA server
- D. RADIUS server

A. B, the end device that sends credentials is called the supplicant. The supplicant is a piece of software in the operating system that supplies the credentials for AAA authentication. 

50. What is the switch called in an 802.1X configuration?
- A. Authenticator 
- B. Supplicant
- C. AAA server
- D. RADIUS server

A. A, the switch is responsible for communicating with the supplicant and sending information to the authentication server. 

51. What protocol does the supplicant communicate to the authenticator for 802.1X?
- A. 802.1X EAP 
- B. UDP
- C. TCP
- D. IP

A. A, the protocol used to communicate between supplicants (OS) and the authenticator (Switch) is 802.1X EAP - Extensible Authentication Protocol. 802.1X EAP is a layer 2 protocol used specifically for authenticating devices to switch ports and wireless. 

52. Which protocol is used by 802.1X for supplicant to authenticator and authenticator to authentication server?
- A. 802.1X authentication headers 
- B. IPsec
- C. EAP
- D. RADIUS

A. C.

53. Which device is the supplicant during the 802.1X authentication process?
- A. The device requesting access
- B. The server that is providing authentication
- C. The device that is controlling access via 802.1X 
- D. The device connecting the layer 3 network

A. A.

54. A smart card is an example of which type of authentication? 
- A. Single-factor authentication
- B. RADIUS authentication
- C. Multifactor authentication
- D. Active Directory authentication

A. C, must have the card and the passphrase that secures the card

55. You believe that a user’s account has been compromised via a password attack. What should have been enforced to prevent this? (Choose the best answer.)
- A. Password complexity 
- B. Password expiration 
- C. Phishing protection 
- D. Time restrictions

A. A. 