## 6.Automation and Programmability


1. Which is a reason to automate a process for the configuration of
several routers?
- A. To increase the possibility for misconfiguration 
- B. To create an outcome that can be reproduced
- C. To decrease problems from the new configuration 
- D. To allow you to do less work

A. B.

2. You need to configure a new static route on the existing 20 routers. Which is the best way to do this?
- A. Copy and paste scripts built in Notepad++ into each router.
- B. Copy and paste scripts built in Excel into each router.
- C. Create a Python script to configure each router.
- D. Work with a partner so that both of you can double-check each other’s work and cut the time in half.

A. C. 

3. Which is the number one motivating factor to use network automation?
- A. Reduce the number of changes to be made
- B. Reduce the complications that arise from changes 
- C. Reduce the human error factor
- D. Reduce the planning time for the changes

A. C. 

4. What is the term that is used to describe the framework responsible for assisting in network automation?
- A. NetOps 
- B. DevOps 
- C. SysOps 
- D. SecOps

A. B.

5. Which management methodology is commonly used by developers for network automation?
- A. Lean and Agile 
- B. Waterfall
- C. Kanban
- D. Scrum

A. A, the management methodology that is commonly used by developers for network automation is Lean and Agile. Agile focuses on an adaptive approach for simultaneous workflows.

6. After you release a network automation script to production, which step should be completed?
- A. Testing
- B. Building 
- C. Planning 
- D. Monitoring

A. D.

7. Which element of YAML defines a key-value pair? 
- A. Definition
- B. Mapping 
- C. Lists
- D. Keys

A. B

8. How can you identify that a file is a YAML file?
- A. The file begins with three dashes.
- B. The file begins with a hashbang preprocessor.
- C. The contents are contained between curly brackets. 
- D. The contents are contained between square brackets.

A. A. 

9. Which structured data format closely resembles HTML? 
- A. YAML
- B. JSON 
- C. CSV 
- D. XML

A. D. 

10. Which data format is structured by white space? 
- A. YAML
- B. JSON 
- C. XML 
- D. CSV

A. A. 

11. You are creating a network automation script to configure a network device. What should you research to identify what can be controlled with your script?
- A. User interface layout
- B. API reference
- C. Source code of the device 
- D. Data storage of the device

A. B.

12. You are developing a network automation script that retrieves information. Which interface can you implement that will act similar to an API?
- A. CLI 
- B. SNMP 
- C. Syslog 
- D. SSH

A. B. SNMP was originally created to allow the retrieval of information from network devices and can be programmatically controlled.

13. Which protocol was created as a replacement for SNMP? 
- A. NETCONF
- B. Syslog 
- C. REST 
- D. SSH

A. A. 

14. Which protocol uses the YANG data model? 
- A. NETCONF
- B. REST 
- C. SNMP 
- D. YAML

A. A. 

15. Which protocol uses an HTTPS transport to configure and retrieve details programmatically?
- A. NETCONF 
- B. RESTCONF 
- C. SNMP
- D. Syslog

A. B.

16. Which is a benefit of controller-based networking?
- A. Increased security
- B. Decreased problems 
- C. Increased throughput 
- D. Increased complexity

A. A, a benefit of controller-based networking is increased security. When ACLs and filters are applied, they are applied informally to all nodes that are controlled by the Controller.

17. Which statement is correct about controller-based networking?
- A. Controller-based networking is always in the form of hardware appliances.
- B. Controller-based networking has a logically centralized control plane.
- C. Controller-based networking has a logically centralized data plane.
- D. Controller-based networking uses ASICs to centrally switch frames.

A. B, controller-based networking has a logically centralized control plane to centrally control the data plane.

18. Which term is used with controller-based networking that combines multiple sites to act as one single network?
- A. SDN
- B. SD-WAN 
- C. SD-LAN 
- D. VPN

