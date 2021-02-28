# OSI Model & TCP/IP Suite

Networking models categorize and provide a structure for networking protocols.

Without standardization devices wouldn't be able to communicate. OSI and TCP/IP attempt to solve this

**Open Systems Interconnection model**
	- A conceptual model that categorizes and standardizes the different functions in a network
	- Functions divided into 7 'layers'
	- These layers work together to make the network work.

Application - Presentation - Session - Transport - Network - Data Link - Physical

### 7. Application Layer

Layer closet to the end user
Interacts with software apps
HTTP and HTTPS are Layer 7 protocols

***Functions of Layer 7:***
Synchronizing communication
Identifying commuNication partners

### 6. Presentation Layer

Data in the application layer is in application format
It needs to be translated to a different format to be sent over the network
The ***Presentation*** Layers job is to translate between application and network formats

***Functions of Layer 6:***
Encryption of data as it is sent
Decryption of data as it is received
Translates between different Layer formats

### 5. Session Layer

Controls sessions between communicating hosts
Establishes and manages sessions between the local app and the remote app (yt, live streams, etc)

The top 3 Layers hand their data over to the next 4 Layers

### 4. Transport Layer
Segments and reassembles data for communications between end hosts
Breaks large pieces of data into smaller segments which can be more easily sent over the network and less likely to cause transmission errors
Provides host-to-host, end-to-end communication


Data plus the L4 header is called a segment

### 3. Network Layer
Provides connectivity between end hosts on different networks
Provides logical adressing. (IP addresses)
Provides path selection between source and destination
Routers operate at Layer 3

OSI Model encapsulation, data from first 3 layers, layer 4 adds a header (segment). Next the Network Layer adds a L3 header (including src and dest IP). This data, with L4 and L3 headers is called a packet. This goes further down the Layers to the Data Link Layer. With a L2 trailer and L2 header added

### 2. Data Link Layer
Provides node to node connectivity
Defines how data is formatted for transmission over a physical medium
Detects and possibly corrects Physical Layer errors
Uses Layer 3 addressing 
Switches operate at Layer 2

This combination of L2 trailer, data, L4 header, L3 header, L2 header is known as a ***frame***

### 1. Physical Layer
Defines physical characteristics of the medium used to transfer data between devices
Digital bits are converted into electrical or radio signals

Once fully encapsulated and data is sent, the process of de-encapsulation begins

## PDU's Protocol Data Units:

-- Data --> Segment --> Packet --> Frame

## TCP/IP Suite

Conceptual model and set of communications used in the Internet and other networks
Known as TCP/IP because those are two of the foundAtional protocols in the suite
Less layers than OSI
In use in modern networks

4 -> Application - 3 -> Transport - 2 -> Internet 1 -> Link


