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

65. (Vlans showing in running-config)
A:- The switch is set up with a VTP mode of transparent. When a switch is set up with a mode of transparent, the VLAN information is stored in the running-config in lieu of the vlan.dat file.

66. You have configured switchport nonegotiate on an interface with a default configuration. What effect will it have on the neighboring interface when the other switch is plugged in with its interface in default configuration?
* A. The switch port will transition to a trunk port. 
* B. The switch port will remain an access port. 
* C. The interface will remain shut down.
* D. The interface will enter an err-disable state.

A:- B, the switch will not send DTP - Dynamic Trunking Protocol frames for trunk negotiation. The default mode for a port is the mode of access, so the port will remain in access mode.

67. Switch A has default configuration on its interface. You need to configure Switch A for VLAN 5. Which command will configure the interface to become a member of VLAN 5?
```
A. SwitchA(config-if)#switchport mode access 
   SwitchA(config-if)#switchport access vlan 5
B. SwitchA(config-if)#switchport trunk 
   SwitchA(config-if)#switchport native vlan 5
C. SwitchA(config-if)#switchport access 
   SwitchA(config-if)#switchport access vlan 5
D. SwitchA(config-if)#switchport mode trunk 
   SwitchA(config-if)#switchport native vlan 5
```

A:- A.

68. Switch A is configured with the command of switchport mode dynamic desirable on its interface. Which command would you need to configure on Switch B to create a trunk between them?
```
A. SwitchB(config-if)#switchport mode dynamic auto
B. SwitchB(config-if)#switchport mode dynamic desirable 
C. SwitchB(config-if)#switchport mode trunk
```
D. All of the above

A:- D.

69. Which statement is correct about the command switchport mode dynamic auto?
A. The interface will become a trunk if requested on the neighboring port.
B. The interface will become a trunk if the neighboring port is configured the same.
C. The interface will remain an access link if the neighboring port is configured as a trunk.
D. The interface will remain an access link if the native VLAN is changed.

A:- A.

70. Which command is similar to show interfaces trunk but will show greater detail?
```
A. Switch#show interfaces trunk detail 
B. Switch#show switchport
C. Switch#show interfaces switchport 
D. Switch#show running-config
```

A:- C. 

71. On a switch you enter the commands switchport mode access and switchport nonegotiate. Which statement is true about the interface you’ve configured?

* A. The interface will become a trunk switch port if a switch is plugged in and DTP is turned on for the other switch.
* B. The interface will always remain an access switch port, regardless of whether another switch is plugged in.
* C. The interface will become a trunk switch port if a switch is plugged in and the other switch is set statically to a trunk switch port.
* D. The interface will become a trunk switch port if a non-Cisco switch is plugged in and statically configured as a trunk switch port.

A:- B.

72. You need to configure a trunk interface to support the protocol of 802.1Q. Which command will achieve this?
``` 
A. Switch(config-if)#switchport mode trunk 802.1q
B. Switch(config-if)#switchport trunk encapsulation 802.1q 
C. Switch(config-if)#switchport 802.1q
D. Switch(config-if)#switchport encapsulation trunk 802.1q
```

A:- B.

73. You are trying to configure a trunk port on an interface for 802.1Q encapsulation. However, after entering the proper command, you receive the error % Invalid input detected at '^' marker. What is wrong?
* A. 802.1Q is not supported on the switch you are configuring this on. 
* B. The interface will not allow configuration of 802.1Q.
* C. The switch only supports the ISL trunking protocol.
* D. The switch only supports the 802.1Q trunking protocol.

A:- D, This error is very common when configuring Cisco switches since many switches only support 802.1q and configuration is not necessary

74. When a frame is not tagged with 802.1Q VLAN identifying information, what happens when it traverses a trunk port?
A. The frame is dropped to the bit bucket.
B. The frame is forwarded to the default VLAN.
C. The frame is forwarded to the native VLAN.
D. The frame is sent to the first VLAN ID configured on the trunk.

A:- C, when a frame traverses a trunk and does not have VLAN tagging information in the 802.1q encapsulation format (untagged), it is sent to the native VLAN configured on the trunk. This is to prevent the untagged frame from being dropped. 

75. Which protocol is an open standard trunking protocol?
* A. ISL
* B. VTP 
* C. 802.1Q 
* D. 802.1X

C:- C, The 802.1q protocol is supported on all switches vendors for trunking. It is an open standard that was developed by the IEEE.