A. B, SD-WAN is the term commonly used to describe the combination of multiple sites to act as one single network. 

19. Which is a potential disadvantage with controller-based networking? 
- A. Scalability
- B. Security
- C. Maturity
- D. Centralized provisioning

A. C. 

20. Which elements can be controlled with an SDN controller for an SDN- enabled switch?
- A. CPU utilization
- B. Memory utilization
- C. QoS
- D. Forwarding of traffic

A. C, QoS can be directly controlled with an SDN controller. The SDN controller will push programming to the SDN enabled switch so that the switch can control the flow of traffic. 

21. Which statement is correct about SDN switches?
- A. All data is centrally switched at the SDN controller.
- B. All SDN switches are stateless with respect to configuration. 
- C. All SDN switches are stateful with respect to configuration. 
- D. All data flowing through the switch is stateless.

A. B, all SDN switches are stateless with respect to their configuration. The configuration is applied from the central controller and therefore any configuration contained on the switch does not matter.

22. Which technology allows for the central remote monitoring of network switches and routers?
- A. SNMP 
- B. Syslog 
- C. SDN 
- D. CDP

A. A.

23. What is the SNMP component that aggregates all SNMP messages and polled metrics?
- A. Trap
- B. SNMP agent 
- C. Syslog server 
- D. NMS

A. D, Network management station.

24. Which method for configuration is used with Cisco Prime Infrastructure?
- A. SNMP
- B. CAPWAP 
- C. LWAPP
- D. RESTCONF

A. A. SNMP with SSH

25. Which type of architecture is used with controller-based networks? 
- A. Three tier
- B. Spine/Leaf
- C. Collapsed core 
- D. SAN fabric 

A. B, the spine/leaf architecture model has been adopted in controller based networks. The leaf switch acts as the access and distribution, and the Spine acts as the core or backbone for the network. 

26. Which is a correct statement about Spine/Leaf architecture?
- A. The Leaf switches connect to other Leaf switches.
- B. There is only one Spine switch per network.
- C. Spine switches provide access to hosts.
- D. The Leaf switches never connect to other Leaf switches, only Spine switches.

A. D. 

27. What is the flow of traffic in a Spine/Leaf network? 
- A. Leaf to Spine to Leaf
- B. Leaf to Leaf to Spine
- C. Spine to Leaf to Spine
- D. Leaf to Leaf

A. A, traffic flow in a Spine/Leaf network flows from the host connected to the Leaf to the Spine, eventually to the destination Leaf and waiting host.

28. Which current Cisco SDN solution is data center focused?
- A. Cisco APIC-EM 
- B. OpenDaylight 
- C. Cisco SD-WAN
- D. Cisco ACI

A. D.  Cisco Application Centric Infrastructure

29. Your company has an application they need remote office/branch office employees to directly access. Which Cisco SDN solution should you implement?
- A. Cisco APIC-EM
- B. Cisco SD-WAN
- C. Cisco Prime Infrastructure 
- D. OpenDaylight

A. B, Cisco Software Defined - WAN is a solution that will allow remote office/branch office personnel to access cloud based applications directly. 

30. What is the name of the networking model that incorporates a distribution layer?
- A. Spine/Leaf 
- B. Campus 
- C. CLOS
- D. SDN

A. B, the campus networking model is a traditional networking model that is deployed as either a three-tire model with a core, distribution and access layer or a collapsed core model. 

31. Which statement is correct about the SDN controller?
- A. The SDN controller configures the management plane of network devices.
- B. The SDN controller monitors data plane traffic.
- C. The SDN controller replaces the control plane of the SDN.
- D. The SDN controller complements the control plane of the SDN device.

A. C, The SDN controller replaces the control plane on SDN devices. The SDN devices in the network do not contain a control plane locally and instead are controlled by the SDN controller.  

32. Which platform is Cisco’s SDN controller offering for enterprise connectivity?
- A. APIC-EM
- B. OpenSDN
- C. OpenStack
- D. OpenDaylight

