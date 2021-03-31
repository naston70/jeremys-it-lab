## TCP / IP
(exam topic - explain difference between TCP and UDP and role of DHCP and DNS in networks)
#### TCP/IP Layer 4 Protocols: TCP & UDP

The OSI transport layer (Layer 4) defines several function, the most important of which are **error recovery** and **flow control.** TCP/IP transport layer protocols also implement these same type of features.

The main difference between TCP and UDP is that TCP offers a wide variety of services to applications but UDP does not. 
This does not mean UDP is worse, UDP needs fewer bytes in its header compared to TCP so less overhead in the network. 

**TCP/IP Transport Layer Features:**

- **Multiplexing using ports**:
    * Allows receiving host to choose the correct app for which data is destined based on the port number
- **Error recovery**:
    * Process of numbering and acknowledging data with Sequence and Acknowledgment header fields
- **Flow control using windowing**:
    * Process that uses window sizes to protect buffer space and routing devices from being overloaded with traffic
- **Connection establishment and termination**:
    * Process used to initialize port numbers and Sequence and Acknowledgment fields
- **Ordered data transfer and data segmentation**
    * Continuous streams of bytes from an upper-layer process that is segmented for transmission and delivered to upper-layer processes at the receiving device, with the bytes in the same order


#### Transmission Control Protocol

Each TCP/IP application chooses to use either TCP or UDP depending on its requirements. ie TCP can provide error recovery but consumes more bandwidth or UDP, does not use error recovery but uses less bandwidth and less processing. 

TCP relies on IP for end-to-end delivery of the data, including routing - TCP only performs only part of the function necessary to deliver data between applications. Its role is more directed to performing services for the applications that sit at endpoints. 

#### Multiplexing using TCP Port Numbers
(Both TCP and UDP use multiplexing)

Multiplexing relies on a concept called a *socket*. A socket contains three things:
- An IP address
- A transport protocol
- A port number
- example socket = 10.1.1.2, TCP, 80

Ports have three types:
* Well Known (System) Ports : 0 - 1023
* User (Registered) Ports   : 1024 - 49151
* Ephemeral Ports           : 49152 - 65535

A socket on a computer should be unique, meaning a connection between two sockets should identify a unique connection. This uniqueness means that you can use multiple applications at the same time, talking to applications running on the same or different computers. Multiplexing based on sockets ensures data is delivered to the correct applications.

#### Popular TCP/IP Applications

WWW - exists through web browsers accessing content on web servers

DNS - allows users to use names to refer to computers, with DNS being used to find the corresponding IP addresses

SNMP - application layer protocol used specifically for network device management

FTP/TFTP - moves files to and from devices


| Port Number | Protocol | Application |
|-------------|----------|-------------|
| 20          | tcp      | ftp data    |
| 21          | tcp      | ftp control |
| 22          | tcp      | ssh         |
| 23          | tcp      | telnet      |
| 25          | tcp      | smtp        |
| 53          | tcp/udp  | dns         |
| 67          | udp      | dhcp server |
| 68          | udp      | dhcp client |
| 80          | tcp      | http        |
| 110         | tcp      | pop3        |
| 161         | udp      | snmp        |
| 443         | tcp      | ssl         |
| 514         | udp      | syslog      |


#### Establishing Connection and Termination

A TCP connection must occur before any TCP feature can begin.
Known as the three-way-handshake SYN-SYN/ACK-ACK

TCP establishes and terminates connections between endpoints, whereas UDP does not.

TCP is a **connection-oriented protocol** in that it requires an exchange of messages before data transfer begins, or that has a required pre-established correlation between two endpoints

UDP is a **connectionless protocol** that does not require an exchange of messages and does not require a pre-established correlation between two endpoints

#### Error Recovery and Reliability

TCP provides error recovery by numbering the data bytes using the Sequence and Acknowledgment fields in the TCP header. TCP achieves reliability in both directions, using the Sequence number field of one direction combined with the Acknowledgment field in the opposite direction.

#### Flow Control using Windowing

TCP implements flow control by using a window concept that is applied to the amount of data that can be outstanding and awaiting acknowledgment at any one point in time. The window concept lets the receiving host tell the sender how much data it can receive right now, giving the receiving host a way to make the sending host slow down or speed up. The receiver can slide the window size up and down to change how much data the sending host can send

#### User Datagram Protocol

UDP provides a service for applications to exchange messages. Unlike TCP, UDP is connectionless and provides no reliability, no windowing, no reordering of the received data and no segmentation of large chunks of data.

UDP data transfer differs from TCP data transfer in that no reordering or recovery is accomplished. Apps that use UDP are tolerant of the lost data or have some mechanism to recover lost data. 

UDP header has only 8 bytes in comparison to 20 byte TCP header









