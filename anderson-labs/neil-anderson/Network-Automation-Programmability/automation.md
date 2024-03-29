## Benefits of Automation and Programmability

Traditional way to manage network devices is one at a time using SSH to the command line. Copying and pasting from a text file template is common. GUI tools to manage one device at a time have also been available for a long time but have typically been slow and inefficient 

#### NMS - Network Management Systems 
- NMS such as SolarWinds, CiscoWorks and Cisco Prime Infrastructure are available
- They use protocols such as SNMP and Netflow to gather information and report on the state of the network
- SNMP was originally proposed in 1988
- SNMP can also be used to push configuration to devices but it has limited functionality 
- Solutions can be complex and difficult to implement 
- SNMP also has security concerns

###### Issues with traditional Network Management

* Configuring one device at a time is time consuming and inefficient
* It increase the likelihood of mistakes
* Individual edits to multiple devices by several engineers over time with little version control leads to configuration drift
* Having non standardized configurations and accessing one device at a time is also inefficient for troubleshooting 

## Network Automation 

Automation can be used for:
    * Device configuration
    * Initial device provisioning 
    * Software version control 
    * Collecting statistics 
    * Compliance verification 
    * Reports
    * Troubleshooting

- Network Programmability enables automation which reduces human to machine interaction 
- This greatly reduces the chance of human error such as typos
- Modern tools have been built with monitoring, configuration and troubleshooting in mind 
- Much more scalable than single device configurations 
- It can provide configuration version control 
- It can also provide software version control 

- Troubleshooting is more efficient with a system wide view and correlation between events 
- Events and error codes can be acted on programmability
- Improving configuration and troubleshooting efficiency reduces OPEX

#### Assurance
Assurance can:
- Ensure devices have a standardized configuration
- Provide reports on and correct any exceptions 
- Provide correlation between events on different devices 
- Automatically take corrective actions on events and error codes 


#### Which Automation Method to Use 

* There are multiple methods that can be used to automate network management - Python scripts, NETCONF, RESTCONF, Ansible, Puppet; SDN, Cisco DNA center. etc.
* Not all methods are supported by all devices 


## Data Serialization 

- Data Serialization is the process of converting structured data to a standardized format that allows sharing or storage of the data in a form that allows recovery of its original structure 
- It allows transfer of the data between different systems, applications and programming languages 
- XML, JSON and YAML are human machine readable, plain text data encoding formats

* Data formats are mostly interchangeable 
* Which one to use depends on support in the system and even which is easiest 

#### JSON JavaScript Object Notation

- 2013
- Easier for humans to read and work with than XML
- Can be imported into directly into JavaScript
- White space has no meaning 
- RESTful APIs often use JSON

#### JSON Data Types
- Object
- Array
- String
- Number
- Boolean
- Null

#### Data Type: Object
* An object is an unordered collection of key/value pairs
* They are surrounded by curly braces {}
* Keys must be strings and values must be a valid JSON data type 
* Keys and values are seperated by a colon 
* Each key/value pair is seperated by a comma 

#### Data Type: Array 
* An Array is an ordered list of values 
* They are surrounded by square brackets 
* Values must be a valid JSON data type 


## XML eXtensible Markup Language
- 1998
- Widely used
- XML was designed to describe and transfer data, while HTML focuses on presentation 
- White space has no meaning 
- <key>value</key> contained with object tags 

## YAML: YAML Aint Markup Language 
- Often used in Python, Perl and Ansible
- Designed to be easily read 
- White space is important 
- Anything at a common indentation level is considered related at the same level
- Starts with ---
- key: value representation 
- - indicates a list 
- Ansible playbooks use YAML 


## API - Application Programming Interface 

* An API is a way for a computer program to communicate directly with another computer program 
* It is typically used to perform CRUD operations 
* The two main types of APIs for web services are SOAP and REST 
* NETCONF and RESTCONF are APIs specifically designed to work with network devices 

#### CRUD 
Create, Read, Update, Delete

## SOAP - Simple Object Access Protocol 

* Soap is a standard communication protocol system that permits processes using different OS's line Linux and Windows to communicate
* Transport is typically HTTP(S) and the data format is always XML 
* As it is a protocol it has strict standards to adhere to 

## REST - representational state transfer

- REST is an architecture, not a protocol, It gives guidelines for the structure and organization of an API 
- It supports any transport and data format 
- HTTP(S) transport and JSON data format are common 
- Typically faster performance and easier to work with than soap 

#### REST Constraints 