A. A. 

33. Which network plane is used for Spanning Tree Protocol (STP)? 
- A. Data plane
- B. Control plane
- C. Management plane 
- D. Switch plane

A. B. the control plane refers to any mechanism that controls the data plane. STP is used to control the data plane by removing redundant links. The data plane is responsible for switching and routing data.

34. Which network plane is used by syslog for delivering messages from the router or switch?
- A. Data plane 
- B. Control plane
- C. Management plane
- D. Switch plane

A. C. any mechanism which helps in the management of a router or switch. (SSH, Telnet)

35. When a network packet is routed in a router, which network plane is facilitating the traffic?
- A. Data plane
- B. Control plane
- C. Management plane 
- D. Switch plane

A. A.

36. On which network plane would a routing protocol perform?
- A. Data plane
- B. Control plane
- C. Management plane 
- D. Routing plane

A. B. OSPF, EIGRP routing protocols operate on the control plane.

37. On which SDN plane does CDP function? 
- A. Data plane
- B. Control plane
- C. Network plane
- D. Management plane

A. D. CDP functions on the management plane of the SDN model, it helps with management of the routers and switches and does not directly impact the data plane. 

38. Which is used for communication directly to the SDN devices in the network?
- A. The northbound interface (NBI)
- B. The southbound interface (SBI)
- C. The core of the controller
- D. Applications hosted on the controller

A. B, the SBI (southbound interface) directly communicates with the SDN devices.

39. What is an application program interface (API)?
- A. An API is a program that allows for data transfer.
- B. An API is a programming language for network programmability.
- C. An API is a programming interface or standard allowing one program to communicate with another program.
- D. An API allows for programs to be virtualized.

A. C.

40. When an application communicates with an SDN controller, which mechanism does it use to communicate?
- A. The southbound interface (SBI)
- B. The core of the controller
- C. The northbound interface (NBI)
- D. Simple Network Management Protocol (SNMP)

A. C. The NBI is responsible for allowing communication between applications and the core of the controller. 

41. Which networking plane is responsible for routing of packets to specific destinations?
- A. Control plane
- B. Data plane
- C. Management plane 
- D. Routing plane

A. B. The data plane is responsible for the routing of packets to specific destinations. 

42. What is the maximum hop count of fabric switching? 
- A. 1 hop
- B. 3 hops 
- C. 4 hops 
- D. 5 hops

A. B. When a host transmits it will enter a Leaf switch, the Leaf swtich will then forward traffic to the spine switch. The spine switch will in turn forward traffic to the corresponding Leaf switch and to the destination. 

43. Which component of an SDN is where the MTU is set? 
- A. Overlay
- B. Tunnel 
- C. Leaf
- D. Underlay

A. D. The underlay is where the MTU is set. 

44. You are connecting to a router and configuring ACLs through the web interface. Which plane are you affecting?
- A. Management plane 
- B. Configuration plane 
- C. Data plane
- D. Control plane

A. D. ACLS affect the control plane. This is because you are controlling the flow of data with an ACL. You are accessing the router through the management plane and are controlling the data plane with the control plane.

45. Which WAN technology uses the overlay to connect remote offices? 
- A. DMVPN
- B. VXLAN 
- C. VLAN 
- D. ECMP

A. A. 

46. Which protocol allows for the tunneling of layer 2 traffic over a layer 3 network?
- A. ECMP 
- B. DMVPN 
- C. VXLAN 
- D. EIGRP

A. C, the Virtual Extensible LAN (VXLAN) is used to create layer 2 tunnels over a layer 3 network. The VXLAN protocol functions by encapsulating layer 2 traffic inside of a layer 3 packet. 

47. Which is a protocol used on the management plane? 
- A. SNMP
- B. CDP 
- C. ICMP 
- D. VTP

A. A.

