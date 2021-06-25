## Network Access

2.0 Network Access
**✓ 2.1 Configure and verify VLANs (normal range) spanning multiple switches**
    2.1.a Access ports (data and voice) 2.1.b Default VLAN
    2.1.c Connectivity
**✓ 2.2 Configure and verify interswitch connectivity**
    2.2.a Trunk ports
    2.2.b 802.1Q
    2.2.c Native VLAN
**✓ 2.3 Configure and verify Layer 2 discovery protocols (Cisco Discovery Protocol and LLDP)**
**✓ 2.4 Configure and verify (Layer 2/Layer 3) EtherChannel (LACP)**
**✓ 2.5 Describe the need for and basic operations of Rapid PVST+ Spanning Tree Protocol and identify basic operations**
    2.5.a Root port, root bridge (primary/secondary), and other port names
    2.5.b Port states (forwarding/blocking)
    2.5.c PortFast benefits
**✓ 2.6 Compare Cisco Wireless Architectures and AP modes**
**✓ 2.7 Describe physical infrastructure connections of WLAN components (AP, WLC, access/trunk ports, and LAG)**
**✓ 2.8 Describe AP and WLC management access connections (Telnet, SSH, HTTP, HTTPS, console, and TACACS+/RADIUS)**
**✓ 2.9 Configure the components of a wireless LAN access for client connectivity using GUI only such as WLAN creation, security settings, QoS profiles, and advanced WLAN settings**



1. You are trying to reprovision a switch in a different part of your network. However, you still see the old VLANs configured from the old network. How can you rectify the problem?
- A. Upgrade the IOS.
- B. Type erase startup-config, confirm it, and reload. 
- C. Type clear vlan, confirm it, and reload.
- D. Delete the vlan.DAT, confirm it, and reload.

A:- D, The vlan.dat is the database for VLANs configured on a switch either manually or through VTP. It is persistent even if config.text is deleted. You must manually delete the VLAN.dat. Upgrading the IOS will not delete the vlan.dat

2. What is the normal range for VLANs before you must use extended VLAN IDs?
- A. VLAN 1 through 1001 
- B. VLAN 1 through 1002 
- C. VLAN 1 through 1005 
- D. VLAN 2 through 1002

A:- A, the normal usable VLAN range for cisco is 1 through 1001. VLANS 1002 to 1005 are reserved for FDDI and Token Ring and cannot be deleted. The extended VLAN range is 1006 to 4096 used for Ethernet VLANs only.


3. Which is a benefit to converting a network from a flat layer 2 network to a routed layer 3 VLAN-enabled network?
- A. Increased collision domains for increased bandwidth
- B. Reduced complexity of design and operations
- C. Flexibility of user management and design
- D. Decreased number of broadcast domains for increased bandwidth

A:- C, the Flexibility of design for workgroups of clients, servers, services etc and the ongoing management of moving and adding people is a benefit of a routed VLAN-enabled network. Migrating from a flat layer 2 network to a routed layer 3 network will not increase collision domains for increased bandwidth

4.

5. What is the extended VLAN range?
- A. VLAN 1002 to 4096
- B. VLAN 1006 to 4096 
- C. VLAN 1006 to 4094 
- D. VLAN 1006 to 4092

A:- C

6. Which command(s) will delete a VLAN? 
- A. Switch(config)#vlan database
     Switch(config-vlan)#no vlan 9 
- B. Switch(config)#vlan database
     Switch(config-vlan)#delete vlan 9
- C. Switch(config)#no vlan 9
- D. Switch(config)#vlan 9 delete

A:- C.


7. Which is a correct statement about frames and VLANs?
- A. Broadcast frames are sent to ports that are configured in different VLANs.
- B. Unicast frames that are not in the MAC address table are flooded to all ports in all VLANs.
- C. The ports that link switches together must be access links.
- D. Frames with a destination MAC that are not in the MAC address table are flooded to only ports in the respective VLAN.

A:- D.


8. What is the normal range of VLANs that can be modified on a Cisco switch with default configuration?
- A. VLAN 1 to 1002 
- B. VLAN 1 to 1001 
- C. VLAN 2 to 1002 
- D. VLAN 2 to 1001

A:- D, the normal range of VLANs on a default Cisco switch is VLAN 1 to 1001. However VLAN 1 cannot be modified so option D 


9. Static VLANs are being used on a switch’s interface. Which of the following statements is correct?
- A. Nodes use a VLAN policy server.
- B. Nodes are assigned VLANs based on their MAC address.
- C. Nodes are unaware of the VLAN in which they are configured. 
- D. All nodes are in the same VLAN.

