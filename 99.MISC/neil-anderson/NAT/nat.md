## NAT - Network Address Translation

- An organisation can use private IP addresses on their inside network but still grant their hosts Internet access by translating them to their outside public IP addresses
- Many hosts on the inside can share a few or a single public IP address on the outside

#### Static NAT

- **Static NAT** - permanent one to one mapping usually between a public and private IP address. Used for servers which must accept incoming connections

- **Dynamic NAT** - uses a pool of public addresses which are given out on an as needed first come first served basis. Usually used for internal hosts which need to connect to the Internet but do not accept incoming connections

- **PAT (Port Address Translation)** - allows the same public IP to be reused