48. Which next-hop packet forwarding protocol is used with SDN switching networks?
- A. ECMP 
- B. OSPF 
- C. MPLS 
- D. CLOS

A. A. 

49. Which product is a replacement for APIC-EM?
- A. OpenFlow
- B. Cisco Prime Infrastructure 
- C. Cisco DNA Center
- D. Cisco SD-WAN

A. C.

50. Which protocol is not used by the DNA discovery process for reading the inventory of a network device?
- A. SSH
- B. HTTPS
- C. NETCONF
- D. OpenFlow

A. D.

51. Where would you see the overall health of the network inside of the Cisco DNA Center?
- A. Design
- B. Policy
- C. Assurance 
- D. Platform

A. C

52. Which Cisco DNA Center feature allows you to template and apply standard configuration such as DNS servers, NTP servers, and AAA servers?
- A. IP-based access control
- B. Plug and Play
- C. Group-based access control 
- D. Assurance

A. B, PnP is a feature inside of the Cisco DNA Center that allows you to onboard network devices and pply standard configuration such as DNS servers, NTP servers and AAA servers.  

53. You want to see how everything is connected at a particular site. Which section contains a tool to obtain this information inside of the Cisco DNA Center?
- A. Provision 
- B. Assurance
- C. Platform
- D. Policy

A. A. Under the provision section, you can click on the hierarchy item that contains the site; then you will select the topology icon in the result pane. 

54. You need to add an OSPF area to a number of routers. What is the easiest method to achieve this with the Cisco DNA Center?
- A. IP-based access control 
- B. Python
- C. DNA Command Runner 
- D. Inventory

A. C.

55. In which section inside of the Cisco DNA Center can you view and manage inventory of routers, switches, APs, and WLCs?
- A. Provision 
- B. Policy
- C. Design
- D. Assurance

A. A, the provision section allows you to view and edit the discovered inventory of network devices. 

56. You are developing a Python script that will interact with the Cisco DNA Center. Which section will detail the API that you will need to use?
- A. Design
- B. Policy
- C. Provision
- D. Platform

A. D. 

57. What is the Cisco DNA Center feature that automates the fabric of the underlay and overlay of the network?
- A. Easy-QOS 
- B. SD-Access 
- C. System 360 
- D. Cisco ISE

A. B, the Cisco feature Software Defined Access is an automated Plug and Play solution that automates the underlay and overlay of the fabric. 

58. Which feature does Cisco Prime Infrastructure provide that Cisco DNA Center cannot provide?
- A. Client coverage heat maps 
- B. Client triangulation support 
- C. Device configuration backup 
- D. Application health

A. C. Cisco DNA Center cannot provide device configuration backups; that function still requires Cisco Prime Infrastructure.

59. Which method(s) of connectivity must be configured for network discovery inside of the Cisco DNA Center?
- A. SSH
- B. SNMP
- C. Logging
- D. Both A and B

A. D.

60. Which protocol is normally used with REST APIs? 
- A. SNMP
- B. HTTP 
- C. SNTP 
- D. SOAP

A. B.

61. You are writing a script to pull information from the Cisco DNA Center via the REST-based API. How do you authenticate so that you can communicate with the Cisco DNA Center API?
- A. Pass the username and password in every request.
- B. Send a POST to the API for an authentication token.
- C. Send a GET to the API for an auth token.
- D. Create a public private key pair for the Cisco DNA Center appliance.

A. B.

62. What is the CRUD framework used for? 
- A. Memory cleanup
- B. Replacement for REST-based APIs
- C. Data encoding
- D. Data actions

A. D.

63. Which type of authentication is used for REST-based token requests to the Cisco DNA Center?
- A. Basic
- B. AD integrated 
- C. SSL
- D. Pass-through

A. A, basic auth is used for token requests with the Cisco DNA Center. 

