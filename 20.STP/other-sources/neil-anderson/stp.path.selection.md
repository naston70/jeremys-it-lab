## STP

#### Why Spanning Tree? 

Layer 2 Ethernet Path selection is controlled by the switch's MAC address tables.
In the example from Neil Anderson's STP, PC1 wants to send traffic to 10.10.10.2 on R1

- PC1 sends an ARP request for 10.10.10.2 - source MAC 1.1.1 dest MAC f.f.f
- Access Switch 3 learns MAC address 1.1.1 is available via f0/1
- Any subsequent traffic for 1.1.1 will be forwarded out of that port
- The switch floods the broadcast traffic out all ports apart from the one it was received on 
- switch CD1 learns MAC 1.1.1 is available via f0/24
- switch CD2 learns MAC 1.1.1 is available via f0/21
- Any subsequent traffic for 1.1.1 to hit either switch will be forwarded out those ports
- switch CD1 floods the broadcast out all ports it has apart from the one it was received on 
- The traffic continues up to R1 (and out other ports)
- R1 responds to the ARP request
- switch CD1 learns the MAC address 2.2.2 is available via interface g0/1
- any subsequent traffic for 2.2.2 will be forwarded out that port  
- CD1 already knows to forward the ARP reply from R1 for 1.1.1 out interface f0/24
- switch Acc3 learns that 2.2.2 is available via f0/24
- Any subsequent traffic for 2.2.2 will be forwarded out that port
- There is now an end-to-end path in both directions
**However, there is a problem - going back to the start:**
* Switch Access 3 receives the ARP request from PC1 and floods the broadcast traffic out all ports apart from the one it was received on
* This includes port f0/24 facing CD1
* Switch CD1 receives the ARP request from Acc3 and floods the traffic out all ports except from the one it was received on
* This includes g0/2 facing CD2
* Switch CD2 receives the broadcast traffic and floods it out all ports apart from the one it was received on
* This includes port f0/21 facing Acc3
* Switch Acc3 sends the traffic back to CD1 again, which will send it back to CD2 which will send it back to Acc3
* This now is running in a loop

**The Layer 2 Ethernet header does not have a TTL field to stop the looping traffic**

* There will be more broadcast traffic on a production network than one single ARP request
* This is known as a broadcast storm
* The network will crash because the amount of looping broadcast traffic will quickly overwhelm CPU and bandwidth 

#### Prevention of Layer 2 loops
- A broadcast storm is disastrous for the LAN and must be avoided at all costs
- STP is used to prevent Layer 2 loops
- It does so by detecting potential loops and blocking ports to prevent them
- STP automates failover as well as performing loop Prevention
- If an access layer switch's uplink fails the link will transition from a blocking state to a forwarding state
- convergence can be slow

#### How STP works
* STP is an industry standard protocol an is enabled by default on all vendors switches
* Switches send BPDU's out all port when they come online. These are used to detect other switches and potential loops
* The switch will not forward any traffic out any port until it is certain it is loop free 
* When the port first comes online it will be in the Blocking state
* STP will detect if the port forms a potential loop
* If there is no loop the port will transition to Forwarding state
* The process can take up to 50 seconds+

#### The Bridge ID 
- The BPDU contains the switch's Bridge ID which uniquely identifies the switch on the LAN
- The Bridge ID is comprised of the switch's unique MAC address and an administrator defined Bridge Priority Value
- The Bridge Priority can be from 0 - 65535, with 32768 being the default

#### The Root Bridge
* A Root Bridge is elected based on the switches Bridge ID values
* The switch with the lowest Bridge Priority value is preferred
* In the case of a tie the switch with the lowest MAC address will be selected
* The switches build a loop free forwarding path Tree leading back to the Root Bridge

#### Root Ports 
- Each switch's exit interface on the lowest cost path to the root bridge is selected as its Root Port

#### Load Balancing 
* A Spanning Tree instance does not do load balancing 
* If a switch has multiple equal cost paths toward the Root Bridge, it will select the neighbor switch with the lowest Bridge ID
* If a switch has multiple equal cost paths via the same neighbor switch towards the Root Bridge it will select the port with the lowest Port ID

#### Designated Ports
- Ports on the neighbor switch opposite the Root Port are Designated Ports 
- Root Ports point toward the Root Bridge, Designated Ports point away from it
- All ports on the Root Bridge are always Designated Ports

**Root Ports and Designated Ports are the most direct paths to and from the Root Bridge and transition to a forwarding state**

#### Other Links

* On the remaining links, the switches determine which of them has the least-cost path to the root
* If they have equal cost paths then the Bridge ID is used as a tiebreaker
* The port connecting this switch to the link is selected as a Designated Port
* Any ports not selected as Root Port or Designated Port can potentially form a loop
* These are selected as Blocking Ports
* Spanning Tree only blocks ports on one side of the blocked link 
* BPDUs continue to be sent over the link but other traffic is dropped

#### Root, Designated and Blocking Ports

The easy way to determine which ports are which:

1. Determine the Root Bridge first (best Bridge ID)
2. All ports on the Root Bridge are Designated Ports
3. Determine the Root Ports on the other switches (lowest cost to Root Bridge)

## Spanning Tree Versions

- industry standard and enabled by default

- IEEE Open Standards:
    * 802.1D STP: The original STP implementation. Uses one spanning tree for all VLANs
    * 802.1w RSTP: Significantly improved convergence time. Uses one spanning tree for all VLANs in the LAN
    * 802.1s MSTP: Enables grouping and mapping VLANs into different spanning tree instances for load balancing 

- Cisco Standards:
    * Per VLAN STP Plus (PVSTP+): Cisco enhancement to 802.1D. Uses a seperate STP instance for every VLAN. Default on Cisco switches.
    * Rapid Per VLAN Spanning Tree Plus (RPVST+): Cisco enhancement to 802.1w RSTP. Significantly improves convergence time over PVST+. Uses a seperate spanning tree per VLAN 

Cisco versions do not support grouping multiple VLANs into the same instance 

## Spanning Tree Verification

#### show spanning tree

Use ```show spanning-tree [vlan]``` command to see information about the stp instance running. The command output gives information on the version running, the root ID, bridge ID and the state of interfaces.
When the command is performed on a switch that is not root, it will show information on the Cost and which port is the Root Port for that device

#### show mac address-table

Use this command to verify the path traffic will take by viewing the mac addresses and which ports the traffic will go out to the mac on 

#### The Root Bridge Election
- Because Spanning Tree selects paths pointing towards the root bridge, it acts as a centre point of the LAN
- Best practice is to ensure a pair of high end core switches are selected as the 1st and 2nd most preferred Root Bridge 

* You can manipulate the Root Bridge election by setting Bridge priority 
* Default value is 32768, with lowest being preferred
* In a tie, the lowest MAC will be selected
* This is liable to pick the oldest switch 
```
#spanning-tree vlan 1 root primary
```
This will set a Bridge Priority of 24576, which is better than default. This manipulates the election. 
To ensure the desired switch also becomes the backup Root Bridge use command:
```#spanning-tree vlan 1 root secondary```, this sets a Bridge Priority of 28672 

#### STP and HSRP Relationship

HSRP should be configured to match the Spanning-Tree path to ensure traffic takes the most direct path to their default gateway

#### PortFast and BPDU Guard

- It can take up to 50 secs for Spanning-Tree to transition a port to forwarding state when it becomes active
- A loop cannot be formed on ports where a single end host is plugged in 
- You can make the port transition to a forwarding state immediately when it becomes active by disabling spanning-tree on the port
```
#int f0/10
#spanning-tree portfast
```

Enabling portfast can cause issues if a users adds a device or changes the cabling, resulting in a broadcast storm. To mitigate the risk we use BPDUGuard on the same ports. If a BPDU is received on the port it will automatically shutdown.
```
#int f0/10
#spanning-tree portfast 
#spanning-tree bpduguard enable 
```

#### Spanning Tree Root Guard

This prevents an unintended switch from becoming the root bridge.
If a port where Root Guard is enabled receives BPDUs that are superior than the current root bridge it will transition the port to root-inconsistent and not forward traffic over the port














