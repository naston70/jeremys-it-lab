## Ethernet Frame (wikipedia)

An Ethernet frame is a data link protocol data unit and uses the underlaying Ethernet physical layer transport mechanisms. A data unit on an Ethernet link transports an Ethernet frame as its payload.

* Minimum size of an Ethernet Frame = 64 bytes
* An Ethernet frame is preceded by a preamble and SFD - (Start Frame Delimiter)
* Each Ethernet frame starts with an Ethernet header, which contains destination and source MAC addresses as its first two fields. 
* The middle section of the frame is payload data including any headers for other protocols carried in the frame
* The frame ends with a Frame Check Sequence - FCS


Layer 	Preamble    SFD    MAC-d    Mac-s    802.1q (opt)    Ethertype    Payload    FCS    interpacket gap        

Layer2  7 octets	1	   6        6        4               2			  46-1500    4      12


Preamble = 7 octets, Start Frame Delimiter = 1 octet, MAC-d = 6 octets, MAC-s = 6 octets, Ethertype/Len = 2, Payload = 46-1500 bytes, Frame Check Sequence =  4 octets.

