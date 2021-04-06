## CDP lab walkthrough

CDP and LLDP are two protocols allowing the discovery of the topology of a network.

Some of this network in the lab is hidden so has to be discovered.
Two parts of the lab are to configure and tune both the CDP and LLDP on the three visible switches. Then, using the protocols and telnet, discover the other devices in the hidden cloud.
Configuration requirements:
* Access switches must have CDP disabled on access ports
* Distribution switch must be running both LLDP and CDP

The discovery process can be written into a table format, including hostname, IP address and device type.

## CDP and LLDP Theory:

Both are neighbor discovery protocols than can operate in an Ethernet environment. Both protocols do the same thing almost identically, with the major difference being CDP is proprietary. 

Network discovery protocols work with a simple yet powerful concept. A device advertises information about itself and listens for information coming from others. The protocols are completely stateless, hence don't have any session establishment nor retransmission of lost packets. Instead each device sends out the same information over a set time period. 

NDP messages are not forwarded. This means a switch receiving a CDP message wont send it to anybody else, but will keep it for itself. This is due to the purpose of the protocols - finding out what is a directly connected neighbor. Therefore, any neighbor discovered with CDP or LLDP is directly connected to the device. Devices store these messages in their CDP / LLDP table. 

## CDP/LLDP Lab 

First configuration requirement is to disable CP on all access ports, do this using ```no cdp enable``` there are port 0/1 - 24 so apply this command on the range of interfaces - switch is called Access1st

```
Acess1st(config)#interface range fa0/1 - 24
Acess1st(config-if-range)#no cdp enable
Acess1st(config-if-range)#exit
```
 Complete this for the second switch and enable LLDP on the distribution switch using 'lldp run'

 #### CDP in a Known Topology

 To see if CDP messages are still being passed between the switch and distribution switch use the command:
 ```show cdp neighbors
 ```

 This shows a simple output containing device information. 

 Using LLDP it is possible to check for the neighbor not running CDP.
 ```show lldp neighbors
 ```
 The output contains the same device information but also finds a new router out of interface g0/1

 To find further information on the hidden device it is possible to use:
 ```show lldp neighbors details
 ```

Can find the IP using a trick to get the MAC and then look up in the ARP table.

With the correct IP (10.0.1.1) it is possible to telnet into the discovered router and use ```show cdp neighbors``` and ```show cdp neighbors details```

From here, two switches are found and the process is repeated to discover any devices from the discovered device. 