A:- C, static VLANs are VLANs that have been manually configured vs. dynamic VLANs that are configured via a VLAN Membership Policy Server (VMPS). A node will not know which VLAN it is assigned to when it is statically set via the command [switchport access vlan 3].
Nodes use a VMPS if the VLAN is dynamically configured. Nodes are not assigned VLANs based on their MAC addresses when they are statically configured. All nodes are not necessarily in the same VLAN when static VLANs are being used.

10. A switch is configured with a single VLAN of 12 for all interfaces. All nodes auto-negotiate at 100 Mb/s full-duplex. What is true if you add an additional VLAN to the switch?
- A. The switch will decrease its bandwidth due to overhead.
- B. The switch will increase its count of collision domains.
- C. The switch will now require a router.
- D. The switch will increase its bandwidth due to broadcast domains.

A:- D, the addition of another VLAN will increase the effective bandwidth by adding additional broadcast domains. 

11. What is a direct benefit of adding VLANs?
- A. An increase of broadcast domains while decreasing collision domains
- B. An increase of broadcast domains while increasing collision domains
- C. A decrease of broadcast domains while decreasing collision domains
- D. A decrease of broadcast domains while increasing collisions domains

A:- When adding VLANs, you immediately increase the number of broadcast domains. At the same time, you increase the collision domains. If a switch had 12 ports and they all negotiated at 100 Mb/s half duplex, when a VLAN is added you will automatically create two collision domains while adding an additional broadcast domain.

12. Which statement describes dynamic VLANs?
- A. The access port is switched into the respective VLAN based upon user credentials.
- B. The access port is switched into the respective VLAN based upon the computer’s IP address.
- C. The access port is switched into the respective VLAN based upon the computer’s MAC address.
- D. The access port is switched into the respective VLAN based upon security ACLs.

A:- C, dynamic vlans are deprecated by may still be seen in operation. 

13. You have changed the name of VLAN 3, and you now want to check your change. Which command will you enter to verify the name change?
- A. Switch#show vlans
- B. Switch#show interface vlan 3 
- C. Switch#show run
- D. Switch#show vlan id 3

A:- D, only [show vlan id 3] will show the friendly name

14. Which of the following is a true statement if you have changed the MTU on a VLAN to support jumbo frames?
- A. If a normal MTU of 1528 is used, the switch will not forward the traffic.
- B. Once jumbo frames are configured, nothing more needs to be done. Clients will auto-detect the new MTU and use jumbo frames.
- C. Changing the MTU is an easy and effective method for raising speed.
- D. For jumbo frames to be effective, all devices on the VLAN, including switches, must support them.

A:- D, when the MTU is changed on the VLAN, it has little consequence to normal MTU communications, it must be supported end to end or it can actually decrease performance

15. Which is a benefit of implementing VLANs with a layer 3 router?
- A. VLANs can span multiple switches.
- B. Implementing routed VLANs will decrease the broadcast domains.
- C. ACLs can be employed to secure VLANs.
- D. All of the above.

A:- C, when layer 3 (routed vlans) is implemented, it allows for a more secure network with the use of ACLs applied to the VLAN interface. A single VLAN spanning multiple switches is a benefit of implementing VLANs and not routed VLANs. When you implement VLANs, the broadcast domains increase.

16. You have created a VLAN for the Research department. Now you need to configure an interface on the switch for the newly created VLAN. Which command will configure the interface for the respective VLAN?

* A. Switch(config-if)#switchport vlan research
* B. Switch(config-if)#switchport access vlan research 
* C. Switch(config-if)#switchport access vlan 9
* D. Switch(config-if)#switchport vlan 9

A:- C.

17. You are installing a VoIP phone on the same interface as an existing computer. Which command will allow the VoIP phone to switch traffic onto its respective VLAN?
* A. Switch(config-if)#switchport voice vlan 4
* B. Switch(config-if)#switchport vlan voice 4
* C. Switch(config-if)#switchport voip vlan 4
* D. Switch(config-if)#switchport access vlan 4 voice

A:- A.

18. Which type of port removes the VLAN ID from the frame before it egresses the interface?
* A. Access port 
* B. Trunk port
* C. Voice port
* D. Native port

A. A:- All VLAN tagging is removed from the frame before it egresses an access port to the end device. Trunk ports carry the VLAN tagging from end-to-end. Voice ports tag packets only when the CoC value is modified from the default. 