64. After you obtain an authentication token, how do you apply it to subsequent actions?
- A. Add it as a variable named X-Auth-Token in the script.
- B. Place it in the header of the request as an X-Auth-Token element.
- C. Pass the token in the URI of subsequent requests.
- D. Perform a POST for the authentication token within 10 seconds of the subsequent request.

A. B, after the initial POST to obtain the authentication token, it should 

65. Which encoding method is used to transmit the username and password to obtain the X-Auth-Token from the Cisco DNA Center?
- A. SSL
- B. AAA 
- C. Base64 
- D. Basic

A. C, when you process the POST to obtain the X-Auth-Token from the Cisco DNA Center, you will pass the username and password encoded in Base64.

66. You are creating a script to directly configure a Cisco switch using the YANG data model. Which network API will you use to perform this task?
- A. OpenFlow
- B. RESTCONF
- C. SNMP
- D. REST-based API

A. B.

67. Which is a RESTCONF content type that is used with a RESTCONF request?
- A. application/yang-data+json 
- B. application/json
- C. data/json
- D. data/yaml

A. A.

68. You’ve initiated a REST-based API call to an SDN controller and received a 500 status code. What will most likely fix the problem?
- A. Format your response correctly. 
- B. Authenticate to the device first. 
- C. Nothing; this code means OK. 
- D. Restart the REST-based service.

A. D, 500 means that there is an internal server error. 200 is ok.

69. On which interface of the Cisco DNA Center would you most likely use a RESTCONF request?
- A. Northbound interface 
- B. Eastbound interface 
- C. Westbound interface 
- D. Southbound interface

A. D, RESTCONF requests are used outbound to network devices on the southbound interface of Cisco DNA Center. REST-based

70. How is a status code passed to the client after a REST-based request has been processed?
- A. HTTP header
- B. HTTP body
- C. Script variable 
- D. Script data object

A. A, the status code is passed back to the client via the HTTP header.

71. You have received a return status code of 201 from an SDN controller after executing an API request via REST. Which CRUD action have you executed, judging by the status code?
- A. POST
- B. GET
- C. PATCH
- D. DELETE

A. A. 

72. Which character signifies the starting point for a series of request query parameters in a URI string?
- A. Backslash
- B. Forward slash 
- C. Question mark 
- D. Ampersand

A. C.

73. Which HTTP action verb is used to insert or create a data item? 
- A. GET
- B. UPDATE 
- C. POST
- D. PUT

A. C 

74. You just sent a request to the SDN controller, and after a little while, the result code came back as a 504 status code. What most likely happened?
- A. The command is missing parameters. 
- B. The command has timed out.
- C. The command is restricted.
- D. The service is down.

A. B.

75. Which function does Ansible, Chef, and Puppet perform in the network?
- A. Network management station 
- B. Configuration management 
- C. Software-defined networking 
- D. Centralized logging

A. B. 

76. Which configuration management tool uses YAML to store configuration?
- A. Ansible
- B. Cisco DNA Center 
- C. Chef
- D. Puppet

A. A.

77. Which component in an Ansible setup defines the connection information so that Ansible can perform configuration management?
- A. Playbook  
- B. Settings 
- C. Inventory 
- D. Modules

A. C

78. Which configuration management tool does not require an agent to apply changes to a Linux-based server?
- A. Ansible
- B. Puppet
- C. Chef
- D. Cisco DNA Center

A. A, Ansible does not require an agent to apply changes to a Linux-based server or other network device. It uses TCP port 22 to apply the configuration. Puppet and Chef both require agents to be installed on the managed hosts.

79. Which Puppet component contains the configuration for the managed hosts?
- A. Manifest 
- B. Agent 
- C. Class
- D. Module

A. A.

80. Which Chef component contains the set of instructions to configure a node?
- A. Cookbook 
- B. Crock Pot
- C. Recipe
- D. Chef Node

A. C, the recipe component of Chef contains the set of instruction that are carried out to configure a server, The recipes are collected into the cookbook component so that the tasks can be organized and applied to hosts. 

