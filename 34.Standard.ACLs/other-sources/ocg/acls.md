## IPv4 Access Control Basics

IP ACLs give engineers a way to identify different types of packets. To do so the ACL configuration lists values that the router can see in the IP, TCP, UDP and other headers. ie an ACL can match packets with source 1.1.1.1 or packets whose destination IP address is some address in a subnet or packets with a destination port of 23 (telnet)

Engineers can enable ACLs on a router so that the ACL sits in the forwarding path of packets as they pass through the router. Once enabled the router considers whether to forward or drop the packet depending on the rules in the ACL.

ACLs can also be used for many other features such as QoS. 

#### ACL Location and Direction
Cisco routers can apply ACL logic at the point in which in enters the router or the point in which it leaves - ACLs become associated with an interface and for a direction of packet flow (in or out)

To filter a packet you must enable an ACL on an interface that processes the packet, in the same direction the packet flows through the interface. 

When enabled, the router then processes every inbound or outbound IP packet using that ACL.

#### Matching Packets

When thinking about the location and direction for an ACL,  what packets are to be filtered and which ones to allow through must be known.
To tell a router those same ideas, the router must be configured with an IP ACL that matches packets. *Matching packets* refers to how to configure the ACL commands to look at each packet, listing how to identify which packets should either be dropped or allowed through.

Each IP ACL consists of one or more configuration commands, with each command listing details about values to look for inside a packets headers. 

###### Taking Action When a Match Occurs
When using IP ACLs to filter packets, only one of two actions can be chosen. 
 - ```permit``` and ```deny.```

###### Types of IP ACLs

Features Cisco has added to their ACL features

- **Standard Numbered** ACLs 1 - 99
- **Extended Numbered** ACLs 100 - 199
- **Additional ACL** numbers 1300 - 1999, 2000 - 2699 extended
- **Named** ACLs
- Improved editing with sequence numbers

IP ACLs will either be numbered or named in that they are identified by either a number or a name. ACLs will also be either standard or extended, with extended ACLs having many more abilities in matching packets.

Standard Numbered | Standard Named = Standard: Matching Source IP

Extended Numbered | Extended Named = Extended:
* Source & Dest IP
* Source & Dest Port
* Others

Numbered = ID with number & Global commands

Named = ID with name & subcommands
                        
## Standard Numbered IPv4 ACLs

Standard numbered ACL: An ACL that matches only the source IO address of the packet (standard) and is configured to identify the ACL using numbers rather than name (numbered).

#### List Logic with IP ACLs

When doing ACL processing, the router processes the packet, compared to the ACL, as follows:
- **ACLs use first-match logic. Once a packet matches one line in the ACL, the router takes the action listed in that line of the ACL and stops looking further in the ACL**

#### Matching Logic and Command Syntax

```access-list { 1 - 99 | 1300 - 1999 } { permit | deny } matching-params
```

Each *standard numbered* ACL has one or more access-list commands with the same number, any number from the ranges above, 1-99, 1300-1999. IOS refers to each line in an ACL as an **Access Control Entity (ACE)**

###### Matching the Exact IP Address

To match a specific IP, simply type the full IP in the command
```access-list 1 permit 10.10.10.1
```

###### Matching a Subset of the Addresses with Wildcards

Often, an ACL is needed to match more than a single IP, usually a range or a subnet is needed to be matched

IOS allows standard ACLs to match a range of addresses using the wildcard mask. 

WC masks can be thought about in decimal and binary, both have uses. Use these rules for decimal:

* Decimal 0: The router must compare this octet as normal
* Decimal 255: The router ignores this octet, considering it already a match

###### Binary Wildcard Masks

Wildcard masks, as DDN values, actually represent a 32-bit binary number. As a 32-bit number, the WC mask actually directs the routers logic, bit by bit.
In short, a WC mask bit of 0 means the comparison should be done as usual but a 1 means the bit is a wildcard and can be ignored.
Usually binary wc masks aren't used as the intent is to match a range of addresses and identify by subnet number and mask.

###### Finding the Right Wildcard Mask to Match a Subnet

In many cases an ACL needs to match all hosts in a particular subnet. To match a subnet with an ACL, there are the following shortcuts:
* **use the subnet number as the source value in the access-list**
* **use a wc mask found by subtracting the subnet mask from 255.255.255.255**
* example: subnet 172.16.8.0/22, use the subnet number as the address parameter, and then do [255.255.255.255 - 255.255.252.0] to find the wc mask = 0.0.3.255
* ```access-list 1 permit 17.16.8.0 0.0.3.255``

###### Matching Any/All Addresses

In some cases it will desirable for one ACL command to match any and all packets that reach that point in the ACL. First the simple way to match all packets is the ```any```keyword but more importantly is the 'when' to match any and all packets

To match all packets: ```access-list 1 permit any```

When to use this command? - ACLs end with an implicit **deny any** concept at the end of each ACL. To override that default behavior, configure a **permit any** at the end of an ACL.
It is also useful to override this default **deny** behavior so that the ACL show commands list counters for the number of packets matched by each command in the ACL  









