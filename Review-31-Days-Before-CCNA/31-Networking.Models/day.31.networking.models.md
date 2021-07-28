## Day 31

#### CCNA EXAM TOPICS:

* Explain the role and function of network components
* Describe characteristics f network topology architectures
* Compare physical interface and cabling types
* Identify interface and cable issues
* Compare TCP to UDP

#### Key Points:

Both the OSI and TCP/IP networking models are important for understanding networks.

###### The OSI and TCP/IP models

To understand how communication occurs across the network, you can use layered models as a framework for representing and explaining networking concepts and technologies. OSI and TCP/IP support interoperability between competing vendor product lines.

###### OSI Layers

- Application = 7
    * Refers to interfaces between network and Application software. Also includes authentication

- Presentation = 6
    * Defines the format and organization of data. Includes encryption

- Session = 5
    * Establishes and maintains end-to-end bidirectional flows between end points.

- Transport = 4
    * Connection establishment and termination, flow control, error recovery and segmentation of large data blocks into smaller parts for transmission

- Network = 3
    * Refers to logical addressing, routing and path determination 

- Data Link = 2
    * Formats data into frames appropriate for transmission onto some physical medium. Defines rules for when that medium can be used and defines the means by which to recognize transmission errors

- Physical = 1
    * Defines the electrical, optical, cabling, connectors and procedural details required for transmitting bits, represented as some form of energy passing over a physical medium 

###### TCP/IP Layers and Protocols

This model defines four categories of functions that must occur for communications to succeed. 


| LAYER          | FUNCTION                      | EG              |
|----------------|-------------------------------|-----------------|
| APPLICATION    | Represent data to user        | DNS, SMTP, IMAP |
| TRANSPORT      | Supports device communication | TCP, UDP        |
| INTERNET       | Determines best path          | IP, ARP, ICMP   |
| NETWORK ACCESS | Controls the hardware         |                 |


###### Protocol Data Units and Encapsulation

As application data is passed down the protocol stack on its way to be transmitted across the network media, various protocols add information to it at each level. This is known as the encapsulation process.

Layers 7,6 and 5 the PDU = Data
Layer 4 the PDU          = Segment
Layer 3 the PDU          = Packet
Layer 2 the PDU          = Frame
Layer 1 the PDU          = Bits 

###### TCP/IP APPLICATION LAYER

Provides an interface between software and the network itself. 
1. An HTTP request is sent 
2. An HTTP response is sent from the web server with a code in the header 

The HTTP request and response are encapsulated in headers. The contents of the headers allows the application layers on each end device to communicate. Regardless of the application layer protocol, all headers use the same general process for communication between application layers on the end devices

###### TCP/IP TRANSPORT LAYER

Provides a mechanism to guarantee delivery of data across the network. TCP supports error recovery to the application layer through the use of basic acknowledgment logic. 

1. web client sends an HTTP request down to the Transport Layer 

2. TCP encapsulates the request with a TCP header and includes the destination port number for HTTP

3. Lower layers process and send the request to the web server 

4. The web server receives the request and sends a TCP acknowledgment back to the web client

5. The web server sends the HTTP response down to the Transport Layer

6. TCP encapsulates the HTTP data with a TCP header

7. Lower layers process and send the response to the web client 

8. The requesting web client sends and acknowledgment back to the web server

If any data is lost at any point during this process, TCP must recover the data.

The Transport Layer also provides UDP, a connectionless, unreliable protocol for sending data that does not require or need data recovery. 

###### TCP header

TCP provides error recovery but to do so it consumes more bandwidth and uses more processing cycles than UDP. TCP and UDP rely on IP for end-to-end delivery. TCP is concerned with providing services to the applications of the sending and receiving services.

TCP HEADER:

Source Port (16)    |   Destination Port (16)
Sequence Number (32)
Acknowledgment (32)
Header LEN (4) | Reserved Code Bits (12) | Window (16)
Checksum (16)  | Urgent
Options (0 or 32)
Data 

###### Port Numbers

The first 2 fields of the TCP header, the source and destination ports, are also part of the UDP header. Port numbers provide TCP with a way to multiplex multiple applications on the same computer. Web browsers now support multiple tabs or pages. Each time you open a new tab another and make another request, TCP assigns a different source port number

###### Well known Port numbers 

