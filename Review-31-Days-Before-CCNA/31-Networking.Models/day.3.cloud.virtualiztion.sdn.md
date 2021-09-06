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