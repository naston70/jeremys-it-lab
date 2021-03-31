## ACL Lab

#### Requirements

* Verify traffic coming from clients network is from expected addressing range, or deny if not
* Ensure devices in DMZ can send responses if interrogated for web (HTTP/S)
* Ensure devices in DMZ can make HTTP/s and DNS requests to external devices
* Allow traffic coming from outside to enter the network only if it is a response for a request originated from the inside
* Allow ICMP replies to come in
* Ensure that external devices can reach only the public webserver 10.0.2.1
* Show the 'hit' count for denied traffic

#### Configuring Access Lists - How to Construct a Policy

(Policy = Access List)

When creating a policy, it is desirable to end with the cleanest possible set of rules. To do this a true understanding of the requirements is needed. It also needs to be evaluated as to where to apply the policies. This can completely change how the policy works, so both the rules and position need to be planned.

The two common places for access lists: **close to the source** and **close to the destination**. These two concepts rely on the fact that traffic must have a source and destination IP address.

#### Close to the Source

If the policy is applied close to the source it is possible to block traffic before it enters the network and wastes bandwidth for no reason. This is a clear benefit but very specific rules need to be created that include destination addresses. Without this, potentially a lot of traffic will be restricted that should be permitted.

Since a **Standard Access List** does not consider the destination address, nor any Layer 4 information, it cannot work with this approach. 

A Standard Access List can only verify if the **Source IP** is in the expected IP range. Applying a policy in this way would require many different routers to have the policy, increasing administrative burden.

#### Close to the Destination

If the policy is applied close to the destination, it is possible to consider only the source address in a standard access list. As the traffic is already at the destination, we know it was for this network as a designation. The destination is implicit, but ports still cannot be verified. This allows a more centralized management system as the lists only need to go in a few points.

However, you can boost the performance of this approach by using an **extended access list.** This provides granular control over traffic and be a centralized management system.

## The Lab

In this lab there are three networks. One is the inside network where clients reside, another is the DMZ of the servers and on the other side is an internet facing network.

#### Creating Access Lists

**The commands:** 

The first requirement is to verify the source for traffic on the inside network. This means that clients should use addresses from the 10.0.1.0/24 range. A Standard ACL can do this. To create an access list, two commands can be used, ```access-list``` or ```ip access-list```. While the result is the same, they differ in operation:
- ```access-list``` expects a number to identify the list and then the rule after. 
- ```ip access-list``` expects the keyword ```standard``` or ```extended,``` to define the ACL type. After the keyword, either an number or a name to identify the access list. From there no rules are expected, after hitting enter the menu will move to the **Named Access List** configuration prompt. 
- number for a standard ACL are 1-99 or extended ACL 100-199


## Access List Configuration

*Verify the traffic coming from the clients network is from the expected addressing range or deny if not*

This rule translates into permitting the ```10.0.1.0/24``` network and deny everything else using the implicit deny.
```
#access-list 1 permit 10.0.1.0 0.0.0.255
```

```
#do show ip access-lists
```

###### The 'From-DMZ' ACL

An extended ACL is required for the more complex list. This will be used to permit or deny traffic coming from the DMZ, summarized below:
* Permit HTTP and HTTPs responses
* Permit HTTP and HTTPs requests
* Permit ICMP replies
* Permit DNS requests
* Permit DNS responses
* Explicitly deny unmatching traffic (to show the hit count of denied traffic)

**Ports and TCP Fine-Tuning:**
Specifying a single port is simple, ```eq``` +  port number.
Usually a range of ports needs to be specified and is helped using the following keywords:
* **eq**, followed by a single port number. The port must be exactly as specified
* **neq**, followed by a single port number. The port must be different from the one specified
* **lt**, (less than), followed by a single port number. The port must be below
* **gt**, (greater than), followed by a single port number. The port must be higher than the one specified 
* **range**, followed by two numbers. The port must be within the inclusive range of ports. 

For TCP extended rules, one may want to check the flags in the TCP connection. To do so, the keyword ```established``` can be added to the end of a rule. The rule will then only match if the TCP ACK flag is set to 1. Meaning it will only match if the traffic is coming as a response. A SYN message wont match. As a result this flag is ideal to allow only responses to traffic to come in.

```
ip access-list extended From-DMZ
  remark Responses to HTTP requests
  permit tcp 10.0.2.0 0.0.0.255 eq www any established
  permit tcp 10.0.2.0 0.0.0.255 eq 433 any established
  remark ICMP and DNS 
  permit icmp 10.0.2.0 0.0.0.255 any echo-reply 
  permit udp 10.0.2.0 0.0.0.255 any eq domain
  permit tcp 10.0.2.0 0.0.0.255 any eq domain
  remark HTTP requests
  permit tcp 10.0.2.0 0.0.0.255 any eq www
  permit tcp 10.0.2.0 0.0.0.255 any eq 443
  permit udp 10.0.2.0 0.0.0.255 eq domain any
  permit tcp 10.0.2.0 0.0.0.255 eq domain any
  deny ip any any
```

 #### 'From-Outside' Policy:

 The last ACL is filtering traffic from the outside. This wants to be restrictive as possible, a Zero-Trust policy. First begin by translating high-level requirements into technical ones.

 * Allow TCP traffic only for existing sessions to come in
 * Allow ICMP replies to come in
 * Allow HTTP and HTTP requests for 10.0.2.11 only to come in
 * Explicitly deny all other traffic

```
ip access-list extended From-Outside
  remark Allow TCP responses
  permit tcp any 10.0.2.0 0.0.0.255 established
  permit tcp any 10.0.1.0 0.0.0.255 established
  remark Allow ICMP Replies
  permit icmp any any echo-reply
  permit tcp any host 10.0.2.11 eq www
  permit tcp any host 10.0.2.11 eq 443
  deny ip any any
```

## Applying Polcies

Access Lists wont do anything until they are applied on the right interface. This needs to be done using the ```ip access-group``` command followed by the ACL number or name. The direction ```in``` or ```out``` also needs to be added. 

- in, means traffic coming into the router
- out, is traffic leaving the router

```
int g0/1.10
  ip access-group 1 in

int g0/1.20
  ip access-group From-DMZ in

int g0/2
  ip access-group From-Outside in
```

#### Troubleshooting Access Lists

Two commands, essentially the same ```show ip access-lists``` or ```show access-lists```.

The output shows the lists of rules.  Similar to show running config but it shows the hit count and with that command it is possible to see how many times an ACL matched

#### Modify a single rule inside an ACL

Deleting and re-creating an entire ACL is simple but can save time to just edit one rule which may not be correct.

First the mode needs to be in the ACL prompt configuration using:
```ip access list [standard|extended][number|name]
```
Find the ID of the rule that needs to be modified and simply add a ```no 50``` for example to delete rule 50 and then put the new rule using usual syntax, ie ```50 permit tcp any any```