* Client-server architecture: the client sends a request, the server sends a response 
* Uniform Interface: Provides simplicity 
* Statelessness: no client context is stored on the server between requests 
* Cacheability: responses must define themselves as either cacheable or non-cacheable 
* Layered system: any intermediary devices such as load balancers must be transparent to the client and server 
* Code on demand: servers can temporarily extend or customize the functionality of a client by transferring executable code 

**REST Request URL:**

- Request method must be sent 
- Headers with key:value pair information about the request can be added 
- Post, Put and Patch requests include data in the body 

Response codes 
1xx, 2xx, 3xx, 4xx, 5xx


## MODEL Driven Programmability - YANG, NETCONF, RESTCONF and gRPC 

- A data model is a well understood and agreed upon method to describe something 

#### YANG -  Yet Another Next Generation 
* YANG is a data modelling language which provides a standardized way to represent the operational and configuration data of a network device 
* It can be used both internally and when packaged for transmission 

## Network Management Transport 
* The configuration and operational status of a network devices components and services can be remotely read or written to.
* NETCONF, RESTCONF and gRPC are APIs which describe the protocols and methods for transport of network management data 

#### NETCONF and YANG 
* NETCONF was designed as a replacement for SNMP
* NETCONF and YANG provide a standardized way to programmatically inspect and modify the configuration of a network device 
* YANG is a data modelling language which provides a standardized way to represent the operational and configuration data of a network device 
* NETCONF is the protocol that remotely reads or applies changes to the data on the device 
* XML encoding is used 
* The transport is over SSH or TLS 

#### NETCONF Protocol Stack 
- **Content** - the data to be inspected or changed 
- **Operations** - eg. <get-config>. <edit-config>. Initiated via RPC methods using XML encoding
- **Messages** - RPC Remote Procedure Calls
- **Transport** - between client and sever. Supports SSH or TLS 

## RESTCONF

- standardized is 2017, builds on NETCONF
- It is an IETF draft that standardizes how to map a YANG specification to a RESTful Interface
- Uses HHTP verbs over a REST API 
- RESTCONF is not intended to replace NETCONF but is simpler to use
- XML or JSON encoding 
- Transport is HTTP(S)

##gRPC

- Google RPC is an open source remote procedure call system initially developed at google in 2015 
- It is well suited to collecting telemetry statistics 
- CPB Google Protocol Buffers encoding is used 
- The transport is HTTP/2


## Postman 

- Very popular tool to test operations of APIs 
- Standalone or as a plugin 
- Collections and environment variables allow for the easy reuse of requests 
- Requests can be exported as code in multiple languages 
- cURL in Linux or requests in Python can also be used 

## Configuration Management Tools 

- configuration management systems are designed to make controlling large numbers of devices easy for administrators and operations teams 
- They allow you to control many different systems in an automated way from one central location 
- Popular options:
    * Puppet
    * Ansible
    * Chef 

**configuration management tools:**
- Can automate the provisioning and deployment of servers and network devices 
- Require little programming knowledge
- Have established development practices including version control and testing 

## Ansible 

* Runs on Python2 or 3
* Agentless
* Push model 
* Communicates over SSH by default 
* Simpler than other tools 
* Released in 2012
* Ansible modules are pre-built Python scripts
* Many pre-built network modules exist 
* Ansible inventory files define all hosts that will be managed by the control workstation 
* Ansible playbooks are YAML files that outline the instructions it needs to run 


## Puppet 

- Typically uses an agent on the target devices 
- 'Puppet Master' runs on Linux+
- Pull model, agent checks in every 30 mins by default
- Written in Ruby 
- Use proprietary DSL rather than YAML 
- A 'Manifest' defines the devices properties 
- It can check configuration consistency 
- Created in 2005

## Chef

* An Agent must be installed on the target devices 
* Pull model 
* Written in Ruby 
* Terminology is Cook Book > Recipe
* Released in 2009

## configuration management tool support

- Ansible, Puppet and Chef were designed primarily for server system administration 
- Ansible is typically more suitable for network environments because it does not use an agent. It is also simpler to use and learn 
- Cisco devices usually cant run an agent 


## SDN - Software Defined Networking 

**Router and Switch Planes:**
- Data (Forwarding) Plane: Traffic which is forwarded through the device.
- Control Plane: Makes decisions about how to respond to forward traffic. Control plane packets such as routing protocol or spanning trees updates are destined to or locally originated on the device itself 
- Management Plane: The device is configured and monitored in the management plane. 

#### SDN - Data and Control Plane Separation

* Network Infrastructure devices are responsible for their own individual control and data planes in a traditional environment
* SDN decouples the data and control planes 
* The network Infrastructure devices are still responsible for forwarding traffic but the control plane moves to a centralised SDN controller 

