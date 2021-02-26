## Ethernet

- Ethernet is a collection of network protocols/standards

Network protocols create ways of communication, agreeing on how. such as size and shape.

Electrical signals are 1's and 0's 8 bits are one byte. speed is measured in bits. 

1 Kb kilobit = 1000 bits
1 Mb megabit = 1000000 bits
1 Gb gigabit = 1000000000 bits
1 Tb terabit = 1000000000000 bits

##### Ethernet Standards

- Defined in the IEEE 802.3

| Speed    | Common Name       | IEEE Standard | Informal Name | Max Length |
|----------|-------------------|---------------|---------------|------------|
| 10 Mbps  | Ethernet          | 802.3i        | 10BASE-T      | 100M       |
| 100 Mbps | Fast  Ethernet    | 802.3u        | 100BASE-T     | 100M       |
| 1 Gbps   | Gigabit  Ethernet | 802.3ab       | 1000BASE-T    | 100M       |
| 10 Gbps  | 10 Gig Ethernet   | 802.3an       | 10GBASE-T     | 100M       |
-----------------------------------------------------------------------------

TYPES OF CABLE:

UTP - Unshielded Twisted Pair 

10BASE-T AND 100BASE-T = 2 Pairs (4 wires)

1000BASE-T and 10GBASET = 4 Pairs (8 wires)

##### PC to Switch

First pairs connects to pins 1 and 2. PC uses pin 1 and 2 to transmit and the switch (RX) recevies on pin 1 and 2.

The switch sends data on pins 3 and 6 and the pc recieves on those pins. 

This is known as Full Duplex

##### Router to Switch (Using 100BASE-T)

Pins 1 & 2 and 3 & 6

A switch receives data on 1 and 2 (RX) and then transmits data on 3 & 6 (TX)

A router sends data on pins 1 & 2 (TX) and receives data on 3 and 6 (RX) same as a PC

This cable is called a straight-through cable

##### Connecting Router to Router / Switch to Switch

To acheive this we need to use a 'crossover' cable.

Pins 1 and 2 connect to the other side using pins 3 and 6. 
Pins 3 and 6 connect to the other side using pins 1 and 2.

| Device   | Transmit Pin (TX) | Receive Pin (RX)  
|----------|-------------------|-----------------|
| Router   | 1 and 2           | 3 and 6         |
| Firewall | 1 and 2           | 3 and 6         | 
| PC       | 1 and 2           | 3 and 6         |
| Switch   | 3 and 6           | 1 and 2         |     
--------------------------------------------------

Most modern networks use Auto MDI-X which is automatic detection for connection type.

Fiber Optics have increased speeds and distances possible.

##### UTP vs Fiber-Optic

**UTP:**
	- Lower cost than fiber
	- Shorter max distnace
	- Can be vulnerable to EMI
	- RJ45 ports used with UTP are cheaper than SFP
	- Emit a signal outside of the cable which can be copied

**Fiber Optic:**
	- Higher cost than UTP
	- Longer max distance
	- Not vulnerable to EMI
	- SFP ports are more expensive tha RJ-45
	- Does not emit any signal outside of the cable



