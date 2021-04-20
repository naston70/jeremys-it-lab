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