76. You have several VLANs and need to route between them. You configure a trunk between your router and switch. What will you need to configure on the router to support each VLAN for routing?
* A. Virtual interface
* B. Switched virtual interface 
* C. Subinterface
* D. VLAN database

A:- C, when implementing ROAS, you must first create a trunk to the router. Once the trunk is created, you mist create subinterfaces for each VLAN to be routed and specify the IP address and 802.1q encapsulation.

77. How many bytes are used in an 802.1Q frame for tagging of VLANs? 
* A. 2 bytes
* B. 4 bytes 
* C. 8 bytes 
* D. 16 bytes

A:- B. 

78. What is the difference between a default VLAN and a native VLAN?
A. A default VLAN is configured on all access ports of the switch from the factory.
B. A native VLAN is configured on all access ports of the switch from the factory.
C. A default VLAN is configured on all trunks for tagged frames.
D. A native VLAN is configured on all trunks for tagged frames.

A:- A.

79. Which command will show you the native VLAN for only Fa0/15?
```
A. Switch#show running-config
B. Switch#show interface fastethernet 0/15
C. Switch#show interface fastethernet 0/15 switchport 
D. Switch#show switchport fastethernet 0/15
```

A:- C.

80. You need to change the native VLAN for interface Fa0/23 from VLAN 1 to VLAN 999. Which command would you use?
```
A. Switch(config-if)#switchport trunk native vlan 999
B. Switch(config-if)#native vlan 999
C. Switch(config-if)#switchport native vlan 999
D. Switch(config-if)#no switchport native vlan 1
   Switch(config-if)#switchport native vlan 999
```

A:- A.

81. When you change the native VLAN of a trunk from VLAN 1 to VLAN 999 and you receive the error %CDP-4-NATIVE_VLAN_MISMATCH: Native VLAN mismatch -discovered.... What is the possible problem?
A. CDP is not running on the other interface, causing a mismatch. 
B. The interface is the first to be changed.
C. The interface is running ISL.
D. The version of CDP is wrong on the other switch.

A:- B, The error is normal if it is the first interface to be changed over to the new native VLAN since the other interface has not been changed yet. However, if the other interface was changed already and you received this error, then CDP is letting you know the other side is mismatched. CDP must be running on both sides of the trunk; therefore you would not see this error if it was disabled on either side. If the interfaces were running mismatched trunking protocols, a different error would be seen. 


82. Switch A and Switch B have a trunk. On Switch A, the native VLAN is set to VLAN 10 on Switch B and the native VLAN is defaulted. What problems will occur?
A. CDP will not function.
B. VTP will not function.
C. All broadcasts will be forwarded to Switch B.
D. Any traffic not tagged on Switch B when traversing the trunk will be switched onto VLAN 10.

A.- D, the problems will not be apparent since the trunk will still function for tagged traffic. However any traffic that is not tagged will be directed to the opposite sides native VLAN. 

83. When you have a native VLAN mismatch on a configured trunk, which protocol will alert you to the issue?
A. VTP 
B. CDP 
C. 802.1Q 
D. ISL

A:- B, CDP - Cisco Discovery Protocol will alert for a native VLAN mismatch. When a trunk is configured the native VLAN is always used for CDP exchanges. 
VTP helps reduce configuration and maintenance of VLANs.
ISL is a proprietary protocol for trunking. 
802.1q is a trunking protocol 

84. You are trying to change the native VLAN from VLAN 1 to VLAN 1002. You have configured both sides with switchport native vlan 1002. However, the native VLAN traffic keeps failing. What is wrong?
A. The native VLAN must be VLAN 1.
B. The native VLAN cannot be an extended VLAN.
C. VLAN 1002 is not allowed for Ethernet traffic.
D. The problem is not the native VLAN; everything is configured properly.

A:- C.

85. Which protocol is an IEEE standard that collects information from neighboring devices on their identity and capabilities?
A. CDP B. LLDP C. 802.1b D. 802.1a

A:- B.


86. You want to turn off CDP on a switch. Which command would you enter?
```
A. Switch(config)#cdp disable
B. Switch(config-if)#no cdp enable 
C. Switch(config)#no cdp
D. Switch(config-if)#no cdp run
```

A:- D.

87. How often are CDP frames sent out of the device by default? 
* A. Every 30 seconds
* B. Every 60 seconds 
* C. Every 90 seconds
* D. Every 180 seconds

