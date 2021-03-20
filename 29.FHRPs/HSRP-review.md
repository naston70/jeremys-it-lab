## HSRP - Hot Standby Router Protocol

Redundancy is a key factor in networks. As all devices point to a default gateway if that fails they will stop communicating outside. HSRP allows a secondary router to take over the role of the default gateway in case the first fails.

When a device powers on it either has a static IP or queries a DHCP server for a dynamic one. The device will have an IP, subnet and the address of the default gateway. Most devices can only store one IP for a default gateway, as a result if that gateway fails there wont be communication outside of their subnet. The router is a Single Point of Failure. No 