19. Which of the following is a true statement about static access ports?
- A. An access port can carry VLANs via tagging.
- B. A client computer can request the VLAN to be placed in.
- C. A client computer cannot see any VLAN tagging information. 
- D. A client computer can see the VLAN tagging information.

A:- D, it is removed before the frame egresses the interface

20. You have been tasked to configure an interface with a VLAN ID of 8 and support a VoIP phone on VLAN 6. Which commands would achieve the goal?
* A. Switch(config-if)#switchport vlan 8 
   - Switch(config-if)#switchport vlan 6 voip

* B. Switch(config-if)#switchport mode access vlan 8 
   - Switch(config-if)#switchport voice vlan 6

* C. Switch(config-if)#switchport access vlan 8 
   - Switch(config-if)#switchport voice vlan 6

* D. Switch(config-if)#switchport access vlan 8 voice 6

A:- C.

21. D

22. When you are protecting an interface with port security, to which mode should you set the switch port?
* A. Access mode 
* B. Dynamic mode 
* C. Trunk mode
* D. Voice mode

A:- A, When configuring port security on an interface, the switch port should have a mode of access configured. This will also protect the switch from transitioning into a trunk if another switch is connected. 


23. Which VLAN is the default VLAN used to configure all switches from the factory?
* A. VLAN 999 
* B. VLAN 1002 
* C. VLAN 1005 
* D. VLAN 1

A:- D.

24. You want to delete VLAN 1 for security reasons. However, the switch will not let you. What is the reason you cannot delete VLAN 1?
* A. The VLAN is still configured on a port.
* B. The VLAN serves as the switch’s main management IP.
* C. The VLAN is protected from deletion.
* D. The VLAN is still configured as a native VLAN on a trunk.

A:- C, VLANs 1 and 1002 - 1005 are protected by the IOS and cannot be deleted.

25. Why is it recommended that you do not use VLAN 1? 
* A. It is not a production VLAN.
* B. It cannot be routed via an SVI.
* C. It cannot participate in VTP transfers.
* D. It shouldn’t be used for security reasons.

A:- D.


26. You attempt to configure a VLAN with a new name. You receive the error Default VLAN 1 may not have its name changed. What is wrong?
* A. The VLAN is used on interfaces currently.
* B. The VLAN is protected from any changes.
* C. The VLAN is being referenced by its name in interface configuration.
* D. You are not in the VLAN database when committing the change.

A:- B.

27. C

28. What is the command to verify a VLAN and the port(s) it is associated with?
* A. Switch#show vlans
* B. Switch#show vlan
* C. Switch#show access vlan 
* D. Switch#show vlan database

A:- B.

29. You are configuring a Catalyst 9200 switch, a VLAN is not configured yet, and you mistakenly configure it on an interface with the command switch access vlan 12. What will happen?
* A. The command will error.
* B. The command will complete and update the VLAN database.
* C. The command will complete, but before forwarding can happen, the VLAN must be manually created.
* D. The command will need to be negated and performed after the VLAN is manually created.

A:- B, When the command is invoked inside of the interface, it will create the VLAN automatically. The command will not error. 

30. You have been asked to segment the network for an R&D workgroup. The requirement is to allow the R&D group access to the existing servers, but no other VLANs should be able to access R&D. How can this be achieved with maximum flexibility?
* A. Create a new VLAN, configure a routed SVI interface, and apply ACLs to the VLAN.
* B. Create a new VLAN, configure a routed SVI interface, and apply extended ACLs to the R&D switch ports.
* C. Create a new VLAN, and install a new R&D server in the new VLAN.
* D. Create a new VLAN, and trunk the existing file server for both the production and R&D networks.

A:- A. Creating the new VLAN will logically segment this work group. Creating a SVI - Switched Virtual Interface, will allow routing on the layer 3 switch. The ACLs should only be applied to VLAN interfaces. 

31. A.

32. You need to verify that an interface is in the proper VLAN. Which command will display the status of the interface, the VLAN configured, and the operational mode?
* A. Switch#show vlan
* B. Switch#show running-config
* C. Switch#show interfaces
* D. Switch#show interfaces switchport

A:- D.

33. You configured VLAN on an interface, but it is not working. After looking at the VLAN database, you find it has been disabled. Which command will enable the VLAN?
* A. Switch#enable vlan 3
* B. Switch(config)#enable vlan 3
* C. Switch#no shutdown vlan 3
* D. Switch(config)#vlan 3
     Switch(config-vlan)#no shutdown