A:- B, CDP frames are sent out all active interfaces every 60 seconds

88. Which Cisco proprietary protocol collects information from neighboring devices about their identity and capabilities?
A. 802.1ab 
B. LLDP 
C. CDP
D. 802.1a

A:- C.

89. What is the default value of the CDP hold down timer for CDP entries? 
* A. 30 seconds
* B. 60 seconds 
* C. 90 seconds 
* D. 180 seconds

A:- D, the default holddown timer for CDP entries is three times the advertisement timer of 60 seconds. So entries have a holddown timer value of 180 seconds.

90. You want to turn off CDP on a single interface. Which command would you enter?
A. Switch(config)#cdp disable
B. Switch(config-if)#no cdp enable 
C. Switch(config)#no cdp
D. Switch(config-if)#no cdp run

A:- B. To turn off or suppress CDP advertisements on a single interface, you would enter the interface and use [no cdp enable]

91. Which command gives information that’s identical to the output of the show cdp neighbors detail command?
``` 
* A. Switch#sh cdp neighbors all 
* B. Switch#sh cdp neighbors * 
* C. Switch#sh cdp entries all 
* D. Switch#sh cdp entry *
```

A:- D.

92. You have several non-Cisco IP phones and you want to allow automatic power adjustments on the Cisco Power over an Ethernet (PoE) switch. Which command will allow you to achieve this?
```
A. Switch#lldp run
B. Switch(config)#lldp run
C. Switch(config)#lldp enable 
D. Switch#lldp enable
```

A:- B.


93. Which command will allow you to see LLDP devices connected to a switch?
``` 
A. Switch#show lldp
B. Switch#show lldp devices
C. Switch#show lldp neighbor detail 
D. Switch#show cdp neighbor detail
```

A:- C.

94. What is the default LLDP advertisement interval? 
A. 30 seconds
B. 60 seconds 
C. 90 seconds 
D. 120 seconds

A:- A, default LLDP advertisement is 30 seconds 

95. You want to disable LLDP from sending advertisements on a single interface. Which command will you use?
```
A. Switch(config-if)#no lldp
B. Switch(config-if)#no lldp transmit 
C. Switch(config-if)#no lldp receive 
D. Switch(config-if)#no lldp enable
```

A:- B. 

96. What is the default value of the LLDP holddown timer for entries? 
- A. 30 seconds
- B. 60 seconds 
- C. 90 seconds 
- D. 120 seconds

A:- D, the default value of the LLDP holddown timer for entries is 120 seconds. This holddown timer is set every time the switch hears an advertisement for a device. The holddown timer is 4 times the advertisement interval

97. A 

98. You have a layer 2 connection to your ISP. You want to make sure that you do not send information on the capabilities of your switch, but you don’t want to affect the use of CDP. Which command will you configure?
```
A. Switch(config)#cdp disable
B. Switch(config-if)#no cdp
C. Switch(config-if)#no cdp disable 
D. Switch(config-if)#no cdp enable
```

A:- D, [no cdp enable] will turn off CDP advertisements on the interface that you configure it on.

99. Which command will show the interfaces that CDP is advertising on? 
```  
A. Switch#show cdp
B. Switch#show cdp interface 
C. Switch#show interface
D. Switch#show interface cdp
```

A:- B. 

100. What is the maximum number of interfaces that can be aggregated with EtherChannel and PAgP?
A. 2 interfaces B. 8 interfaces C. 16 interfaces D. 4 interfaces

A:- B. EtherChannel can aggregate 2 - 8 interfaces together on a single switch when using PAgP

101. Which is a true statement about EtherChannel?
- A. EtherChannel works with 802.1Q to block the redundant links.
- B. EtherChannel can aggregate multiple links with varying speed.
- C. EtherChannel can aggregate interfaces across multiple stand- alone switches.
- D. When configured, EtherChannel acts as a single layer 2 connection.

A:- D.

102. You have a switch with 2 gigabit interface ports and 48 FastEthernet ports and are using PAgP. What is the highest bandwidth you can achieve?
- A. 2 Gb/s 
- B. 2.2 Gb/s 
- C. 400 Mb/s 
- D. 2.6 Gb/s

A:- A, the highest configurable bandwidth is going to be 2 Gb/s. This is because you cannot mix speeds and duplex settings. 

