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
