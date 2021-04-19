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