- Rules for packet handling are sent to the network infrastructure devices from the controller
- The network infrastructure devices query the controller for guidance as needed and provide it with information about the traffic they are handling 

#### Pure SDN vs Hybrid SDN 

* With a pure SDN the control plane runs purely on an SDN controller and the data plane runs purely on network devices 
* With a hybrid SDN the majority of the control plane intelligence is provided by an SDN controller, but the network devices retain some control plane intelligence as well as the data plane operations 
* Most implementations use a hybrid SDN 

## SDN architecture

1. [Application Layer - SDN Business Applications]

Northbound APIs - typically REST

2. [Control Layer -- SND Controller (network services)]

Manages, with Southbound APIs the: (eg OpenFlow, SNMP, REST, NETCONF, SSH)

3. [Infrastructure Layer (devices)]

## Cisco SDN Controllers: APIC 

- APIC - Application Policy Infrastructure Controller 
- The main component of the Cisco ACI (Application Centric Infrastructure)
- Designed to manage data center environments with Nexus Switches 

----------------------------------------------------------------------------

## Cisco SDN Controllers: DNA Center 

- DNA Digital Network Architecture 
- Designed to manage enterprise environments - campus, branch and WAN 

----------------------------------------------------------------------------

## Cisco DNA Digital Network Architecture 

* Cisco DNA enables you to streamline operations and facilitate IT and business innovation 
* **Intent-based networking** (IBN) built on **Cisco DNA** takes a **software-delivered** approach to automating and assuring services across your WAN and your campus and branch networks 

- 3 of the main building blocks of Cisco DNA and Software Defined Architecture are:
- DNA Center 
- SD-Access
- SD-WAN 

#### DNA Center Appliance 

* The DNA Center Appliance runs on Cisco UCS server hardware
* The underlying operating system is Linux 
* It can be clustered for redundancy 

#### IBN Intent Based Networking
- Intent Based Networking transforms a traditional manual network into a controller led network that translates the business needs into policies that can be automated and applied consistently across the network 
- The goal is to continuously monitor and adjust network performance to help assure desired business outcomes 

#### IBN Intent Based Networking Example 1

Example 1: a QoS policy roll-out 
* The Intent: The network policy is first defined, for example providing guaranteed service to voice and video across network locations 

**Traditional Networking:**
* The network team researches the plans and implementations, then configures each network device individually
* Different network device models require different commands 
* This method is very time consuming and liable to mistakes 

**Intent Based Networking:**
* The network team creates an Application Policy in DNA Center specifying voice and video as business relevant applications
* DNA Center automatically configures the best practice QoS settings on the network devices
* This can reduce total deployment time from months to minutes 


#### IBN Intent Based Networking Example 2

Example 2: Securing traffic flows in the campus 
* The Intent: Users in DeptA and DeptB must have connectivity to other users in their own department, and to the company servers. They must not have connectivity to users in the other department 

**Traditional Networking:**
- The network team plans the VLAN, IP subnet and ACL implementation, then configure each switch individually
- Users are expected to stay plugged in to the same access port. They are assigned a VLAN and IP address based on their physical location
- This method is very time consuming, liable to mistakes and does not support mobility 

**Intent Based Networking:**
- The network team creates a Group-Based Access Control Policy in DNA Center which specifies the allowed traffic flows 
- Users log in from and can move to any physical location on campus 
- They are authenticated by Cisco ISE Identity Services Engine and assigned a Security Group TAG controlling their access 


## DNA Center Features

####Network Plug and Play 

- Network Plug and Play allows routers, switches and wireless access points to be deployed in remote offices with zero touch configuration
- The device is physically installed in the remote office and connected to the network
- It discovers DNA center through various methods including DHCP option 43 or DNS 'pnpserver.domain-name.com'
- It then registers with and downloads its configuration from DNA Center 
- This ensures consistent configuration of remote office devices with no need for a network engineer on-site 

#### Assurance
* Assurance guarantees that the infrastructure is doing what you intended it to do 
* DNA center receives information from all the network devices and ISE (Identity services engine) etc 
* DNA Centers correlation engine can identify 150+ different types of network and client Issues
* DNA Center reports the problem and provides recommended remediation actions 

#### Network Time Travel 
* administrators can drill down into the health status of network devices and clients
* You can see the current status and also view historical information
* This is useful to troubleshoot intermittent problems or issues which occured in the past

#### Path Trace 
* An engineer can use Path Trace to query DNA center for the path that traffic takes over the network 
* This aids troubleshooting

## API Support
- Everything that can be done via DNA center gui can also be done via a northbound REST API 
- DNA Center also supports 'east' and 'west' bound APIs for integration with other services such as reporting and analytics servers