103. Which aggregation protocol is an IEEE standard? 
- A. LACP
- B. 802.1Q 
- C. PAgP 
- D. 802.1X

A:- A, the LACP is the IEEEE standard 802.ad 

104. You need to form an EtherChannel between a VMware ESXi host and the switch. Which negotiation protocol will you choose?
- A. EtherChannel 
- B. LACP
- C. Channel Group
- D. PAgP

A:- B, LACP is an IEEE standard supported by non cisco devices to create aggregation links and negotiate the configuration.

105. What is the maximum number of interfaces that can be aggregated with EtherChannel and LACP?
- A. 2 interfaces 
- B. 8 interfaces 
- C. 16 interfaces 
- D. 4 interfaces

A:- C, EtherChannel can aggregate 2 - 16 interfaces together when using LACP

2-8 interfaces with PAgP
2-16 interfaces with LACP

106. Which mode forces the aggregation of links without the use of a control protocol?
* A. LACP off mode 
* B. PAgP off mode 
* C. On mode
* D. 802.3ad mode

A:- C, if you can configure the EtherChannel to on mode, it forces the aggregation of links without the use of a control protocol.

107. Which is a correct statement about aggregating ports together?
- A. The term EtherChannel is a Cisco proprietary term for port channeling.
- B. PAgP can be used with non-Cisco products.
- C. LACP can only be used with other Cisco switches.
- D. PAgP can bundle several different links with varying speeds and duplexes together.

A:- A, it is a Cisco centric term, PAgP is cisco proprietary, LACP is an open standard for port aggregation and neither can bundle links with varying speeds and duplexes.

108. Which negotiation protocol is a Cisco proprietary standard? 
- A. LACP
- B. 802.1Q 
- C. PAgP 
- D. 802.1ab

A:- C, PAgP is Cisco proprietary


109. How often does PAgP send messages to control the status of the links in the bundle?
- A. Every 30 seconds
- B. Every 60 seconds 
- C. Every 90 seconds 
- D. Every 120 seconds

A:- PAgP sends control notifications every 30 seconds to the adjacent switch

110. You want to configure two switches so that LACP is used between the switches. Which mode should you use on both sides to force LACP?
- A. Active mode on both sides 
- B. Passive mode on both sides 
- C. Auto mode on both sides
- D. Desirable mode on both sides

A:- A, active mode on both sides assures us that the switches will start negotiation with only LACP.

**Active and Passive for LACP**
**Auto and Desirable for PAgP**

111. What is the effect of configuring a port channel with one side set to passive mode and the other side set to active mode?
- A. The channel group will use PAgP.
- B. The channel group will not be formed.
- C. The channel group will use LACP.
- D. The channel group will use EtherChannel.

A:- C.

112. Which command is used to verify the negotiation protocol for a port channel?
- A. Switch#show etherchannel 
- B. Switch#show port-channel 
- C. Switch#show interface
- D. Switch#show run

A:- A.

113. What is the effect of configuring a port channel with one side set to passive mode and the other side set to passive mode?
- A. The channel group will use PAgP.
- B. The channel group will not be formed.
- C. The channel group will use LACP.
- D. An unconditional port channel will be formed.

A:- B.

114. What is the effect of configuring a port channel with one side set to on mode and the other side set to on mode?
A. The channel group will use PAgP.
B. The channel group will not be formed.
C. The channel group will use LACP.
D. An unconditional port channel will be formed.

A:- D, an unconditional port channel is formed with no assisting control protocol

115. What is the IEEE specification for Spanning Tree Protocol (STP)? 
- A. 802.1X
- B. 802.1w 
- C. 802.1D 
- D. 802.1s

A:- C, 802.1D

116. Which statement is correct about STP?
- A. STP runs on a central switch by creating a topology database.
- B. STP runs as a distributed process on each switch and creates a topology database.
- C. STP uses routing protocols to check for network loops.
- D. STP uses the MAC address table to check for switching loops.

A:- B, Spanning Tree runs as a distributed process on each switch. Each switch creates and maintains its own topology database referencing and electing root bridge.

117. How does STP detect and monitor loops in networks?
- A. STP detects and monitors BPDUs being received on multiple interfaces.
- B. STP detects and monitors normal traffic frames being received on multiple interfaces.
- C. STP detects and monitors CDP frames being received on multiple interfaces.
- D. STP detects and monitors access ports in the same VLAN.

A:- A.

