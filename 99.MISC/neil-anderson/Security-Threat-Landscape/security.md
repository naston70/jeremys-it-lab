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


