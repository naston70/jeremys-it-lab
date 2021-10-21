## Security Fundamentals

CIA Triad form the foundation of security:

* Confidentiality
	- only auth users should be able to access data 
* Integrity
	- data should not be tampered with
	- data should be correct and authentic
* Availability
	- the network/systems should be operational and accessible to authorized users
	
* A mitigation technique is something that can protect against threats

#### Common Attacks

DoS, Spoofing, Reflection, MITM, Recon, Malware, Social engineering, Password


##### DoS

Threaten the availability of a system
- common DoS is a TCP SYN flood
- ddos, attacker infects or uses many computers with malware and uses them to initiate a ddos

##### Spoofing
- To spoof a fake source address, IP or MAC
- Numerous attacks

##### Reflection
- in a reflection attack the attacker sends traffic to a reflector, and spoofs the source address of its packets using the targets IP
- the reflector (ie a DNS server) sends the reply to the targets IP address
- if the amount of traffic sent to the target is large enough in can result in a dos 

- a reflection attack becomes an amplification attack when the amount of traffic sent by the attacker is small but it triggers a large amount of traffic to be sent from the reflector to the target 

##### Recon attacks

- Used to gather more information rather than attack
- often public info

##### Malware

- Malware refers to a variety of harmful programs that can infect a computer 
- **Viruses** infect other software and spreads as software is shared by users.
- **Worms** do not require a host program. They are standalone malware and spread on their own without user interaction. 
- **Trojan Horses** email, downloads

##### Social Engineering Attacks

- target the most vulnerable part of the system - people 
- they involve psychological manipulation
- Phishing, spear phishing, whaling
- Vishing, voice phishing
- Smishing, sms 

- Watering hole 
- Tailgating, a physical breach

#####