A:- D, The proper way to enable a VLAN to forward traffic is to first enter the VLAN database for ID3 and then issue the [no shutdown] command

34. Which command will show the operational mode of only Fa0/3? 
* A. Switch#show interfaces
* B. Switch#show interfaces switchport
* C. Switch#show interfaces FastEthernet 0/3 switchport
* D. Switch#show interfaces status | i 0/3

A:- C.

35. B 
36. A
37. B

38. A VLAN was created on another non-Cisco switch. You look at the current VLAN database, but the VLAN is not in the VLAN database. What must be done to correct the issue?
* A. Set the correct trunking protocol between the switches. 
* B. Create the VLAN manually.
* C. Configure VTP on both switches.
* D. Assign the VLAN to an interface on the other switch.

A:- B, you must manually configure the VLAN on the cisco switch(s).

39.
A:- B, when a VLAN is created , so is a broadcast domain. The broadcast domain/VLAN requires its own unique IP network addressing and a router to route between networks. 

40. An administrator calls you and states that they believe an interface is down on a router you maintain. Which command will show only the interface, the IP address configured, and the status of the interface?
* A. Router#show ip interface
* B. Router#show interface
* C. Router#show ip interface brief 
* D. Router#show interface brief

A:- C. 

41.

42. You have connected a Dell switch to the Cisco switch you are configuring and you cannot get a trunk between the two. What must be changed?
* A. The Dell switch must be configured to use ISL.
* B. The Cisco switch must be configured to use 802.1Q.
* C. Both switches need to have duplicated VLAN configurations. 
* D. VTP needs to be configured on each of the switches.

A:- B, the Dell cannot support proprietary protocol ISL (inter-switch link), both switches need to have duplicate VLAN configurations, that will not prevent them from creating a trunk between themselves. VTP is also a proprietary Cisco protocol so cannot be configured on the Dell. 

43. You need to view all of the trunks on a switch and verify that they have the proper trunking protocols configured. Which command will display the information?
* A. Switch#show interfaces brief 
* B. Switch#show interfaces trunk 
* C. Switch#show switchport trunk 
* D. Switch#show switchport brief

A:- B, ```show interface trunk``` will display all of the configured trunks on the switch. 

44. What is the default VTP mode all switches are configured as by default?
A. Server
B. Client
C. Transparent 
D. Master

A:- A. 

45. You need to verify the VTP mode on a switch. Which command will display the information?
* A. Switch#show vtp
* B. Switch#show vtp status
* C. Switch#show vtp counters 
* D. Switch#show running-config

A:- B.

46. Which commands would you enter on a new switch joining your existing network to configure VTP?
```
* A. Switch(config)#vtp mode transparent  
     Switch(config)#vtp domain corpname

* B. Switch(config)#vtp mode client 
     Switch(config)#vtp domain corpname

* C. Switch(config)#vtp domain corpname

* D. Switch(config)#vtp client 
     Switch(config)#vtp corpname
```

A:- B.

47. You need to remove VLANs 2 through 4 from the allowed list on a trunk interface. Which command will remove only these VLANs without interruption to the network?
```
* A. Switch(config-if)#switchport trunk remove vlan 2-4
* B. Switch(config-if)#switchport remove vlan 2-4
* C. Switch(config-if)#switchport trunk allowed vlan remove 2-4
* D. Switch(config-if)#switchport trunk allowed remove vlan 2-4
```

A:- C.

48. D

49. You need to add VLAN 4 to the allowed list on a trunk interface. Currently VLANs 5 through 8 are allowed. Which command will add only this VLAN without interruption to the network?
``` 
* A. Switch(config-if)#switchport trunk allowed vlan add 4 
* B. Switch(config-if)#add allowed vlan 4
* C. Switch(config-if)#switchport trunk add vlan 4
* D. Switch(config-if)#switchport trunk allowed add vlan 4
```

A:- A.

50. You try to configure the command switchport mode trunk on an interface. However, you see the error message Command rejected: An interface whose trunk encapsulation is Auto cannot be configured to trunk mode. What command will fix the issue?
```
* A. Switch(config-if)#switchport mode trunk manual
* B. Switch(config-if)#no switchport mode dynamic auto
* C. Switch(config-if)#switchport trunk encapsulation dot1q
* D. Switch(config-if)#no switchport trunk encapsulation auto
```

A:- C. 

51. What is the function of the VTP?
* A. VTP allows for dynamic trunking between links.
* B. VTP allows for propagation of the VLAN database.
* C. VTP detects trunk encapsulation and negotiates trunks. 
* D. VTP allows for propagation of the trunking database.

