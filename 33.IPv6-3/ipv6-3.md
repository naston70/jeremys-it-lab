## IPv6 - 3

#### The IPv6 Header

40 bytes in length

###### IPv6 Header - Version 
- Length 4 bits
- Indicates the version of IP that is used
- Fixed value of 6 (0b0110) to indicate IPv6

###### IPv6 Header - Traffic Class
* Length 8 bits
* Used for QoS to indicate high priority traffic
* For example, IP phone traffic will have a Traffic calls value which will give it priority over other traffic

###### IPv6 Header - Flow Label
- Length 20 bits
- Used to identify specific traffic flows (communications between a specific source and destination)

###### IPv6 Header - Payload Length
* Length 16 bits
* Indicates the length of the payload (the encapsulated Layer 4 segment) in bytes
* The length of the IPv6 header itself isn't included because its always 40 bytes

###### IPv6 Header - Next Header
- Length 8 bits
- Indicates they type of the 'next header' (header of the encapsulated segment) for example TCP or UDP
- Same function as the IPv4 headers 'Protocol' field

###### IPv6 Header - Hop Limit
* Length 8 bits
* The value in this field is decremented by 1 each router that forwards it. If it reaches 0, the packet is discarded
* Same function as the IPv4 headers 'TTL' field

###### IPv6 Header - Source / Destination
- Length 128 bits
- Contains the IPv6 addresses of the packets source and the packets intended destination


**Version = 4 bits,** **Traffic Class = 8 bits,** **Flow Label = 20 bits,** **Payload Length = 16 bits,** **Next Header = 8 bits,** **Hop Limit = 8 bits,** **Source / Destination = 128 bits**





- 