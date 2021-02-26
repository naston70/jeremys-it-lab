# Ethernet Frame


How an ethernet frame looks: 

|Eth header|			Packet		 |Eth trailer|


Within the Ethernet Header:

Preamble|SFD|Destination|Source|Type

The Ethernet trailer only contains an FCS


### Preamble and SFD

**Preamble:**

7 bytes
Alternating 1's and 0's
Allows devices to sync their recevier clocks

**SFD:**
Start Frame Delimter
1 byte length
Marks the end of the preamble, and beginning of the rest of the frame
