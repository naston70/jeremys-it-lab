## Standard ACLs -  Access Control Lists

#### ACLs from a security viewpoint

- ACLs function as a packet filter, instructing the router to permit or discard specific traffic
- ACLs can filter traffic based on source / destination IP addresses, source / destination Layer 4 ports, etc

There must be a requirement -  such as 'Hosts in 192.168.2.0/24 cannot access 10.0.2.0/24 network'
* ACLs are configured globally on the router (global config mode)
* They are an ordered sequence of ACEs (Access Control Entries)

- Configuring an ACL in global config mode will not make the ACL take effect
- The ACL must be applied to an interface
- ACLs are applied either inbound or outbound
- ACLs are made up of one or more ACEs
- When the router checks a packet against the ACL, it processes the ACEs in order from top to bottom
- If the packet matches one of the ACEs in the ACL, the router takes the action and stops processing the ACL. All entries below the matching entry will be ignored
- Maximum if one inbound and one outbound ACL per interface

#### Implicit Deny

What happens if a packet doesn't match any entries in an ACL?
