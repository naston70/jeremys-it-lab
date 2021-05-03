## Security Landscape

#### Terms:
- **Threat:** has potential to cause harm to an IT asset
- **Vulnerability:** a weakness that compromises the security or functionality of a system 
- **Exploit:** uses a weakness to compromise the security of functionality of a system 
- **Risk:** the likelihood of a successful attack
- **Mitigation:** techniques to eliminate or reduce the potential of and seriousness of an attack 

#### Malware

* Viruses: software which inserts itself into other software and can spread from computer to computer.
* Worms: self propagating virus that can replicate itself 
* Trojan Horses: malicious software which looks legitimate to trick humans into triggering it. Often installs back doors 
* Ransomware: Encrypts data with the attackers key and asks the victim to pay a ransom to obtain the key 

#### Hacking Tools

- Many available, pen testers use the same tools, typically run on linux.
- examples:
    * password cracking
    * sniffers
    * ping sweepers
    * port and vulnerability scanners


#### Common Attacks 

Reconnaissance: obtains information about the intended victim
- In a targeted attack the attacker will typically start with completely unobtrusive methods such as whois, phone directories, job listings etc
- Then the attacker will dig deeper with port scanners, vuln scanners etc 

Social Engineering: the use of deception to manipulate individuals into divulging confidential or personal information 
- typically only involves use of a telephone or email
- The attacker will often pretend to be somebody else to trick the victim 

Phishing: a social engineering attack where attackers pretend to be from a reputable company to get personal information. The victim is often directed to enter details into a fake website 

Data Exfiltration: where data leaves an organisation without authorization 
- Can be by a hacker
- Or an internal staff member by accident or maliciously 

DoS: attack which prevent legitimate users from accessing an IT resource
- typically brute force style of attack which floods the target system with more traffic than it can handle 
- DoS attacks from a single source can be easily stopped by blocking that host 

DDoS: attack is from multiple sources
- Attacker builds and controls a botnet
- Built through malware such as worms and trojan horses
- Infected hosts connect out to the attackers command and control server. This circumvents firewalls because the connection is initiated from the inside
- The attacker now has control of the botnet to launch attacks 
- DDos attacks are more difficult to mitigate against because the attack comes from multiple sources which could normally be expected to send legitimate traffic 

Spoofing: where an attacker fakes their identity
* IP address, MAC address and Application spoofing

Reflection and Amplification Attacks: a Dos attack where the attacker spoofs the victims source address
- the attacker sends traffic supposedly from the victim which elicits a response from 'reflectors'
- amplification causes a large amount of response traffic to the victim 

Man in the Middle Attacks: attacker inserts themselves into the communication path between legitimate hosts 
- attacker can then read and optionally modify the data 
- ARP spoofing is a well known man in the middle attack 

Password Attacks: an attacker with connectivity to a login window can attempt to gain access to the system behind it.
- Enumeration techniques attempt to discover usernames 
- Password cracking techniques attempt to learn user passwords
- Methods include:
    - Guessing
    - Brute force
    - Dictionary attacks 

Buffer Overflow Attacks: send malformed and / or too much data to the target system, this can cause a dos or compromise of the target system 

Packet Sniffers: attacker has compromised a target system or insert themselves into the network path, Packet sniffers such as WireShark can be used to read the sent and received packets 
- Any unencrypted sensitive information can be learned by the attacker 
- They can use this to damage the organisation or escalate the attack 

## FIREWALLS - IDS and IPS 

* IDS - Intrusion Detection system
* IPS - Intrusion Prevention system
* IDS and IPS use signatures to inspect packets up to layer 7 of the OSI stack, looking for traffic patterns which match known attacks 
* They can also use anomaly-based inspection to look for unusual behaviour, such as a host sending more traffic than usual 
* They require skilled staff to tune the IPS to their own particular environment and minimize false positives and negatives 

Similar to anti-virus

Differences:
- IDS sits alongside the traffic flow and informs security administrators of any potential concerns
- IPS sits inline with traffic flow and can also block attacks 
- (An IDS many also have the capability to tell a firewall to block attacks)

**IPS vs Firewalls**
* IPS uses signatures to inspect up to layer 7 of the OSI stack looking for patterns which may match known attacks 
* Firewalls block or permit traffic based on rules such as destination IP address and port number 
* organisations always deploy firewalls on the Internet edge. They may also deploy them at suitable security points inside their internal network
* IPS's are an option which may be deployed in conjunction with a firewall 
* The lines have blurred recently between IPS and Firewall functions
* Modern firewalls often also have IPS capability 
* They are also often capable of acting as the endpoint of VPN tunnels
* organisations can deploy an all in in one solution or may split out the functions for better scalability
* Specialised devices may also have more advanced features 
* Another option for scalability and higher throughput is clustered devices 

## Firewalls vs Packet Filters (ACLs)

#### How Stateful Firewalls Work
- Firewalls secure traffic passing through them by either permitting or denying it
- Stateful firewalls maintain a connection table which tracks the two-way 'state' of traffic passing through the firewall 
- Return traffic is permitted by default
- Firewall rules example:
    * Deny all traffic from outside to inside
    * Permit outbound wen traffic from 10.10.10.10/24 

#### Next Generation Firewalls 

* Next Generation Firewalls move beyond port / protocol inspection and blocking to add application - level inspection, intrusion prevention and user based security
* DPI analyzes packets up to Layer 7 of the OSI stack 
* Different permissions can be applied to different users 
* The Cisco ASA with FirePower is a Next Generation Firewall 

