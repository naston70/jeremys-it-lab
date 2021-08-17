## Network Security Concepts

Exam Topics:
- Define key security concepts 
- Describe Security program elements
- Describe Security password policies

## Security Fundamentals

Cyber criminals now have the expertise and tools to take down critical infrastructure and systems. Specific terminology is used to describe their tools and attacks.

#### Security Terms

Assets must be identified and protected. Vulnerabilities must be addresses before they become threats and are exploited. Mitigation techniques are required before, during and after an attack.

###### Security Terms Table

| Term          | Description                                    |
|---------------|------------------------------------------------|
|               |                                                |
| Assets        | Anything of value, data, resources etc         |
| Vulnerability | A weakness in a system or its design           |
| Threat        | A potential danger to a company's assets       |
| Areas         | Support the same two-level hierarchy           |
| Exploit       | A mechanism that takes advantage of a vuln     |
| Mitigation    | The process of taking countermeasures          |
| Risk          | The likelihood of a threat exploiting the Vuln |

#### Attack Vectors and Data Exfiltration

An attack vector is a path by which a threat actor can gain access to a server, host or network, Attack vectors originate inside or outside a network. For example, threat actors may target a network through the Internet to disrupt Network operations and create a DoS attack.

Internal threats have the potential to cause greater damage than external threats because internal users have direct access to the building and its infrastructure devices. 

Employees may also have knowledge of the corporate network, its resources and its confidential data. Data loss or data exfiltration occurs when data is intentionally or unintentionally lost, stolen or leaked. Network security professionals must protect organizations data. Various data loss prevention controls must be implemented (DLP), combining strategic, operational and tactical measures.

#### Data Loss Vectors

| Vector                  | Description                              |
|-------------------------|------------------------------------------|
|                         |                                          |
| email/social            | Intercepted email / IM messages captured |
| Unencrypted devices     | retrieval of valuable data               |
| Cloud storage           | Weak security settings                   |
| Removable media         | Unauthorized transfer of data            |
| Hard copy               | confidential data should be shredded     |
| Improper access control | weak passwords compromised               |

#### Penetration Testing Tools 

To validate the security of a network and its systems, many network penetration testing tools have been developed. These can also be used by bad actors

| Tool                       | Description                                  |
|----------------------------|----------------------------------------------|
|                            |                                              |
| Password crackers          | tools that repeatedly guess to crack         |
| Wireless hacking tools     | used to intentionally hack into wireless     |
| Network scanning tools     | used to probe network devices for open ports |
| Packet crafting tools      | test firewall robustness with forged packet  |
| Packet sniffers            | used to capture and analyze packets          |
| Rootkit detectors          | directory and file integrity checker         |
| Forensic tools             | used to find traces of evidence on computers |
| Debuggers                  | used to reverse engineer binary files        |
| Hacking OS's               | specially desined OS's preloaded             |
| Encryption tools           | algorithm schemes to encode data             |
| Vulnerability exploitation | to identify vulnerability on remote hosts    |

#### Attack Types

- **Eavesdropping attack:** Threat actor captures and listens to traffic. AKA - sniffing or snooping

- **Data Modification attack:** Capture and altercation of traffic without the knowledge of sender or receiver

- **IP address spoofing:** Construction of an IP packet that appears to originate from a valid address inside the corporation

- **Password based attacks:** A threat actor who discovers a valid use account has the same rights as the real user. A threat actor can use a valid account to obtain lists of other users or network information.

- **Denial of Service:** A DoS prevents normal use of a computer network by flooding a computer or entire network

- **Man in the Middle:** Attackers positioned between source and destination. 

- **Compromised key attack:** If a threat actor obtains a secret key, that key is referred to as a compromised key attack

- ** Sniffer attack:** An application that can read, monitor and capture network data exchanges

#### Types of Malware

*Malware*, short of malicious software, is code or software specifically designed to damage, disrupt, steal or inflict 'bad' or illegitimate action on data, hosts, or networks. Viruses, worms and Trojan horses are examples.

Other types include: Adware; Ransomware; Rootkit (used to gain admin level access) and Spyware

#### Network Attacks 