| Port Num | Protocol | Application |
|----------|----------|-------------|
| 20       | TCP      | FTP data    |
| 21       | TCP      | FTP control |
| 22       | TCP      | ssh         |
| 23       | TCP      | Telnet      |
| 25       | TCP      | SMTP        |
| 53       | UDP, TCP | DNS         |
| 67,68    | UDP      | DHCP        |
| 69       | UDP      | TFTP        |
| 80       | TCP      | HTTP        |
| 161      | UDP      | SNMP        |
| 443      | TCP      | HTTPS       |

###### Error recovery

TCP provides error recovery, also known as reliability, during the data transfer sessions between two end devices that have an established connection. The SEQ and ACK fields in the TCP header tracker every byte of data transfer and ensure that missing bytes are retransmitted. 

###### Flow Controls

TCP handles flow control through a process called windowing. The two end devices negotiate the window size when establishing the connection; then they dynamically renegotiate window size during the life of the connection, increasing its size until it reaches the max window size of 65535. Tis size is specified in the TCP header. 

###### UDP

TCP establishes and terminates connections between endpoints where UDP does not. Therefore UDP is called a connectionless protocol. It rovides no reliability, no windowing and no reordering of the data. However UDP does provides data transfer and multiplexing using port numbers and dooes so with much less overhead.

#### The TCP/IP Internet Layer

The Internet layer of the TCP/IP model and its Internet Protocol (IP) define addresses so that each host computer can have a different IP address. In addition, the Internet layer defines the process of routing so that routers can determine the best path for sending packets to the destination. Continuing with the web page example, IP addresses the data as it passes from the transport layer to the Internet layer:

Step 1. The web client sends an HTTP request

Step 2. TCP encapsulates the HTTP request.

Step 3. IP encapsulates the transport segment into a packet, adding source and destination addresses.

Step 4. Lower layers process and send the request to the web server.

Step 5. The web server receives HTTP requests and sends a TCP acknowledgment back to the requesting web client.

Step 6. The web server sends the HTTP response down to the transport layer.

Step 7. TCP encapsulates the HTTP data.

Step 8. IP encapsulates the transport segment into a packet, adding source and destination addresses.

Step 9. Lower layers process and send the response to the requesting web client.

Step 10. The requesting web client sends an acknowledgment back to the web server.

###### The TCP/IP Network Access Layer

IP depends on the network access layer to deliver IP packets across a physical network. Therefore, the network access layer defines the protocols and hardware required to deliver data across some physical network by specifying exactly how to connect a networked device to the physical media over which data can be transmitted. 

The network access layer includes many protocols to deal with different types of media that data can cross on its way fro source device to destination device. For example, data might need to travel first on an Ethernet link and then cross an PPP link, then a frame relay link, then a MPLS link and finally an Ethernet link to reach its destination. At each transition from one media type to another, the network access layer provides protocols, cabling standards, headers and trailer to send data across the physical network.

Many times, a local link address is needed to transfer data from one hop to the next. For example, MAC addresses are used between the sending device and its local gateway router. At the gateway router, the Ethernet header might be replaced with an MPLS label. The label serves the same purpose as the MAC addresses in Ethernet: to get the data across the link from one hop to the next so that data can continue its journey to the destination.

With the network layer, the web page example can be finalized:

Step 1. The web client sends an HTTP request.

Step 2. TCP encapsulates the HTTP request.

Step 3. IP encapsulates the transport segment into a packet, adding source and destination addresses.

Step 4. The network access layer encapsulates the packet in a frame, addressing it for the local link.

Step 5. The network access layer sends the frame as bits on the media.

Step 6. Intermediary devices process the bits at the network access and Internet layers and then forward the data toward the destination.

Step 7. The web server receives the bits on the physical interface and sends them up through the network access and Internet layers.

Step 8. The web server sends a TCP acknowledgment back to the requesting web client.

Step 9. The web server sends the HTTP response down to the transport layer.

Step 10. TCP encapsulates the “HTTP data.

Step 11. IP encapsulates the transport segment into a packet, adding source and destination addresses.

Step 12. The network access layer encapsulates the packet in a frame, addressing it for the local link.

Step 13. The network access layer sends the frame as bits on the media.

Step 14. Lower layers process and send the response to the requesting web client.

