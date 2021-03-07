# VLANs Part 2

### Trunk Ports

In small networks it is possible to use a seperate interface for each VLAN, however when the number of VLANs increases, this is not viable - wasted interfaces and often not enough.

Trunk ports can be used to carry traffic from multiple VLANs over a single interface.

Switches know which VLANs traffic belongs to as switches 'tag' all frames they send over a trunk link. This allows the receiving switch to know which VLAN the frame belongs to.