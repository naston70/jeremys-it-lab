## EtherChannel

#### Why we have EtherChannel?

Review - Campus Design

- End hosts do not constantly send traffic onto the network, most of the time the network connection is sitting idle
- Due to this you can connect less uplinks to each higher layer than the number of hosts you have and still maintain acceptable network performance
**Oversubscription:**
* A starting recommendation for oversubscription is 20:1 from the access layer to the distribution layer
* Recommendation is 4:1 for the distribution to core layer links
* These are only general values, traffic on each network should be analyzed to verify links are not congested

- Switches often have dedicated uplink ports with higher bandwidth than their access ports
- ie, a 48 port 1Gbps switch with a pair of 10Gbps uplinks
- This can help with the subscription ratio 
- 48 x 1Gbps clients = 48Gbps
- 2 x 10Gbps uplinks = 20Gbps
- Subscription ratio of 2.4 : 1
- However, in this case, when enabling two uplinks there is a problem. STP will shutdown one link

#### Spanning Tree Load Balancing

* Spanning Tree instances provide redundancy, but not load balancing 
* If a switch has multiple equal cost paths via the same neighbor switch towards the Root Bridge, it will select the port with the lowest Port ID.

#### EtherChannel
- EtherChannel-groups multiple physical interfaces into a single logical interface
- Spanning Tree sees the EtherChannel as a single interface, so it does not block any ports 
- Traffic is load balanced across all the links in the EtherChannel
- If an interface goes down its traffic will fail over to the remaining links

#### NIC teaming
- combines multiple physical network cards into a single logical interface 

#### EtherChannel Load Balancing 
(eg from udemy)

* A flow is a communication from a client to a server
* If a PC opens a web session to a server, and another opens an FTP session to another server, there are two flows going through the switch 
* A single flow is load balanced onto a single port channel interface 
* ie the packets in one flow stay on one interface and the other flow on another interface  
* Packets from the same flow are not load balanced round robin across all the interfaces in the port channel 
* Round robin load balancing could cause packets to arrive out of order and possibly break some applications

- Any single flow receives the bandwidth of a single link in the port channel as a maximum
Etherchannel provides redundancy as well as load balancing

#### Etherchannel Protocols

- LACP - Link Aggregation Control Protocol
    * open standard
    * the switches on both sides negotiate the portchannel creation and maintenance
    * this is the preferred method

- PAGP Port Aggregation Protocol
    * cisco proprietary
    * switches on both sides negotiate the port channel creation and maintenance
    * not recommended due to its proprietary nature 

- Static Etherchannel
    * The switches do not negotiate creation and maintenance but settings must still match on both sides for the port channel to come uplinks
    * Use if LACP is nt supported on both sides

- All protocols are configured with the ```channel-group```command


