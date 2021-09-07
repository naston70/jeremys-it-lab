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

The VXLAN tunnel in the overlay works like this:

1. An endpoint sends a frame
2. The frame is encapsulated in the VXLAN tunneling specification
3. The frame is forwarded to the underlay fabric
4. The other nodes in the underlay forward the frame based on the VXLAN tunnel details
5. The last SDA node removes the VXLAN details
6. The frame is forwarded to the destination 

#### Cisco DNA Center

Cisco DNA Center has two roles: 
* A controller in a network that uses Cisco SDA 
* A network management platform for traditional (non-sda) network devices

Cisco DNA Center supports several southbound APIs so that the controller can communicate with the devices it manages:

- Telnet, SSH and SNMP to support traditional devices
- NETCONF and RESTCONF to support newer devices 

#### Cisco DNA Center and SDA

Cisco DNA center and SDA make managing policies, such as access control lists (ACLs) much easier. 

Determining where to place new access control entries within an existing ACL can be complex and risky business. Also, unless an ACL is fully documented, effects of a new policy can be unknown.

However,, with SDA security groups, you can enforce a policy without even thinking about IP address ranges and ACLs. Instead of writing new ACEs each time a policy needs to implemented, the policy is defined in DNA Center. Then as needed, DNA center configures the devices in the fabric to enforce the security.

The SDA policy model solves the challenges with traditional ACLs:
* Each new security requirement can be considered separately, without analysis of an existing ACLs
* Each new requirement can be considered without searching for all the ACLs in the likely paths between endpoints and analyzing each and every ACL
* DNA Center keeps the policies seperate
* Each policy can be removed without fear of impacting the logic of the other policies

To implement policies in SDA, you then tie them to a security group. A security group is identified with a tag (SGT). If DNA center sees a permit action between source/destination pair of SGTs, DNA center directs the edge nodes to create the VXLAN tunnel. The SGTs for source and destination are added to the VXLAN header along with the VXLAN IDs

#### Cisco DNA Center Network Management Platform 