81. Which Chef component collects system state information and reports back to the Chef Server component?
- A. Chef-Client
- B. Chef Workstation 
- C. Ohai
- D. Knife

A. C, the ohai component is the second of two parts installed on the CHef Node. The first part is the CHef-Client component. Ohai is responsible for monitoring system state information and reporting back to the Chef-Server component. 

82. Which variable is checked to determine the location of the Ansible settings file?
- A. ANSIBLE_SETTINGS 
- B. ANSIBLE_CONFIG
- C. ansible_connection 
- D. /etc/ansible/hosts

A. B.

83. Which command will give detailed information on modules in Ansible?
- A. man
- B. cat
- C. ad-hoc
- D. ansible-doc

A. D.

84. Which Ansible tool will allow you to try commands against a host without making a Playbook?
- A. Knife interface
- B. ansible_playbook command 
- C. Ad-hoc interface
- D. Ansible Tower

A. C. 

85. What are global variables that contain information specific to Puppet called?
- A. Resource 
- B. Class
- C. Module 
- D. Facts

A. D

86. Once you have completed a Cookbook for Chef, where do you upload the Cookbook so it is accessible on the Chef Server?
- A. Bookshelf
- B. Chef Workstation 
- C. Chef Node
- D. Chef-Client

A. A.

87. Which tool will allow for central management and RBAC and is supported by Red Hat?
- A. Ansible Tower 
- B. Chef
- C. Puppet
- D. Ansible

A. A. 

88. Which configuration management utility allows for easy configuration of Cisco network devices?
- A. Ansible 
- B. Puppet 
- C. Chef
- D. Python

A. A, Ansible has many modules dedicated to Cisco IOS

89. What function does Knife serve in the Chef configuration management utility?
- A. Storage of the Bookshelf
- B. Storage of the configuration of Chef
- C. CLI utility for the management of Chef
- D. Client-side agent

A. C.

90. Which is a correct statement about configuration management?
- A. IaaS helps maintain configuration over the life cycle of the host. 
- B. Configuration management prevents drift with NTP.
- C. IaC solutions prevent drift with Idempotence.
- D. Configuration management software requires per-host licensing.

A. C. 

91. Which configuration management utility is the easiest to set up? 
- A. Chef 
- B. Puppet
- C. Ansible
- D. Cisco DNA Center

A. C.

92. Which format must a custom Ansible module be written in? 
- A. YAML
- B. CSV 
- C. JSON 
- D. XML

A. C.

93. What is at the beginning of every JSON file that helps you identify the format?
- A. Three dashes
- B. A square bracket 
- C. A double quote 
- D. A curly bracket

A. D.

94. You just opened a JSON file, and the key you are looking for has a square bracket. What can be concluded?
- A. The value that follows the square bracket is the value you are looking for.
- B. There are several key-value pairs for the key you need.
- C. The value is after the matching square bracket.
- D. The value is unknown.

A. B.

95. In the following exhibit, what is wrong with this JSON file?
   {
       "interface": "Fa0/1",
       "bandwidth": "100mb",
       "status": "up",
       "address": {
"ipaddress": "192.168.1.5",
"subnetmask": "255.255.255.0",
"default gateway": "192.168.1.1",
}

- A. The interface of Fa0/1 is capitalized.
- B. The address should have a square bracket
- C. There is a missing curly bracket.
- D. Nothing is wrong.

A. C.

96. Which is an advantage in using JSON over a CSV file? 
- A. Values can be used that contain spaces.
- B. There are multiple values for a particular key.
- C. The files can be read line by line for every value. 
- D. Hierarchical structure allows for programmability.

A. D.


97. When you request information from the Cisco DNA Center via a REST-based API, what format is the response in?
- A. JSON 
- B. XML 
- C. CSV 
- D. YAML

A. A. 