118. What is the IEEE specification for Rapid Spanning Tree Protocol (RSTP)?
- A. 802.1X
- B. 802.1w 
- C. 802.1D 
- D. 802.1s

A:- B.

119. What is the link cost with respect to STP?
- A. Link cost is the latency of a frame traversing across the link.
- B. Link cost is the calculation of all the ports in the path to the root bridge.
- C. Link cost is the monetary cost to traverse a link.
- D. Link cost is a numeric value associated with the speed of a link.

A:- D.

120. What is the path cost with respect to RSTP?
A. Path cost is the latency of a frame traversing across the link.
B. Path cost is the calculation of all the ports in the path to the root bridge.
C. Path cost is the monetary cost to traverse a link.
D. Path cost is a numeric value associated with the speed of a link.

A:- B.

121. Which protocol is a Cisco proprietary enhancement for 802.1D that allows separate spanning-tree instances for each VLAN?
- A. IEEE 802.1w 
- B. PVST+
- C. CST
- D. RSTP

A:- B.

122. Which protocol is a Cisco proprietary enhancement for 802.1W that allows separate spanning-tree instances for each VLAN?
- A. Rapid PVST+ 
- B. PVST+
- C. CST
- D. RSTP+

A:- A.

123. Which statement is correct about the Common Spanning Tree (CST)?
- A. CST elects a root bridge for each VLAN.
- B. CST elects a single root bridge for the entire physical network.
- C. CST has an immediate convergence because it elects a single root bridge.
- D. CST is best implemented for really large networks because it scales efficiently.

A:- B.

124. Which statement is correct about RSTP?
- A. RSTP allows for multiple root bridges.
- B. RSTP is backward compatible with STP.
- C. RSTP has a convergence time of around 50 seconds.
- D. RSTP has five port states to which the interfaces could possibly transition.

A:- B, RSTP has three transition modes and converges faster than STP, which is 50 seconds. It is backward compatible with STP 

125. How do switches participating in an STP network become aware of topology changes?
- A. The root bridge is responsible for sensing the change and sending Topology Change Notification BPDUs.
- B. Each switch is responsible for sensing the change and sending Topology Change Notification BPDUs.
- C. The root bridge polls each switch participating in STP for changes.
- D. The switches participating in STP poll the root bridge for changes.

A:- B, each switch is responsible for sensing changes to the topology; it is not the sole responsibility of the root bridge. Whenever the topology changes, a TCN is sent out all root ports and an acknowledgment is sent back. This happens until the root bridge sends back a notification.

126. Which of the following standards is an IEEE standard that replaces Rapid PVST+?
- A. 802.1X 
- B. 802.1w 
- C. 802.1D 
- D. 802.1s

A:- D, 802.1s MST is a standard bases upon PVST+. It is an open standard created by the IEEE which allows per-VLAN spanning-tree in multi-vendor switched networks.

127. You have a network consisting of four switches, all configured with the same bridge priority. Which switch will be elected the root bridge?
- A. 0081.023a.b433 
- B. 0011.03ae.d8aa 
- C. 0041.0611.1112 
- D. 0021.02fa.bdfc

A:- B-.

128. What is the default STP mode all Cisco switches run? 
- A. 802.1D
- B. 802.1w
- C. PVST+
- D. Rapid PVST+

A:- D, all cisco switches default to RPVST+

129. Which option is a correct statement about alternate ports in RSTP?
- A. An alternate port receives BPDUs from another port on the same switch and therefore can replace the designated port if it fails.
- B. An alternate port receives BPDUs from another switch and therefore can replace the designated port if it fails.
- C. An alternate port is always placed
- D. An alternate port receives BPDUs therefore can replace the root port

A:- D, an alternate port is a port in a discarding state. If the root port fails on the switch with the alternate port then the alternate port becomes the root port for that switch. 

130. How is the root bridge in STP elected?
A. The root bridge is the switch with the highest IP address and priority.
B. The root bridge is the switch with the lowest IP address and priority.
C. The root bridge is the switch with the lowest MAC address and priority.
D. The root bridge is the switch with the highest MAC address and priority.

A:- C.

131. Why is a root bridge elected for STP to function properly?
- A. The root bridge is the logical center of the STP topology.
- B. The root bridge allows all forwarding decisions of frames.
- C. The root bridge calculates the port cost for the rest of the network.
- D. The root bridge calculates the fastest path for the rest of the network.

