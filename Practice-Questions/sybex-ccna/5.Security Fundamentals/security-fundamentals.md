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