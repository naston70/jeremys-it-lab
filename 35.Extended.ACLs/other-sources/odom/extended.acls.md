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

When examining ACLs that match port numbers, first consider the location and direction in which the ACL will be applied. That direction determines whether the packet is being sent to the server or from the server. At that point, you can decide whether you need to check the source or destination port in the packet. 

#### Extended IP ACL Configuration

As extended ACLs can match so many different fields in the various headers in an IP packet, the command syntax cannot be easily summarized to a single command.

The configuration process for extended ACLs mostly matches the same process used for standard ACLs. The location and direction in which to enable the ACL must be chosen. In particular the direction so that you can characterize whether certain addresses and ports will be either the source or destination. Configure the ACL using the same **ip access-group** command used with standard ACLs. All these steps mirror what is done with standard ACLs; however the following differences need to be kept in mind:

* Place extended ACLs as close as possible to the source of the packets that will be filtered. Filtering close to the source of the packets saves some bandwidth
* Remember that all fields in once access-list command must match a packet for the packet to be considered to match that access-list statement
* Use numbers 100-199 and 2000-2699 on access-list commands

#### Extended IP Access List Examples:

Practice building One-line Extended ACLs

1. ```#access-list 101 permit tcp host 10.1.1.1 10.1.2.0 0.0.0.255 eq web```

2. ```#access-list 102 permit tcp 172.16.4.0 0.0.0.127 172.16.3.0 0.0.0.127 eq telnet```
3. ```#access-list 103 permit icmp 192.168.7.```



## Named ACLs and ACL editing

Named IP ACLs have many similarities with numbered ACLs, Standard numbered ACLs match the same fields as standard named. Extended numbered match the same as Extended numbered. 

There are three big differences between using named and numbered ACLs:

* Using names instead of numbers to identify the ACL, making it easier to remember the ACL purpose

