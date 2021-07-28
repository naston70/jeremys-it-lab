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