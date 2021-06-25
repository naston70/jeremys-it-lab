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
