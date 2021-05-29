## Access Lists (Source: David Bombal)

- Used for creating a standard or extended list to filter packets based on defined rules for source and destination host IP addresses
- These are bound to interfaces facing in or out
- ACL's help router to discard traffic before it is sent all over the network being processed by multiple devices
- ACLs are primarily configured on firewalls but can be configured on routers as well 
- The process of checking an ACL is it checks the first rules for matching statements either permit or deny 
- Once a match is found it will either forward or discard the traffic implicitly. ACLs have deny all traffic at the end 

#### Standard ACL
* Standard Access Lists 0 - 99 are configured far away from the source to prevent traffic being accidentally discarded
* Prioritize traffic by the source IP address 
* This is the command syntax format of a standard ACL:
**access-list access-list-number {permit|deny} {host|source-wildcard|any}**
* An ACL must also be assigned under an interface directionally going out or coming in 

#### Extended ACL
- Extended Access Lists 100 - 199 are configured close to the source because they are more specific and check a range of rules before discarding 
- Filter based on Source / Destination IP address 
- Filter based on TCP / UDP source + destination ports 

#### Comparing Standard vs Extended ACL's 

###### Standard ACL:
- Filters on source address only 
- Permit or deny all IP/TCP 
- Ranges 1-99, 1300-199

###### Extended ACL:
* Filters on source and destination
* Specify IP, protocol and port number 
* Range 100-199, 2000-2699

###### Well known ports:
* 20: FTP data 
* 21: FTP
* 22: SSH 
* 23: Telnet 
* 25: SMTP
* 49: Tacacs
* 69: TFTP 
* 80: HTTP
* 88: Kerberos 
* 161: SNMP
* 162: SNMP trap
* 179: BGP
* 443: HTTPS
* 4224 TCP: CDP 

