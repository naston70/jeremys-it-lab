## Extended ACLs

Can do more specific matches than a standard ACL

Numbered ACLs are configured in global config mode, named ACLs are configured with subcommands in a seperate config mode.

When configuring/editing numbered ACLs from global config mode, you can't delete individual entries, you can only delete the entire ACL. 

If it is likely to need to edit an ACL, it is better to use the named ACL configuration method

###### Advantages of named ACL config mode

- You can easily delete entries in the ACL with ```no``` *sequence-number*
- You can insert new entries in between other entries by specifying the sequence number 

There is a resequencing function that helps edit ACLs
```ip access-list resequence acl-id starting-seq-num increment
```

## Extended ACL notes

- Extended ACLs function mostly the same as standard ACLs
- They can be numbered or named, just like standard ACLs
    * Numbered ACLs use the following ranges: 100 - 199 & 2000 - 2699

- They are processed from top to bottom, as standard ACLs
- However, the can match based on more parameters, so they are more precise than standard ACLs
- CCNA - matches Layer 4 protocol/port, source address and destination address
**extended number**
```
#access-list number [permit | deny] protocol src-ip dest-ip
```
**extended named**
```
#ip access-list extended {name|number}
```

Important protocol numbers:
1 - ICMP, 6 - TCP, 17 - UDP, 88 - EIGRP, 89 - OSPF

Practice 1:

1. Allow all traffic:
```#permit ip any any
```
2. Prevent 10.0.0.0/16 from sending UDP traffic to 192.168.1.1/32
```#deny udp 10.0.0.0 0.0.0.255 host 192.168.1.1
```
3. Prevent 172.16.1.1/32 from pinging host in 192.168.0.0/24
```#deny icmp host 172.16.1.1 192.168.0.0 0.0.0.255
```

#### Matching the TCP/UDP Port Numbers

When matching TCP/UDP, you can optionally specify the source and/or destination port numbers to match.

If you do specify the protocol, source IP, source port, destination IP, destination port, etc a packet must match ALL those values to match the ACL entry. Even if it matches all except one of the params, the packet wont match that entry

Practice 2

1. Allow traffic from 10.0.0.0/16 to access 2.2.2.2/32 using HTTPS
```#permit tcp 10.0.0.0 0.0.255.255 host 2.2.2.2 eq 443 
```
2. Prevent all hosts using source UDP port numbers from 20000-30000 from accessing server 3.3.3.3/32
```#deny udp any range 20000 30000 host 3.3.3.3
```
3. Allow hosts in 172.16.1.0/24 using a TCP port greater than 9999 to access all TCP ports on server 4.4.4.4/32 except port 32
```permit tcp 172.16.1.0 0.0.0.244 gt 9999 host 4.4.4.4 neq 23
```

**Extended ACLs should be added as close to the source as possible, to limit how far the packets travel in the network before being denied**












