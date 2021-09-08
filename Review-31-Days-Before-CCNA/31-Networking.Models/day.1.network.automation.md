## Network Automation 

Exam Topics:

- Explain how automation impacts network management
- Describe characteristics of REST based APIs (CRUD, HTTP verbs, data encoding)
- Recognize the capabilities of configuration management mechanisms Puppet, Chef, and Ansible
- Interpret JSON encoded data

#### Data Formats

Data formats provide a way to store and exchange data in a structured format. These are some common data formats used in network automation and programmability:

* JavaScript Object Notation
* Extensible Markup Language
* YAML Ain't Markup Language

#### Data Format Comparison

| Data | Central Purpose        | Common use     |
|------|------------------------|----------------|
|      |                        |                |
| JSON | General data modelling | REST APIs      |
| XML  | Data text markup       | REST APIs, web |
| YAML | General modelling      | Ansible        |
|      |                        |                |

#### JSON Data Format 

JSON is human-readable data format used by applications for storing, transferring and reading data. It is easy to parse and can be used with most modern programming languages

###### JSON Syntax Rules 

JSON data is a collection of key:value pairs that follow these rules:

- One key:value pair
- Key: text inside double quotes and before the colon that is used as the name that references a value
- Value: The item after the colon that represents the value of the key, which can be:
    * Text
    * Numeric
    * Array
    * Object
- Multiple pairs: when listing multiple key:value pairs, seperate the pairs with a comma at the end of each pair, except the last.

## RESTFUL APIs 

APIs exist to allow two programs to exchange data. Some APIs are for interprogram communications within a single operating system (OS). Other APIs are available to programs that run on other computers. These APIs must define the networking protocol. Many are based on REST. REST is an architectural style for designing web service applications. A REST API is an API that works on top of the HTTP protocol. It defines a set of functions developers can use to perform requests and receive response through HTTP, such as GET and POST. An API can be considered RESTful if it has the following features:

* Client/Server: The client handles the front end, and the server handles the back end. Either can be replaced independently of the other.
* Stateless: No client data is stored on the server between requests. The session state is stored on the client
* Cacheable: Clients can cache responses to improve performance

#### RESTful Implementation

A RESTful web service is a collection of resources with four defined aspects:

- The data format supported by the web service, which is often xml, json or yaml
- The set of operations supported by the web service using HTTP methods
- The API, which must be hypertext driven
- The base uniform resource identifier for the web service

RESTful APIs use common HTTP methods - PUT, POST, PATCH, GET, DELETE. These methods correspond with RESTFUL operations: create, read, update and delete

#### RESTful API Requests

A RESTful API is requested by using a URI, which is a string of characters that identifies a specific network resource. A URI has two specializations:
- Uniform resource name (URN): Identifies only the namespace of the resource without reference to the protocol
- Uniform resource locator (URL): Defines the network location of a specific resource on the network

###### Structure of a URI

* Protocol/scheme: HTTPS or another protocol, such as FTP, SFTP, mailto or NNTP
* Hostname
* Path and filename
* Fragment: ie #page1

A RESTful API request elicits a response from the API server. There are different parts of the API request:
- API server: The URL for the server that answers REST requests
- Resources: Specifies the API that is being requested
- Query: Specifies the data format and information the client is requesting from the API service. Queries can include
    * Format: usually JSON but can be xml or yaml
    * Key: key for authorization, if required
    * Parameters: Parameters are used to send information pertaining to the request

#### Configuration Management Tools

Configuration Management Tools provide different methods to define logic and processes that indicate what changes the tools should make, to which devices and when. For each tool, engineers use a language of some kind to define the action steps. The language is often a language defined by the company offering the tool but the tools language is generally easier to learn than a programming language. 

#### Ansible

Ansible uses an agentless architecture to manage network devices. Agentless means that the network device does not need code. Ansible uses SSH or NETCONF to make changes and extract information. Ansible uses a push model, using several text files:
- Playbooks: files with actions and logic about what ansible should do
- Inventory: device hostnames along with information about each device, such as device roles, so ansible can perform functions for subsets of the inventory
- Templates: a device configuration with variables
- Variables: a list of YAML variables that ansible will substitute into templates

#### Puppet

Puppet typically uses an agent-based architecture for network device support. Some network devices enable Puppet support though an on-device agent. However, not every Cisco OS supports Puppet agents and Puppet solves that problem using a proxy agent running on some external host. The external agent then uses SSH to communicate with the network device. Puppet uses a pull model to get a configuration to appear in the device. 

###### Puppet pull model 

Puppet uses several important text files with different components:
* Manifest: a human-readable text file that defines the desired configuration state of a device 
* Resource, class and module: components of the manifest, with the largest component being comprised of smaller classes, which are in turn comprised of resources 
* Template: a file used to create a manifest, with variable names that will be substituted 

#### Chef

Chef, like Puppet, uses an agent based architecture. Chef uses several important text files:
- Resource: a configuration object whose state is managed by Chef 
- Recipe: the chef logic applied to resources to determine when, how and whether to act against the resources
- Cookbook: A set of recipes about the same kinds of work, grouped together for easier management and sharing 
- Runlist: An ordered list of recipes that should be run against a given devices

Chef requires on device client code and many Cisco devices do not support Chef clients.