A:- A, the root bridge is a point of perspective for the rest of the STP network. It is important to have a point of perspective to calculate which ports are blocked and which remain in a forwarding mode. 

132. How does a switch calculate the bridge ID?
- A. The bridge ID is a 6-byte number containing a 2-byte bridge priority and 4-byte IP address.
- B. The bridge ID is an 8-byte number containing a 4-byte bridge priority and 4-byte IP address.
- C. The bridge ID is an 8-byte number containing a 2-byte bridge priority and 6-byte MAC address.
- D. The bridge ID is a 10-byte number containing a 4-byte bridge priority and 6-byte MAC address.

A:- C, the bridge ID is made up of a 2-byte bridge priority and a 6-byte MAC address for a total of 8 bytes

133. What is the definition of a designated port?
- A. A port that is determined to have the lowest cost and placed in a forwarding state for a network segment
- B. A port that is determined to have the highest cost and placed in a forwarding state for a network segment
- C. A port that is determined to have the lowest path cost to the root bridge and placed in a forwarding state for a network segment
- D. A port that is determined to have the highest path cost to the root bridge and placed in a blocking state for a network segment

A:- A, a designated port that has the lowest cost compared to the higher cost of the redundant ports. It is laced into a forwarding state for a network segment. A designated port is determined to have the lowest cost and the not the highest cost.

134. Which is a correct statement about bridge port roles in STP?
- A. Every switch, excluding the root bridge, must have at least one root port.
- B. Every switch, including the root bridge, must have at least one designated port.
- C. Every switch, excluding the root bridge, must have at least one alternate port.
- D. Every switch, including the root bridge, must have at least one backup port.

A:- A, every switch in the network segment must have at least one root port. This is the port that leads back to the root bridge. The root bridge will have a designated port on the adjacent link. Every switch will have an active link back to the root bridge; however, those ports leading back to the root bridge are called root ports. 


135. What is the definition of an STP root port?
- A. A port that is determined to have the lowest cost to the network segment and placed in a forwarding state
- B. A port that is determined to have the highest cost to the network segment and placed in a forwarding state
- C. A port that is determined to have the lowest path cost to the root bridge and placed in a forwarding state for a network segment
- D. A port that is determined to have the highest path cost to the root bridge and placed in a blocking state for a network segment

A:- C.

136. What is the definition of an STP designated port?
A. A port that is determined to have the lowest cost to the network segment and placed in a forwarding state
B. A port that is determined to have the lowest path cost to the root bridge and placed in a forwarding state for a network segment
C. A port that is determined to have the highest path cost to the root bridge and placed in a blocking state for a network segment
D. A port that is determined to have the highest cost to the network segment and placed in a forwarding state 

A:- A, The designated port is the port with the lowest cost of the redundant links to the network segment. 

137. How is the bridge ID calculated for PVST+?
- A. The bridge ID is a 4-byte bridge priority, a 12-byte sys-id-ext, and a 6-byte MAC address.
- B. The bridge ID is a 4-byte bridge priority and sys-id-ext and a 6- byte MAC address.
- C. The bridge ID is a 4-bit bridge priority, a 12-bit sys-id-ext, and a 6-byte MAC address.
- D. The bridge ID is a 4-bit bridge priority, a 12-bit sys-id-ext, and an 8-byte IP address.

A:- PVST+ bridge ID comprises a 4-bit bridge priority calculated in blocks of 4096, a 12-bit sys-ext-id that is the VLAN ID for the segment and a 6 byte MAC address for the switch. 

138. What is the default bridge priority for all STP switches? 
- A. Bridge priority of 8,192
- B. Bridge priority of 16,384 
- C. Bridge priority of 32,768 
- D. Bridge priority of 65,526

A:- C. 

139. Which is a correct statement about bridge port roles in STP?
- A. A designated port is always in a blocking state.
- B. Every switch, including the root bridge, must have at least one designated port.
- C. Every switch, excluding the root bridge, must have at least one non-designated port.
- D. All ports on the root bridge are in a designated port state.

A:- D, the root bridge always has all of its ports in a designated mode or forwarding mode. 

140. Which is a correct statement about backup ports in RSTP?
- A. A backup port receives BPDUs from another port on the same switch and therefore can replace the designated port if it fails.
- B. A backup port receives BPDUs from another switch and therefore can replace the designated port if it fails.
- C. A backup port is always placed in a forwarding state.
- D. A backup port receives BPDUs from another switch and therefore can replace the root port if it fails.

