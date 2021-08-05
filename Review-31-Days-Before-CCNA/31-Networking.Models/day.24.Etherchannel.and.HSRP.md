## EtherChannel and HSRP

#### Exam Topics

- Configure and verify EtherChannel
- Describe the purpose of first hop redundancy protocol

EtherChannel enables you to bundle multiple physical interfaces into one logical channel to increase the bandwidth on point-to-point links. In addition, EtherChannel provides a sway to prevent the need for Spanning Tree Protocol convergence when only a single port or cable failure occurs

Most end devices do not store routes to reach remote networks. Instead, an end device is typically configured with a default gateway than handles routing for the device. 

What if this device fails? To ensure that a device will still have access to remote networks, you should implement some type of default gateway redundancy in the network. That is the role of first-hop redundancy protocols (FHRPs)

#### EtherChannel Operation

EtherChannel, a technology that cisco developed, can bundle up to 8 equal-speed links between two switches. STP sees the bundle of links as a single interface. As a result, if at least one of the links is up, STP convergence does not have to occur. This makes much better use of available bandwidth while reducing the number of times STP must converge. 

Without the use of EtherChannel or modification of the STP configuration, STP would block all links except one. 

#### Benefits of EtherChannel

When EtherChannel is configured, the resulting virtual interface is called a port channel. The physical interfaces are bundled together into a port channel interface. EtherChannel has the following benefits:

* Most configuration tasks can be done on the EtherChannel interface instead of on each individual port, thus ensuring configuration consistency throughout the links. 
* EtherChannel relies on existing switch ports to increase bandwidth. No hardware upgrades are required
* Load balancing is possible between links that are part of the same EtherChannel
* EtherChannel creates an aggregation that STP recognizes as one logical link. 
* EtherChannel provides redundancy

#### Implementation Restrictions

