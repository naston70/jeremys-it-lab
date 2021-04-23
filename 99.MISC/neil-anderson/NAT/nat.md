## NAT - Network Address Translation

- An organisation can use private IP addresses on their inside network but still grant their hosts Internet access by translating them to their outside public IP addresses
- Many hosts on the inside can share a few or a single public IP address on the outside

#### Static NAT

- **Static NAT** - permanent one to one mapping usually between a public and private IP address. Used for servers which must accept incoming connections

- **Dynamic NAT** - uses a pool of public addresses which are given out on an as needed first come first served basis. Usually used for internal hosts which need to connect to the Internet but do not accept incoming connections

- **PAT (Port Address Translation)** - allows the same public IP to be reused

#### Static Nat Scenario

- Bought range 203.0.113.0/28 from service provider
- 203.0.113.2 is used on the outside interface on the Internet edge router R1
- 203.0.113.1 is used as the default gateway address. 
- 203.0.113.3 - 203.0.113.14 remain available

- Int-S1 at 10.0.1.10 is an internal web server which needs to accept incoming connections from the Internet
- A fixed public IP address is needed to accept incoming connections, we use 203.0.113.3
- A static NAT translation is required to translate the public IP address 203.0.113.3 on f0/0 to 10.0.1.10 on f1/0 for incoming connections
- The translation is bidirectional so will also translate 10.0.1.10 to 203.0.113.3 for outbound traffic from the server 