#### How Packet Filters Work
* An ACL is a packet filter 
* Packet filters do not maintain a connection table 
* They affect traffic in one direction only and do not track the state of two way connections going through the router
* If there is an ACL applied on the way out only the return traffic will be allowed because all traffic is allowed when an ACL is not applied 
* If you have ACLs applied in both directions, you will need explicit entries to allow both the outbound and the return traffic 

#### The 'Established' Keyword

eg:
```
#access-list 100 permit tcp any eq 80 10.10.10.10 0.0.0.255 established
```

- The **established** keyword in an ACL only checks for the ACK flag in return traffic
- This does not make the router a stateful firewall and it also does not keep a connection table 

#### Internal and External Threats 

* ACL packet filters on routers can add to an overall defence in depth strategy
* Standard practice is to use firewalls on major security boundaries and augment this with internal ACLs
* Purely external threats are primarily covered with a strong firewall and IPS protection on the network perimeter 
* Sensitive hosts should also have firewall and IPS protection from internal hosts 

## Cryptography 

* Cryptography transforms readable messages into an unintelligible form and then later reverse the process
* It can be used to send sensitive data securely over an untrusted network
* It uses authentication and encryption methods 

- Cryptography provides:
    * Authenticity (proof of source)
    * Confidentiality (privacy and secrecy)
    * Integrity (has not changed in transit)
    * Non-repudiation (cannot be denied)

#### Symmetric Encryption 

- With symmetric encryption, the same shared key both encrypts and decrypts the data 
- The shared key is known by both the send and receiver and must be kept secret
- It is Fast 
- Used for large transmissions (eg mail, secure web traffic, IPsec)
- Algorithms include DES, 3DES, AES, SEAL 

#### Asymmetric Encryption

- Asymmetric encryption uses private and public key pairs
- Data encrypted with the public key can only be decrypted with the private key and vice versa
- Data encrypted with the public key cannot be decrypted with the public key
- Only the private key must be kept secret
- The public key can be available in the public domain
- Slow
- Used for small transmissions (symmetric key exchange, digital signatures)
- Algorithms include RSA, ECDSA

* This allows anyone to send data securely to the host with the private key
* It is the only one with the private key so only one who can read the message 
* Other hosts with the public key cannot read the message

#### HMAC - Hash-based Message Authentication Codes 

* HMAC codes provide data integrity 
* The sender creates a hash value from the data to be sent using a symmetric key 
* The hash value is appended to the data 
* The receiver hashes the data with the same shared key 
* If the hash values are the same the data has not been altered in transit 
* Used for large transmissions (email, secure web)
* Algorithms include MD5 SHA

#### Key Distribution 
- Cryptography can be used to send sensitive data securely over an untrusted network
- Symmetric key encryption is used for bulk data transmissions
- Each side needs to know the shared key 
- This leads to a key distribution problem

example:
    * When purchasing online, credit card details need to be encrypted over the Internet 
    * The online store cant send the shared key over the same Internet channel, its not secure 
    * It is not practical to contact the client for every purchase
**Public Key Infrastructure:**
- PKI solves the secure key distribution problem
- It uses a trusted introducer (certificate authority) for the two parties who need secure communication
- Both parties need to trust the certificate authority

## SSL, TLS and HTTPs

* SSL: Secure Sockets Layer (deprecated)
* TLS: Transport Layer Security (successor to SSL)
* Can be used to provide web browsing with HTTPs 
- Uses symmetric cryptography to encrypt transmitted data 
- Symmetric keys are generated uniquely for each connection 
- Authentication is provided by public key cryptography
- Message Authentication Code provides integrity


#### Site-to-Site VPNs 


- A site to site vpn uses symmetric encryption algorithms such as DES, 3DES and AES to send encrypted traffic between locations over an untrusted network such as the internet 
- Traffic inside an office is often unencrypted as it is seen as a trusted network 
- VPN tunnels can however also be deployed internally 
- Cisco Trust SEC is another solution for internal authentication and encryption 
- Site-to-Site VPN tunnels typically terminate on a firewall or router on both sides
- A pre-shared key can be configured on both sides of the tunnel or certificates can be used 
- certificates offer a more scalable solution 

#### IPSEC 

* IPSEC is a framework of open standards that provides secure encrypted communication over an IP network 
* Internet Key Exchange (IKE) handles negotiation of protocols and algorithms, and generates the encryption and authentication keys 
* Internet Security Association and Key Management Protocol (ISAKMP) defines the procedures for authenticating and communicating peer creation and management 

- Authentication Header - AH, provides integrity, authentication and protection from replay attacks 
- Encapsulating Security Payload (ESP) provides Confidentiality, integrity, authentication and protection from replay attacks
- ESP is more commonly used 

#### ESP Tunnel Mode 

* Tunnel mode protects the internal routing information by encrypting the IP header of the original packet. The original packet is encapsulated by another set of IP headers
* It is widely implemented in Site-to-Site VPN scenarios 

#### ESP Transport Mode 
* Transport mode encrypts only the payload and ESP trailer so the IP header of the original packet is not encrypted
* The IPsec Transport mode is implemented for client to site VPN scenarios 


## IPsec VPN Implementation 

* Interesting Traffic: The VPN devices recognise the traffic to protect 
* ISAKMP / IKE phase 1: The VPN devices negotiate an IKE security policy, authenticate each other and establish a secure channel 
* ISAKMP / IKE Phase 2: The VPN devices negotiate an IPsec security policy to protect IPsec data 
* Data Transfer: The VPN devices apply security services to traffic, then transmit the traffic 