## Cisco SD-Access

**Traditional Access Control:**

- The traditional way to control access to nd traffic flows within a network is with fixed VLANs, IP addresses and ACLs
- Users are expected to always connect to the same physical port where they are assigned an access VLAN and IP subnetACLs control traffic flows between IP subnetACLsThe configuration can get complex and each device is configured individually
- The solution does not support user mobility 
 
 The new approach:

 **Software Defined Access:**
 * SD-Access is a newer method of network access control which solves the limitations of the traditional implementation 
 * Traffic flow security is based on user identity, not physical location and IP address 
 * Users log in from and can move to any physical location in the network a

- Two components are required for SD-Access:
- Users are authenticated by the ISE Identity Services Engine 
- The security policy is configured on the DNA center 

#### Underlay and Overlay Network 
- SD-Access uses an underlay and overlay network 
- An underlay network is the underlying physical network. It provides the underlying physical connections which the overlay network is built on top of
- An overlay network is a logical topology used to virtually connect devices. It is built over the physical underlay network 
- The combination of underlay and overlay forms the SD-Access network fabric

###### Underlay Network
- When SD-Access is deployed into an existing network, any configuration can be used for the underlying physical network. Links between devices can be layer 2 or layer 3 and any routing protocol can be used 
- DNA Center can be used to automatically provision the underlay network in new sites. In this case layer 3 links are used between devices and IS-IS is used as the routing protocol 

###### Overlay Network 
- LISP is used for the Control Plane 
- VXLAN is used for the data plane
- Cisco TrustSec CTS is used for the policy 
- Each technology has been optimized for SD-Access

######  Policy Plane - Cisco TrustSec CTS
* Users are authenticated by the ISE identity services engine 
* The security policy is configured on DNA Center 
* Users are allocated an SGT Scalable Group Tag 
* Cisco TrustSec secures traffic flows based on security policy and SGTs 
* Standard TrustSec needs end to end TrustSec devices, SD-Access uses overlay tunnels so can work with other devices 


## SDA - SD WAN

**Traditional WAN deployments:**
- Individual device configuration
- Configuration is not standardized organization wide 
- Focus is on link connectivity, not the required performance for applications
- Typically difficult to migrate to another WAN service 

#### SD-WAN 
* Cisco acquired Viptela in 2017 to enhance their SD-WAN solution 
* It provides automated setup of WAN connectivity between sites 
* Monitoring and failover is automated 
* Traffic flow is application aware 

#### SD-WAN Benefits:
- Automated, standardized setup of connectivity between sites 
- Transport independent 
- Simplified, integrated operations 
- More flexibility and easier to migrate WAN services 
- The required, predictable performance for important applications
- Integration with the latest cloud and network technologies
- Lower cost 

#### Data Plane - vEdge Routers 
- vEdge routers run the data plane 
- They are physical or virtual routers 
- They form an IPsec encrypted data plane between each other 
- A site can have 2 vEdge routers for redundancy

#### Control Plane - vSmart Controllers 
- vSmart controllers run the control plane 
- They are the centralized brain of the solution 
- They run as virtual machines
- They distribute policy and forwarding information the the vEdge routers inside TLS tunnels 
- Each vEdge router connects to two vSmart controllers for redundancy 

#### Management Plane - vManage NMS 
- The vManage NMS provides the management plane GUI
- It enables centralized configuration and simplifies changes
- It provides real time alerting 
- It runs a virtual machine 
- Multiple vMange NMS are clustered for redundancy

#### Orchestration - vBond orchestrator 
* The vBond orchestrator authenticates all vSmart controllers, vMange NMS and vEdge routers that join the SD-WAN network 
* It enables routers to discover each other, vMange and vSmart
* It has a public IP address and is deployed in the DMZ 
* It runs as a virtual machine 
* Multiple vBond orchestrator's can be deployed with round robin DNS 

## ZTP Zero Touch Provisioning service 
* Cloud based shared service hosted by cisco 
* Utilized on first boot of vEdge router only 
* Directs it to vBond to orchestrate joining the network 
* On premise or cloud 


## Building the Data Plane:

- The vSmart controller directs the vEdge routers to build a full mesh (by default) of IPsec VPN tunnels between themselves 
- vSmart propagates policy and routing information to the vEdge routers with OMP Overlay management Protocol 
**BF VPN Tunnel Monitoring:**
- Bidirectional Forwarding Detection packets are sent over all VPN tunnels 
- This detects if a tunnel goes down and also provides latency, jitter and loss statistics 

#### Traffic Forwarding Options:

If multiple tunnels are available traffic can be load balanced (ie internet and mpls) over the tunnels 



