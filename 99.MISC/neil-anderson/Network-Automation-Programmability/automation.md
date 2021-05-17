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
- 
