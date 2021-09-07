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

