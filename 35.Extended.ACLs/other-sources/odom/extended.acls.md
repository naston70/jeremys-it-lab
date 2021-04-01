## Extended Numbered IP Access Control Lists

Extended IP access lists have many similarities compared to the standard numbered IP ACLs. Just like standard IP ACLs, you can enable extended access lists on interfaces for packets either entering or exiting the interface. IOS searches the list sequentially. Extended ACLs also use first-match logic, because the router stops the search through the list as soon as he first statement is matched, taking the action defined in the first matched statement. All these features are also true of standard numbered access lists and named ACLs. 

Extended ACLs differ from standard ACLs mostly because of the larger variety of packet header fields that can be used to match a packet. One extended ACE (rule) can examine multiple parts of the packet headers, requiring that all the parameters be matched correctly to match that one ACE. That powerful matching logic makes the extended access lists more useful and more complex than standard ACLs

#### Matching the Protocol, Source IP and Destination IP

Like standard numbered IP ACLs, extended numbered IP ACLs also use the access-list global command. The syntax is identical, at least up through the **permit** or **deny** keyword. At that point, the command lists matching parameters, and those differ, of course. In particular, the extended ACL access-list command requires three matching parameters: the IP protocol type, source IP and destination IP

```
access-list 101 permit protocol source_IP dest_IP
```

[numbers 100-199 & 2000 - 2699] [protocol = ip, tcp, udp, icmp, etc]

|access-list statement            | Matches                                   |
|---------------------------------|-------------------------------------------|
|access-list 101 deny tcp any any | any packet that has a tcp header          |
|access-list 101 deny udp any any | any packet that has a udp header          |
|access-list 101 deny icmp any any| any packet that has a icmp header         |
|deny ip host 1.1.1.1 host 2.2.2.2| packets from 1.1 to 2.2 regardless of head|
|deny udp 1.1.1.0 0.0.0.255 any   | packets with UDP header following IP head |

**In an extended ACL access-list command, all the mactch parameters must match the packet for the packet to match the command**

#### Matching TCP and UDP Port Numbers

Extended ACLs can also examine parts of the TCP and UDP headers, particularly the source and destination port number fields. The port numbers identify the application that sends or receives the data.

The most useful ports to check are the well-known ports used by servers. ie web servers use well-known port 80 by default. 

When an extended ACL command includes either the **tcp** or **udp** keyword, that command can optionally reference the source and/or destination port. To make these comparisons, the syntax uses keywords for equal, not equal, less than, greater than and for a range of port numbers. The command can use either the literal decimal port numbers or more convenient keywords for some well-known application ports. 

example: (page 49 vol 2)
```access-list 101 permit tcp 172.16.1.0 0.0.0.255 172.16.3.0 0.0.0.255 eq 21
```

Packets with a tcp header, from the 172.16.1.0/24 subnet, sent to the 172.16.3.0/24 subnet with TCP destination port 21.

Assuming the server uses well-known port 21 (FTP), the packets TCP header has a destination port value of 21. The ACL syntax includes the **eq 21** parameters after the destination IP address. The position after the destination address parameters is important: that position identifies the fact that **eq 21** parameters should be compared to the packets destination port. 


