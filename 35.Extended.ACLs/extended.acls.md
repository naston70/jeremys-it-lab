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


















