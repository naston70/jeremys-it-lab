# PortChannels

STP has the purpose of removing loops and will disable links in the network. To overcome that PortChannels (EtherChannels) are used. A PortChannel will bundle multiple physical interfaces into one logical interface. Once in this bundle, STP can only block or permit the logical interface. If the interface is in the forwarding state, all the interfaces are too. Aggregating links into logical ones defined as LAG (LINK AGGREGATION)

#### PortChannel LAB - Topology

PortChannels can be used everywhere. This lab will show the three different options for creating a PortChannel.

[SW1] ======== [SW2] ======== [SW3] ======== [SW4] 

SW1 & SW2 use Fa0/1 and Fa0/2 between each other
SW2 & SW3 use Fa0/10 and Fa0/11
SW3 & SW4 use Fa0/20 and Fa0/21

Requirements: 
 * Create a PortChannel between SW1 and SW2
 * Create a PortChannel with a standard protocol between SW2 and SW3, with SW2 being the main
 * Use a Cisco proprietary protocol to create a PortChannel between SW3 and SW4 , where both are main

All PortChannels need to be trunks.

#### PortChannels

A PortChannel is a **logical association** of physical links, that appear as one single link. The PortChannel can be configured like any other; set an IP, configure it as a trunk, enable PortFast etc. The configurations will be automatically replicated to the children physical interfaces.

PortChannel interfaces must be of the same type only with a usual limit of 8 links

For a PortChannel to work, both devices must agree on it. They must know they are talking over a PortChannle and to treat it like a single link. 

PortChannel Modes and Protocols:

With a **static PortChannel**, the existence of the PortChannel needs to be hardcoded. They will then begin to treat all the links as a bundle. However, if one of the two devices is misconfigured, the other will notify out-of-order packets and shut the link down

A more scalable approach is to use a dynamic protocol to negotiate the existence of the PortChannel. There is:
	- LACP, Link Aggregation Control Protocol
	- PAgP, Port Aggregation Protocol
They are not interoperable so both devices will need the same protocol configured.

#### LACP

LACP is the standard version and is widely accepted. LACP will be found on switches from vendors other than Cisco and on servers. If a port is configured to work in LACP, it will start to work as a standalone physical port. It will start to send and listen for LACP messages. If/when it finds an LACP peer on the other side, the port will be automatically added to the bundle. LACP has two modes, active & passive. An active port will actively try to make the channel while a passive one will wait for the other side to initiate.

#### PAgP

Cisco proprietary aggregation protocol. It works exactly like LACP, but only Cisco supports it. 

#### Inside a PortChannel

No matter if ports are hard-coded statically or if a dynamic protocol negotiated them: once they are in a bundle they are in that bundle. Once in that bundle **hashing** is used to select which packet gets sent through which port.

Each port is associated with a specific identifier, the hash. Once a packet arrives on the switch and the switch understands that it should go on a PortChannel, it runs a hash function on the headers.

## Configuring PortChannels


