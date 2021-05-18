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
- cURL in linux or requests in Python can also be used 
