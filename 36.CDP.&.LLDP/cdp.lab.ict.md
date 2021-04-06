## CDP lab walkthrough

CDP and LLDP are two protocols allowing the discovery of the topology of a network.

Some of this network in the lab is hidden so has to be discovered.
Two parts of the lab are to configure and tune both the CDP and LLDP on the three visible switches. Then, using the protocols and telnet, discover the other devices in the hidden cloud.
Configuration requirements:
* Access switches must have CDP disabled on access ports
* Distribution switch must be running both LLDP and CDP

The discovery process can be written into a table format, including hostname, IP address and device type.

## CDP and LLDP Theory:











