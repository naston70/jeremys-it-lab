## Cloud Computing

#### Traditional IT Deployment Models 

- Traditional deployment models for IT services before Cloud:
    * On premises solutions
    * Colocation or 'Colo' services 

**On premise:**
    - all equipment located in your building
    - all equipment owned by you
    - clear lines of demarcation
    - equipment is CapEx
    - new equipment takes over a week to deploy
    - equipment requires technology refreshes 
    - redundancy needs to be considered 

**Colocation:**
    * A 'colo' is a data center location where the owner of the facility rents out space to external customers
    * The facility owner provides power, cooling and physical security for their customers server, storage and networking equipment
    * Independent colo providers such as Equinix offer customers multiple network connectivity options through a choice of network service providers 
    * Network service providers will also typically peer with each other in colo facilities 

#### Colo Solutions Characteristics 

- The colo provider owns the data center facility and is responsible for providing highly available power, cooling and physical security
- You own your own server, storage and networking equipment within the colo facility 
- The connections between your offices and the colo are your network service providers responsibility
- Equipment within the colo facility is a CapEx cost 
- Monthly colo hosting fees are an OpEX expense 
- New equipment will typically take over a week to deploy 
- Equipment requires technology refreshes 
- Redundancy needs to be considered 

## Defining Cloud Computing 

- Tends to be describes as 'IT services which are located somewhere else'
- But, colo facilities are off premise and are not cloud 
- Private cloud deployments are often on premise 
- NIST provides the following definition:

"Cloud computing is a model of enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources that can be rapidly provisioned and released with minimal management effort or service provider interaction"

###### On-Demand Self-Service
'A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider'

###### Rapid Elasticity
'Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited and can be appropriated in any quantity at any time'

###### Broad Network Access 
'Capabilities are available over the network and accesses through standard mechanisms that promote use by heterogeneous thin or think client platforms'
(accessible from anywhere with any device)

###### Resource Pooling
'The providers computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand'

###### Measured Service 
'Cloud systems automatically control and optimize resource use by leveraging a metering capability at some level of abstraction appropriate to the type of service (eg. storage, processing, bandwidth)'

## Server Virtualization

- Virtualization is one of the main enablers of Cloud Computing 
- It allows for resource pooling where multiple customers share the underlying hardware
- Virtualization has been around longer than cloud computing 

* The cloud provider does not provision seperate physical hardware for every customer
* A customer can sometimes deploy dedicated hardware devices at additional cost 

**Popular Type 1 (bare metal) hypervisors:**
- Type 1 hypervisors run directly on the system hardware

* VMware ESXi 
* Microsoft Hyper-V
* Red Hat KVM 
* Oracle VM Server 
* Citrix XenServer 

**Popular Type 2 hypervisors:**
- Type 2 hypervisors run on top of a host operating system 

* VMware Workstation, Fusion and Player
* VirtualBox
* QEMU
* Parallels 

Type 1 used for data-centre environments, Type 2 used for normal laptop / PC 

#### Virtualizing Network Devices 

* Virtualization supports running multiple virtual systems on a single physical system
* This provides flexibility and reduces costs
* Redundancy is supported by adding multiple physical systems which each have virtual systems running on them 

#### Clustering
- Clustering supports combining multiple physical systems into a single virtual system 
- This provides redundancy and increased performance 

#### Cloud Service Models 

* NIST defines three Service Models of how cloud services can be offered
    - IAAS: Infrastructure as a Service 
    - PaaS: Platform as a Service
    - SaaS: Software as a Service 
* Large cloud server providers offer multiple models 
* The three models define where the customer and provider area of responsibility are and at what level the customer gains access 
* The three models build on top of one another 

#### Cloud Deployment Models

- NIST define four Cloud Deployment Models
    * Public Cloud
    * Private Cloud
    * Community Cloud
    * Hybrid Cloud 

###### Public Cloud 
' The cloud Infrastructure is provisioned for open use by the general public. It may be owned, managed and operated by a business, academic or government organization or some combination of them. It exists on the premises of the cloud provider'

Providers such as: AWS, Microsoft Azure, IBM Bluemix, Salesforce 
- This is the most common type of deployment

###### Private Cloud 
'The cloud Infrastructure is provisioned for exclusive use by a single organization comprising multiple consumers. It may be owned, managed and operated by the organization, a third party, or some combination of them and it may exist on or off premises'

- Private cloud works the same way as Public Cloud, but the services are provided to internal business units instead of to the external public enterprises

#### How is Private Cloud Different than On Prem?

Private cloud fulfills the Cloud 'essential Characteristics'
    * On-Demand Self Service
    * Rapid Elasticity
    * Broad Networks Access
    * Resource Pooling
    * Measured Service 

- With traditional On Prem model, a business unit orders a new server by raising a ticket with the IT department. The server is then provisioned and configured by the teams as seperate manual processes 
- With Private Cloud, a business unit orders a new server typically through a web portal. The server is then completely automatically provisioned without requiring manual intervention 

* A company will use automation software such as Cisco UCS Director
* DNA center can be used as an SDN Controller
* Private CLoud is most suitable for large companies where the long term ROI and efficiency gains can outweigh the initial effort and cost to set up the infrastructure and automated workflows 

###### Community Cloud 
'The cloud infrastructure is provisioned for exclusive use by a specific community of consumers from organizations that have shared concerns (eg mission, security requirements, policy and compliance)'

- This is the least common deployment model, but sometimes used in government

