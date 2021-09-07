## Cloud, Virtualization and SDN

Exam Topics
* Describe characteristics of network topology architectures
* Explain Virtualization fundamentals
* Describe controller-based and software defined architectures 
* Compare traditional networks with controller-based networking 

## Cloud Computing 

Cloud computing involves large numbers of computers connected through a network that can be physically located anywhere. Cloud computing provides the following fits:
* Enables access to organizational data anywhere and at any time
* Streamlines IT operations by making it possible to subscribe to only needed services 
* Eliminates or reduces the need for onsite IT equipment, maintenance and management 
* Reduces costs for equipment, energy, physical plant requirements and personal training needs
* Enables rapid responses to increasing data volume requirements

Cloud providers rely heavily on Virtualization to enable the solutions they offer to clients 

#### Server Virtualization

Historically, organizations bought multiple hardware servers and the server administrator installed one or more network applications on the server, such as an email server or a file server.

###### Dedicated Server with One OS 

Each of these servers had its own CPU, memory, NIC and disk space. However, this model faces several challenges:
- If a component fails, the service is unavailable until the component is repaired or replaced
- Servers sometimes sit idle for long periods of time, waiting for clients to use them 
- Servers take up space and waste energy 

Server virtualization takes advantage of idle resources and consolidates the number of required servers. Virtualization seperates the operating system (OS) from the hardware. This also makes it possible for multiple OSs to exist on a single hardware platform. Each instance is called a VM 

A server with multiple WMs uses a hypervisor to manage access to the servers physical resources. The hypervisor sits between the VMs and the hardware.

#### Hypervisor Managing Four VMs

Another method for managing a set of VMs on a server, especially in a data center environment, is to use a virtual switch that connects the VMs to physical NICs

#### Virtual Switch and VMs

In a data center, multiple servers are placed in a rack. Physical NICs can be attached to ToR switches. Racks are lined up in rows by two redundant end of row EoR switches.

#### Cloud Computing Services

To understand the value of cloud computing, the effort to manage VMs in a traditional data center must be considered. The workflow follows:

1. A customer requests a VM or a new set of VMs
2. The data center engineer configures virtualization software
3. Virtualization software creates the VM 

While this process works, it does not have the characteristics laid out by NIST:
- On-demand self-service
- Broad network access
- Resource pooling
- Rapid elasticity 
- Measured service 

Cloud providers can offer a variety of services to meet the needs of customer, including these:

* **Software as a Service** (SaaS): access to services that are delivered over the internet, such as email, communication and Office 365. Users only need to provide their data 
* **Platform as a Service** (PaaS): access to the development tools and services used to deliver the applications. Customers can customize the virtualized hardware
* **Infrastructure as a Service** (IaaS): access to the network equipment, virtualized network services and network infrastructure support

Four primary cloud models exist:
- Public clouds: apps and services in a public cloud offered to general public
- Private clouds: apps and services for a specific org or entity
- Hybrid clouds: made up of two or more clouds, each part distinct but connected
- Community clouds: created for a specific community

#### Virtual Network Infrastructure

A virtual network infrastructure consists of a collection of virtual network functions (VNFs), including virtual switches, virtual server load balancers (SLBs), virtual routers and virtual firewalls. 

#### Software Defined Networking

Network programmability refers to the trend toward software defined networking At its core SDN decouples the data, control and management planes from the physical device and virtualize them and defines the networking functions in software. This creates an architecture that can be more efficiently and effectively managed through programmatic control 

###### Data, Control and Management Planes

A traditional networking device contains two planes. The data plane is responsible for forwarding data as quickly as possible. To do so, it relies on tables built by the control plane. Actions taken by the data plane include the following:
* Layer 2 and Layer 3 de-encapsulation/encapsulation 
* Addition or removal of an 802.1Q trunking header
* MAC address table lookup
* IP routing lookup
* Data encryption and addition of a new IP header (as in a VPN)
* Change to the source of destination IP address (as in NAT)
* Message discard due to a filter (such as an ACL)

The control plane does all the calculations for populating tables used by the data plane and manages control messages between other networking devices.

The following are the most common control plane protocols:
* Routing protocols:- OSPF, EIGRP, RIP, BGP
* IPv4 ARP
* IPv6 NDP
* Switch MAC learning 
* STP

The management plane is responsible for all functions that are not directly related to controlling the data plane. Management protocols include Telnet, SSH, SNMP, Syslog

#### Controllers 

Traditionally the control plane has been part of the device OS and has been distributed across every device. That means every device must spend some resources calculating and maintaining Layer 2 and Layer 3 data structures. When viewed as a whole, the networks control plane is distributed across all the networking devices. 

In SDN, the functions of the control plane can be completely removed from the physical networking devices and placed in a centralized application called a controller. This frees up the devices to focus on data plane tasks.

The controller sits at the top of a network topology diagram and the connections to the networking devices are called the *southbound interface* (SBI).

A *northbound interface* (NBI) also exists between the SDN controller and the applications that are installed on the controller. These applications are what enable network programmability

#### SDN Examples: Open SDN and OpenFlow

The Open Networking Foundation (ONF) model of SDN uses an SBI called OpenFLow. OpenFlow is a protocol used between the controller and the networking devices to manage traffic flows. ONF's controller, OpenDayLight, is the result of a collaborative effort among many vendors.

In addition to OpenFlow, the controller has SBIs for other activities, such as configuring network devices (NetConf), managing routes (BGP-LS and PCEP) and switching traffic between VMs (OVSDB)

NBIs typically include Java APIs for applications and the RESTful API. REST uses HTTP messages to transfer data to other applications that are not running on the controller. 

The definition and operation of these SBI and NBI protocols is beyond CCNA. 

#### SDN Example: The Cisco Application Centric Infrastructure (ACI)

The Cisco SDN solution for data centers is ACI. ACI uses the concept of endpoint groups and policies. An endpoint group is a collection of similar VMs, such as a set of virtual switches for one of the data centers tenants. Policies define which endpoint groups can communicate with who,. 

The Cisco Application Policy Infrastructure Controller (APIC) uses the endpoint topology and policies to direct the network regarding what needs to be in the forwarding tables and how to easily react to VM changes. ACI uses a partially centralized control plane, RESTful and native APIs and OpFlex as an SBI.email

OpFlex is the cisco solution for SBI communication with networking devices. Whereas OpenFlow centralizes the network control by pushing commands directly from the SDN controller, OpFlex uses policies to push command implementation down to a distributed network of controllers. 

#### SDN Examples: Spine and Leaf

 Cisco ACI uses a spine and leaf design. The physical network has a number of spine switches and a number of leaf switches. Links between switches can be single links or multiple parallel links. Spine and leaf switches are connected using the following design guidelines:
 * Each leaf switch must connect to every spine switch 
 * Each spine switch must connect to every leaf switch 
 * Leaf switches cannot connect to each other 
 * Spine switches cannot connect to each other 
 * Endpoints connect only to leaf switches 

#### SDN Examples: The Cisco APIC Enterprise Module (APIC-EM)

