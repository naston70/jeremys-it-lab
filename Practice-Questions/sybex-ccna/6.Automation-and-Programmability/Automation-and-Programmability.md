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
