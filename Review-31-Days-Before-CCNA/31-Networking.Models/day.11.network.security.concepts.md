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

