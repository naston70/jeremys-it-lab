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
