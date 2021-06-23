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

A:- 




8. What is the normal range of VLANs that can be modified on a Cisco switch with default configuration?
A. VLAN 1 to 1002 B. VLAN 1 to 1001 C. VLAN 2 to 1002 D. VLAN 2 to 1001
9. Static VLANs are being used on a switch’s interface. Which of the following statements is correct?
A. Nodes use a VLAN policy server.
B. Nodes are assigned VLANs based on their MAC address.
C. Nodes are unaware of the VLAN in which they are configured. D. All nodes are in the same VLAN.
10. A switch is configured with a single VLAN of 12 for all interfaces. All nodes auto-negotiate at 100 Mb/s full-duplex. What is true if you add an additional VLAN to the switch?
A. The switch will decrease its bandwidth due to overhead.
B. The switch will increase its count of collision domains.
C. The switch will now require a router.
D. The switch will increase its bandwidth due to broadcast domains.

