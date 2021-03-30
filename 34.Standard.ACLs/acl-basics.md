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

| ID | Action | Source      | Wildcard    |
|----|--------|-------------|-------------|
| 1  | permit | 10.80.1.0   | 0.0.0.255   |
| 2  | deny   | 10.95.1.12  | 0.0.0.0     |
| 3  | permit | 10.95.1.0   | 0.0.0.255   |
| 4  | deny   | 192.168.0.0 | 0.0.255.255 |