A:- A, a backup port is a port in a discarding state. It receives BPDUs from another port on the same switch. If the forwarding port fails, then the backup port will become designated so that connectivity to the segment can be restored. 

141. What is the default wait time for STP convergence to complete? 
- A. Convergence takes 60 seconds to complete.
- B. Convergence takes 5 seconds to complete.
- C. Convergence takes 30 seconds to complete.
- D. Convergence takes 50 seconds to complete.

A:- D, 802.1D STP convergence takes 50 seconds to complete before the port is put into a state of forwarding or blocking. 

142. When a computer is connected to an interface with STP enabled in default mode, which is the correct order of the port transitions?
- A. Listening, learning, blocking, forwarding
- B. Forwarding, listening, learning, blocking
- C. Blocking, listening, learning, forwarding 
- D. Blocking, learning, listening, forwarding

A:- C.

143. Which statement describes an STP port that is placed into a blocking state?
- A. When a port is placed into a blocking state, it blocks all frames, including BPDUs.
- B. When a port is placed into a blocking state, it blocks redundant frames, excluding BPDUs.
- C. When a port is placed into a blocking state, it blocks all frames, excluding BPDUs.
- D. When a port is placed into a blocking state, it blocks redundant frames, including BPDUs.

A:- C. 

144. When a computer is connected to an interface with RSTP enabled in default mode, which is the correct order of the port transitions?
- A. Discarding, learning, blocking, forwarding 
- B. Discarding, listening, forwarding
- C. Blocking, listening, learning, forwarding 
- D. Discarding, learning, forwarding

A:- D, RSTP has three transitions when a computer is plugged in (no loops). The transitions are discarding, learning and forwarding, which allow for rapid convergence times. 

145. In RSTP, which port mode replaces the blocking and listening port states?
- A. Discarding 
- B. Learning 
- C. Forwarding 
- D. Backup

A:- A. (three port states: discarding, learning and forwarding)

146. Which new port state does RTSP have compared to STP? 
- A. Learning
- B. Forwarding 
- C. Blocking 
- D. Discarding

A:- D.

147. You receive a call that when computers boot up, they display an error message stating that they cannot reach a domain controller. However, after a few tries, the problem goes away, and the domain controller can be reached. Which command would you enter into the interface if you suspect spanning-tree convergence problems?
``` 
A. SwitchA(config-if)#no switchport spanning-tree
B. SwitchA(config)#switchport spanning-tree portfast 
C. SwitchA(config)#spanning-tree portfast default
D. SwitchA(config-if)#spanning-tree portfast
```


A:- D. 

148. On which types of ports should you configure PortFast mode? 
- A. Trunk ports
- B. Access ports
- C. Voice ports
- D. Designated ports

A:- B

149. What will the command spanning-tree portfast default entered in global configuration mode do?
- A. Turn on PortFast mode for all ports
- B. Turn on PortFast mode for all access ports only 
- C. Turn off spanning tree on all ports
- D. Turn off spanning tree on all access ports only

A:- B. 

150. What will happen if you plug a hub into two ports on the same switch configured with PortFast on all the interfaces?
- A. You will create a temporary switching loop.
- B. You will create a permanent switching loop.
- C. Both ports will sense the switch and err-disable.
- D. One of the links will disable via Spanning Tree.

A:- A.

151. Which feature will protect a switch immediately if it sees another switch’s advertisement?
- A. BPDU Guard
- B. BPDU Detection 
- C. Loop Guard
- D. UplinkFast

A.

152. What is the transition of states when PortFast is configured? 
- A. Forwarding, listening, learning, blocking
- B. Listening, forwarding, learning, blocking
- C. Listening, learning, forwarding, blocking
- D. Blocking, listening, learning, forwarding

A:- A.

153. Which command would you use to configure BPDU Guard on an interface?
```
A. SwitchA(config-if)#switchport mode bpduguard
B. SwitchA(config-if)#switchport bpduguard enable
C. SwitchA(config-if)#spanning-tree bpduguard enable 
D. SwitchA(config-if)#spanning-tree bpduguard
```

A:- C, [spanning-tree bpduguard enable]

154. C . BPDU Guard was turned on the trunk link. When the BPDU of the adjacent switch was seen, he switch turned the port into err-disabled mode. A spanning tree loop will not err-disable an interface, it wills imply block the offending port. 

