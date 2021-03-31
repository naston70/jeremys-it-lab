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









