## ACL Basics

ACLs are a tool to identify traffic and create custom rules for that traffic. For example, with an ACL it is possible to identify traffic and use it later in another part of the configuration.

#### Understanding Access Lists

In IOS traffic filtering means **stateless firewalling.** Traffic filtering permits or blocks traffic based on a set of statically defined rules. This means you can allow a device to communicate with another and prevent the communication with a third one. This technology relies exclusively on Access Lists...

With traffic filtering, you tell the router to analyze the traffic received (or to be sent) on a specific interface. The router opens every packet and compares it against a set of predefined rules. Based on those rules it decides whether to block or permit.
These rules deciding the action of the router are inside of an Access List. Each rule is just a statement. As a result, traffic filtering is static and stateless by nature, because the router does not create dynamic entries in an Access List.


#### Standard Access Lists

A standard access list is a set of rules which only evaluates the source IP address. Based upon the IP it decides whether the packet should be dropped or forwarded. 

###### The Components

Each rule contains :
```
id_num action source_ip wildcard_mask
```

Explanation of the components of a Standard Access Control List
* **ID:** a number the router uses to evaluate the rules in order. The router adopts a top-down approach so analyzes the rules from first to last until something matches. *The first matching rule is executed*
* **Action:** either a 'permit' to allow traffic or a 'deny' to block traffic
* **Source IP & Wildcard Mask:** combination used to see if the packet matches or not. 

#### Analyzing an Access List

| ID | Action | Source IP   | Wildcard    |
|----|--------|-------------|-------------|
| 1  | permit | 10.80.1.0   | 0.0.0.255   |
| 2  | deny   | 10.95.1.12  | 0.0.0.0     |
| 3  | permit | 10.95.1.0   | 0.0.0.255   |
| 4  | permit | 192.168.0.0 | 0.0.255.255 |
|    | deny   | any         | -           |

The above shows an explicit deny for any IP address at the end of the ACL. 
- First rule permits 10.80.1.0/24 subnet
- Second rule permits host 10.95.1.12
- Third rule denies the subnet 10.95.1.0/24
- Fourth rule permits 192.168.0.0/16
- Last rule will deny everything else with an implicit deny

#### Extended Access Lists

Unlike standard, Extended Access Lists consider the source and destination IP address, **transport protocol** and **Layer 4 ports.**
This allows for more specific rules, matching a specific type of traffic

To match source and destination IP, the Wildcard mask is still used but the number of fields increases.

- **Protocol:** can be either IP (doesn't check the transports ports), ICMP, TCP or UDP
- **Port:** can be either a specific port, a range of ports, a list of ports or 'any port'. The router will check these fields only if the protocol is TCP or UDP. 

#### Applying Access Lists

Access lists are simply sets of rules. If an ACl is created but not applied it wont have any effect. To successfully turn an ACL into a filter it needs to be associated with a router interface. This association is directional. Either incoming or outgoing.
Incoming =  traffic coming into the router
Outgoing is traffic the router has already processed and is ready to leave the router out of that interface. An Access List can be applied in both directions or one for the 'in' and one for the 'out'. 

#### The Return Traffic

As Access Lists are directional and stateless care for the return traffic must be taken. If another device is allowed to send traffic to another, then that device must be able to reply. Both ways need to function.


#### Access Lists Logging

Logging can also be enabled with messages going to syslog. Not possible for the implicit deny so some sort of rule should be applied to achieve the same outcome.