155. Which option is a best practice when configuring links on an access switch?
- A. Never configure spanning-tree PortFast mode on an access link. 
- B. Always configure BPDU Guard along with PortFast.
- C. Always configure BPDU Guard on trunks.
- D. Always configure BPDU Guard along with UplinkFast.

A. :- B, configuring bpduguard along with PortFast ensures that the end device will always be forwarding. BPDU Guard ensures that in the event a BPDU is heard on the interface, the interface will enter into an err-disable mode. 
Portfast should only be configured on access ports.

BPDU Guard should never be configured on a trunk line since it will place the interface into an err-disable state when a BPDU is seen. 

156. Which command will show you if a port has been configured for PortFast mode?
``` 
A. Switch#show portfast
B. Switch#show interface fa 0/1
C. Switch#show spanning-tree
D. Switch#show spanning-tree interface fa 0/1
```

A:- D. 

157. Which command would you use to remove BPDU Guard from an interface?
```
A. Switch(config-if)#switchport bpduguard disable
B. Switch(config-if)#spanning-tree bpduguard disable
C. Switch(config-if)#no switchport bpduguard
D. Switch(config-if)#spanning-tree bpduguard disable
```

A:- D. 

158. You have BPDU Guard configured on an interface. What happens if a
BPDU is advertised on the interface?
- A. The interface will become administratively disabled. 
- B. The interface will become disabled.
- C. The interface will become err-disabled.
- D. A small switching loop will happen until convergence.

A:- The switch's interface will become err-disabled immediately. Once it is in err-disable mode, an administrator is required to reset the interface. 

159. Which command will show you if BPDU Guard is enabled by default? 
- A. Switch#show interface gi 0/1
- B. Switch#show spanning-tree summary
- C. Switch#show spanning-tree vlan 2
- D. Switch#show spanning-tree

A:- B. 

160. You are configuring an edge switch and want to make sure that someone does not plug a switch in accidentally. Which feature will you configure?
A. PortFast
B. UplinkFast
C. BackboneFast 
D. BPDU Guard

A:- D, BPDU Guard will protect the edge switch from someone accidentally plugging in another switch to a port dedicated for end devices. 

spanning-tree portfast will allow the interface to enter into a forwarding mode as it listens and learns BPDUs converging. 
UplinkFast helps faster convergence when an uplink fails between switches. 

161. You require a density of 100 wireless clients in a relatively small area. Which design would be optimal?
A. Autonomous WAPs with a WLC
B. Lightweight WAPs with a WLC
C. Autonomous WAPs without a WLC 
D. Lightweight WAPs without a WLC

A:- B, to achieve density and/or bandwidth in a relatively small area, you will need to deploy lightweight WAPs with a wireless LAN controller (WLC)Although Autonomous WAPs without a WLC would work, it would be problematic due to frequency coordination and roaming.
Lightweight WAPs do not function without a WLC

162. Which mode will allow a Cisco AP to detect interference of Bluetooth devices?
A. BT mode
B. Sniffing mode 
C. Analysis mode 
D. Monitor mode

A:- D, Cisco wireless access points can be placed into one of two modes: data serving mode or monitoring mode. In data serving mode, the AP will serve the data and act as a normal wireless access point. When the AP is switched into monitor mode, the AP can scan the wireless spectrum and report on interference

163. Which wireless mode allows for a network connection without a wireless infrastructure in place?
A. BSS 
B. ESS 
C. IBSS 
D. DS

A:- An independent basic service set. also known as an adhoc network, does not require any wireless infrastructure. Clients connect directly to each other over the 802.11 wireless spectrum. 

* A BSS is a small area with wireless coverage and is served by a single WAP.
* An ESS is a scaled out BSS, where many WAPs support client roaming between the WAPs and channel selection. 

164. Which statement is correct about root and non-root wireless devices?
- A. Non-root devices can connect to other non-root devices.
- B. Non-root devices can connect to root devices.
- C. Root devices can connect to other root devices.
- D. Repeaters are considered root devices.

A:- B, non-root devices such as clients and repeaters connect to root devices such as access points (WAPS). Non root devices cannot connect to other non-root devices in normal situations such as network infrastructure. 

165. Which type of WAP can operate independently?
- A. Lightweight WAP 
- B. WLC
- C. Mesh
- D. Autonomous WAP

A:- D.