A:- B.

52. Which VTP mode will not allow the switch to participate in VTP traffic but will forward VTP traffic?
A. Server mode
B. Transparent mode 
C. Proxy mode
D. Client mode

A:- B, a switch in vtp transparent mode will not participate in VTP. However if the VTP mode is v2, the switch will forward and receive VTP advertisements.

53. D.

54. What significance does VTP VLAN pruning provide?
* A. VLAN pruning removes VLANs from the databases of other switches that they are not configured on.
* B. VLAN pruning removes VLAN traffic from other switches that are not configured for the respective VLAN.
* C. VLAN pruning automatically changes the allowed VLANs on all interfaces.
* D. All of the above.

B:- B, VTP pruning removes forwarding traffic for VLANs that are not configured on remote switches. This saves bandwidth on trunks because if the remote switch does not have the VLAN configured on it, the frame destined for the VLAN will not traverse the trunk. 

55. Which command enables VTP pruning?
```
A. Switch(config)#vtp mode pruning
B. Switch(config)#vtp pruning
C. Switch(config)#vtp vlan pruning
D. Switch(config-vlan)#enable pruning
```
A:- B.

56. When enabling VTP pruning, where does it need to be configured?
A. VTP pruning needs to be configured only on the VTP server.
B. VTP pruning needs to be configured only on the VTP client.
C. VTP pruning needs to be configured only on the VTP transparent.
D. VTP pruning needs to be configured on all VTP clients and the server.

A:- A, VTP pruning only needs to be configured on the server. The clients will receive the update and turn on VTP pruning automatically.

57. B. 

58. Which command will turn off Dynamic Trunking Protocol (DTP) on an interface?
```
A. Switch(config-if)#no dtp
B. Switch(config-if)#no switchport dtp enable 
C. Switch(config-if)#switchport dtp disable 
D. Switch(config-if)#switchport nonegotiate
```
A:- D.

59. You are trunking Switch A and Switch B together. On Switch A you have the default of switchport mode dynamic auto. On Switch B, which command will you need to configure to allow trunking?
``` 
A. SwitchB(config-if)#switchport mode trunk
B. SwitchB(config-if)#switchport mode dynamic trunk 
C. SwitchB(config-if)#switchport mode dynamic auto 
D. SwitchB(config-if)#switchport nonegotiate
```

A:- A, Switch B will need to have its interface set to either ```switchport mode trunk ``` or ```switchport mode dynamic desirable``` for SwitchA to turn its interface into a trunk 

60. D.

61. Which protocol is a Cisco proprietary protocol used for trunking switches?
* A. ISL
* B. 802.1Q
* C. VTP
* D. CDP

A:- A,

62. How does IEEE 802.1Q tag frames?
* A. 802.1Q adds a 32-bit header to the frame with the VLAN tagging information.
* B. 802.1Q adds a 32-bit header to the packet with the VLAN tagging information.
* C. 802.1Q inserts a 32-bit field between the source MAC address and the type field.
* D. 802.1Q inserts a 32-bit field between the destination MAC address and the type field.

A:- C, 802.1Q inserts a field containing the 16 bit Tag Protocol ID of 0x8100, a 3-bit COS field a 1-bit drop eligible indicator and the 12-bit VLAN ID, with = 32 bits or 4 bytes. 


63. Which commands will allow a trunk with another switch configured as mode desirable auto?
```
A. SwitchB(config-if)#switchport trunk encapsulation dot1q 
   SwitchB(config-if)#switchport mode trunk

B. SwitchB(config-if)#switchport mode dynamic auto 
   SwitchB(config-if)#switchport mode encapsulation dot1q

C. SwitchB(config-if)#switchport nonegotiate

D. SwitchB(config-if)#switchport encapsulation dot1q
   SwitchB(config-if)#switchport mode trunk
```

A:- A, you must first set the encapsulation to 802.1Q, then you can statically set the mode to trunk. 


64. Which statement is correct about native VLANs?
* A. Any traffic tagged will be placed on the native VLAN.
* B. Any traffic that is not allowed over the trunk will be placed on the native VLAN.
* C. Any traffic not tagged will be placed on the native VLAN.
* D. Any traffic that is tagged with ISL on an 802.1Q trunk will be placed on the native VLAN.

A:- C, native VLANs are only used for traffic that is not tagged, in which untagged frames are placed on a trunk link. A common use for native VLANs is management traffic between switches, before both sides are configured as a trunk. 







