## QOS

The purpose of QoS is to give certain kinds of network traffic priority over others during congestion

**Classification** organizes network traffic (packets) into traffic classed (categories)

- Classification is a fundamental to QoS. To give priority to certain types of traffic, you have to identify which types of traffic to give priority to 
- There are many methods of classifying traffic:
	* An ACL: Traffic permitted by the ACL will be given certain treatment, other traffic will not.
	* NBAR: performs a DPI, looking beyond layer 3 and 4 up to layer 4
	* In the Layer 2 and Layer 3 headers there are specific fields used for classification:
		- The PCP
		- The DSCP

**PCP**

PCP is also known as CoS (Class of Service). Defined by IEEE 802.1p
3 bits in length = 8 possible values (2 to the power of 3 = 8)

PCP values 0: 'best effort' delivery means there is no guarantee that data is delivered or that it meets any QoS standard. This is regular traffic

PCP values 3 and 5: IP phones **mark** call signalling traffic as PCP3, they **mark** the actual voice traffic as PCP5


PCP/CoS  because PCP is found in the dot1q header, it can only be used over the following connections:
* trunk links
* access links with a voice vlan

**DSCP**

IPP updated to DSCP, new standard markings had to be decided. By having generally agreed upon standard markings for different kinds of traffic, QoS design and implementation is simplified, QoS works better between ISPs and enterprises, among other benefits.

The markings are DF - best effort traffic and EF - low loss/latency/jitter traffic, AF assured forwarding and CS, class selector (IPP backward compatibility)