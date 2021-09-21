## Study Mode Exam 2

###### Result: FAIL
###### Score : 676

#### Question Review
1.
The AP-manager interface on a WLC controls all Layer 3 communication between a WLC and a lightweight access point.. A WLC can contain up to four static interfaces: the management interface, the AP-manager interface, the virtual interface and the service port interface. The AP-manager interface contains the IP address that is used as the source IP address by which the lightweight APs communicate with the WLC.

###### EIGRP metric weights?

EIGRP uses the lowest segment bandwidth and the sum of the segment delays in the calculation of metric weights.

###### NBIs = REST & OSGI | SBIs = NETCONF, OpenFlow, OpFlex, OnePK

###### Command Sequence

2 hosts connected to  hub>switch>router
```
# conf t
# int fa0/1
# switchport port-security
# switchport port-security violation protect 
```

After the sequence has been issued, one of the hosts will not be able to access the network and the interface will dynamically learn a MAC address. Port security can limit traffic on a switch port so that only traffic sent from one or more statically configured or dynamically learned source MAC addresses is allowed into a switch port. If port security has not been previously configured for an interface , using the ```switchport port-security``` command will result in port security becoming enabled with the following default settings:
* sticky address disabled
* maximum of one MAC allowed on the port 
* port security aging time is 0
* port security static aging is disabled 
* port security aging type is configured to absolute 

###### How OSPF operates on serial interfaces:

Hello timer is set to 10 seconds and dead timer to 40 seconds. PPP encapsulation uses the ptp network type by default.
On ptp networks there is no election. Multicast updates are sent so manual configuration with the ```neighbor``` command is not needed. To configure an OSPF point-to-point network use ```ip ospf network point-to-point``` command. Enabled by default on HDLC and PPP 

###### Security settings likely to configure using Layer 3 Securitydropdown list box

Most likely to configure 'Web Authentication' or 'Web Passthrough' by using the Layer 3 Security drop-down box on the Layer 3 tab of the WLC GUI. 

###### FlexConnect ACLs

FlexConnect ACLs are supported on the native VLAN. 

###### IP 48.25.24.71/21 what is the last host?

/21 = 255.255.248.0, group size is 8 so subnets begin with:
48.25.0.0
48.25.8.0
48.25.16.0
48.25.24.0
48.25.32.0 
SO the IP is situated between x.x.24.x and x.x.32.x and last usable being 48.25.24.31.254