Step 15. The response travels back to the source over multiple data links.

Step 16. The requesting web client receives the response on the physical interface and sends the data up through the network access and Internet layers.

Step 17. The requesting web client sends a TCP acknowledgment back to the web server.

Step 18. The web page is displayed in the requesting device’s browser.

###### Data Encapsulation Summary 

Each Layer of the TCP/IP model adds its own header information. As the data travels down through the layers it is encapsulated with a new header. At the network access layer, a trailer is also added. 

Step 1.
Create and encapsulate the application data with any required application layer headers. 

Step 2.
Encapsulate the data supplied by the application layer header. 

Step 3.
Encapsulate the data supplied by the transport layer inside an Internet layer (IP) header - IP is the only protocol available in the TCP/IP network model at the Internet layer

Step 4. 
Encapsulate the data supplied by the Internet layer inside a network access layer trailer and header. This is the only layer that uses both.

Step 5.
Transmit the bits


1. [data]        - Application
2. [tcp|data]    - Transport
3. [IP|tcp|data] - Internet
4. [LH|IP|TCP|DATA|LT] - Network Access

###### DEVICES 

In wired networks, switches are almost exclusively used to connect end devices to a single LAN. Hubs are now legacy devices. 
Differences between Hubs and Switches:

- Hubs were typically chosen as intermediary devices within very small LANs, in which bandwidth usage was not an issue or cost limitations were a factor. 
- Switches replaced Hubs as LAN intermediary devices because a switch can segment collision domains and provide enhanced security.

###### SWITCHES

When choosing a switch, these are the main factors to consider. 

* Cost: cost is determined by the number and type of ports, network management capabilities, embedded security technologies and optional switching technologies.

* Interface characteristics: the number of ports must be sufficient both for now and for future expansion. Other characteristics include uplink speeds, a mixture of UTP and fiber and modularity

* Hierarchial network layer: switches at the access layer have different requirements than switches at the distribution or core layers.

###### Access Layer Switches

Access layer switches facilitate the connection of end devices to the network. Features of access layer switches include the following:

- Port security
- VLANs
- Fast Ethernet/Gigabit Ethernet
- Power over Ethernet (PoE)
- Link Aggregation 
- Quality of Service 

###### Distribution Layer Switches 

Distribution Layer Switches receive the data from the access layer switches and forward it to the core layer switches.

* Layer 3 support 
* High forwarding rate 
* Gigabit Ethernet/10 Gigabit
* Redundant components 
* Security policies/acls
* Link Aggregation
* QoS

###### Core Layer Switches 

- Core layer switches make up the backbone and are responsible for handling the majority of data on a switched LAN. Features of core switches include the following:

- Layer 3 support 
- Very high forwarding rate 
- Gigabit Ethernet/10 Gigabit Ethernet 
- Redundant components
- Link Aggregation
- QoS

###### Routers

Routers are the primary devices used to interconnect networks- LANs, WANs and WLANs. When choosing a router the following are the main factors to consider:

* Expandability: provide flexibility to add new modules as needs change

* Media: determines the type of interfaces the router needs to support for the various network connections 

* OS system features: determines the version of IOS loaded on the router. Different IOS version support different feature sets.

* Console ports: two console ports for the initial configuration, using a regular RJ-45 and a USB Type-B connector 

* AUX port: An RJ-45 port for remote management access 

* LAN interfaces

* Ethernet WAN

* NIM slots 

#### Specialty Devices

###### Firewalls

A firewall is a networking device, either hardware or software based, that controls access to the organizations network. This controlled access is designed to protect data and resources from outside threats. 
Organizations implement software firewalls through a NOS such as Linux/Unix or Windows etc. The firewall is configured on the server to allow or block certain types of traffic. Hardware firewalls are often dedicated network devices than can be implemented with little configuration.

A stateful firewall allows traffic to originate from an inside, trusted network and go out to an untrusted network such as the Internet. The firewall allows return traffic that comes back from the untrusted network to the trusted network. However, the firewall blocks traffic that originates from an untrusted network. 

#### IDS and IPS

Both intrusion detection systems (IDS) and intrusion prevention systems (IPS) can recognize network attacks; they differ primarily in their network placement. An IDS device receives a copy of traffic to be analyzed. An IPS device is placed inline with the traffic




