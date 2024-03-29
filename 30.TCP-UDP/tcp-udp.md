## TCP & UDP - exam topic 1.5 Compare TCP to UDP

#### Functions of Layer 4 (Transport Layer)

- Provides transparent transfer of data between end hosts
- Layer 4 encapsulates the data with a Layer 4 header and then uses the services of the below layers 3, 2 and 1 to deliver the data unchanged to the destination host. The above layers are unaware of this process.
- Provides or (doesn't provide) various services to applications:
    - reliable data transfer
    - error recovery
    - data sequencing
    - flow control

- Provides Layer 4 addressing (port numbers)
    - Identify the Application Layer Protocol
    - Provides session multiplexing 

## TCP - Transmission Control Protocol

- TCP is connection oriented:
    * before actually sending data to the destination host, the two hosts communicate to establish a connection. Once the connection is established, the data exchange begins.

- TCP provides reliable communication
    * the destination host must acknowledge that it received each TCP segment
    * if a segment isn't acknowledged, it is sent again

- TCP provides sequencing
    * Sequence numbers in the TCP header allow destination hosts to put segments in the correct order even if they arrive out of order

- TCP provides flow control
    * the destination host can tell the source host to increase/ decrease the rate that data is sent

- Establishes a connection using the three-way handshake:
    * SYN flag -->
    * <-- SYN flag, ACK flag
    * ACK flag -->

- Terminating Connections, four-way handshake:
    * FIN flag -->
    * <-- ACK flag
    * <-- ACK flag
    * ACK flag -->

## UDP - User Datagram Protocol

- UDP is not connection oriented
    - The sending host does not establish a connection with the destination host before sending data. The data is simply sent

- UDP does not provide reliable communication
    - When UDP is used, acknowledgments are not sent for received segments. If a segment is lost, UDP has no mechanism to re-transmit it. 

- UDP does not provide sequencing
    - There is no sequence number in the UDP header. If segments arrive out of order, UDP has no mechanism to put them back in order


## Comparing TCP & UDP

* TCP provides more features than UDP but with additional **overhead**
* For applications that require reliable communications, TCP is preferred
* For applications like voice and video, UDP is preferred
* Some applications use UDP but provide reliability with the application
* Some applications use both TCP and UDP, depending on the need


| TCP                 | UDP             |
|---------------------|-----------------|
| Connection Oriented | Connectionless  |
| Reliable            | Unreliable      |
| Sequencing          | No sequencing   |
| Flow Control        | No Flow Control |


## PORT NUMBERS

| TCP               | UDP               | TCP and UDP |
|-------------------|-------------------|-------------|
| FTP         - 20  | DHCP Server - 67  | DNS         |
| FTP Control - 21  | DHCP Client - 68  |             |
| SSH         - 22  | TFTP        - 69  |             |
| Telnet      - 23  | SNMP Agent  - 161 |             |
| SMTP        - 25  | SNMP Manager- 162 |             |
| HTTP        - 80  | Syslog      - 514 |             |
| POP3       - 110  |                   |             |
| HTTPS      - 443  |                   |             |
