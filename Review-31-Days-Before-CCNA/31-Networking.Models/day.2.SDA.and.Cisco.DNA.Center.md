## SDA and Cisco DNA Center

Exam Topics
- Explain the role and function of network components
- Compare traditional campus device management with Cisco DNA Center enabled device management

#### SDA ARCHITECTURE 

SDA uses a controller and application programming interfaces (APIs) to communicate via southbound interfaces (SBIs) with the network infrastructure. SBIs include Telnet/SSH, SNMP, NETCONF and RESTCONF

#### Fabric

The network infrastructure, called the *fabric*, is divided into two parts:

* Underlay: This is most closely associated with the physical network. The underlay reveals additional devices and specifies how these devices are connected. Endpoints access the network through the Layer 2 devices. The underlay control plane is responsible for simple forwarding tasks
* Overlay: This is where tunneling protocols like Virtual Extensible LAN (VXLAN) are implemented to transport Layer 3 protocols such as IP security (IPSec) and Control and Provisioning of Wireless Access Points (CAPWAP). The overlay is where policies are specified. The overlay is not concerned with how the devices are physically or logically connected. Its job is to abstract these inherent complexities and limitations.

###### Underlay

The underlay includes the switches, routers, cables and wireless links used to create the physical network. It also includes the configuration and operation of the underlay to support the work of the overlay network. 

The SDA underlay configuration includes different SDA roles filled by each device. These include:
* Fabric edge node - a switch that connects to endpoint devices
* Fabric border node - a switch that connects to devices outside SDA's control, such as switches that connect to the WAN router 
* Fabric control node - A switch that performs special control plane functions for the underlay, requiring more CPU and memory

###### Overlay

Cisco chose the VXLAN protocol to create the tunnels used by SDA. When an SDA endpoint sends a data link frame to an SDA edge node, the ingress node encapsulates the frame and sends it across a VXLAN tunnel to the egress edge node