Network attacks include reconnaissance attacks, access attacks, DoS attacks, social engineering and attacks to exploit the TCP/IP suite.

###### Reconnaissance Attacks 
Information gathering, threat actors use recon attacks to do unauthorized discovery and mapping of systems, service or vulnerabilities. Recon attacks precede access attacks or DoS attacks.

**Techniques:** 
- perform an information query of the target: The threat actor looks for initial information about a target.
- initiate a ping sweep of the network: the information query usually reveals the targets network address. The attacker can then initiate a ping sweep to determine active IP addresses
- initiate a port scan of active IP addresses: a port scan can be used to determine which ports or services are available.
- run vulnerability scanners: query the identified ports to determine the type and version of the application and operating system running on the host
- run exploitation tools: attacker attempts to discover vulnerable services that can be exploited

#### Access Attacks 

The purpose of an access attack is to gain entry to web accounts, confidential databases and other sensitive information. Threat actors use access attacks on network devices and computers to retrieve data, gain access or escalate access privileges to administrator status 

###### Types of Access Attacks 

- password attack: attempted discovery of critical system passwords using various methods. 
- spoofing attack: devices pose as another device by falsifying data. 
- trust exploitation: threat actor uses unauthorized privileges to gain access to a system possibly compromising the target 
- port redirection: threat actor uses a compromised system as a base for attacks against other targets
- man-in-the-middle-attack: read or modify data passing between two parties
- buffer overflow attack: exploit the buffer memory and overwhelms it with unexpected values.

#### Social Engineering Attacks

- Pretexting: an attack in which a threat actor pretends to need personal or financial data to confirm the identity of the target
- Phishing: an attack in which a threat actor sends fraudulent email that is disguises as being from a legitimate, trusted source to trick the recipient into installing malware
- Spear phishing: an attack in which a threat actor creates a targeted phishing attack tailored for a specific individual or organization 
- Spam: Unsolicited email, also known as junk mail, that often contains harmful links, malware or deceptive content
- Something for something: sometimes called quid pro quo, an attack in which a threat actor requests personal information from a party in exchange for something such as a gift
- Baiting: an attack in which a threat actor leaves a malware infected flash drive in public location
- Impersonation: an attack in which threat actors pretend to be someone they are not
- Tailgating: an attack in which a threat actor quickly follows an authorized person into a secure location to gain access to a secure area 
- shoulder surfing: an attack where someone looks over the shoulder of the victim
- dumpster diving: information retrieved from rubbish bins 

#### DoS and DDoS Attacks 

A DoS attack creates some sort of interruption of network services to users, devices or apps. DoS attacks are created in two ways:

* Overwhelming quantity of traffic: an enormous quantity of data at a rate that the network, host or application cannot handle. This causes transmissions and response times to slow down. It can also crash a device or service or
* Maliciously formatted packets: maliciously formatted packets send to a host or app and the receiver is unable to handle it. This causes the receiving device to run very slowly or crash

DoS attacks are relatively simple to conduct, even by unskilled users. A DDoS attack is similar to a DoS attack but originates from multiple, coordinated sources. 

#### IP Attacks 

IP does not validate whether the source IP address contained in a packet actually came from that source. For this reason, threat actors can send packets using a spoofed source IP address. Other fields in the IP header can also be tampered with. Security analysts must understand the different fields in both the IPv4 and IPv6 headers.

###### Types of IP Attacks

- icmp attacks: ICMP echo packets can be used to discover subnets and hosts on a protected network, to generate flood DoS attacks and alter host routing tables
- amplification and reflection attack: prevention of legitimate users from accessing information or services using DoS and DDoS attacks.
- address spoofing attacks: spoofing source IP addresses in an IP packet to perform blind spoofing or non-blind spoofing. In non-blind spoofing, the threat actor can see the traffic that is being sent between the host and target. The threat actor uses non-blind spoofing to inspect the reply packet from the target victim.
- MITM: Threat actors position themselves between a source and destination to transparently monitor, capture and control the communications
- session hijacking: gain access to the physical network and then use an MITM attack to hijack a session

#### Transport Layer Attacks 

Threat actors conduct port scans of target devices to discover which services are avaialble. A thret actor can exploit TCP and UDP in the following ways:

