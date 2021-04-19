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


