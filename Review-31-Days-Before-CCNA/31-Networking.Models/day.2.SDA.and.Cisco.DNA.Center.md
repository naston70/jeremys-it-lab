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
