## IP Services

1. Which method will allow you to use RFC 1918 addresses for Internet requests?
- A. CIDR
- B. Classful addressing 
- C. NAT
- D. VPN

A. C, Network Address Translation (NAT) was created to slow the depletion of Internet addresses. It does this by translating RFC 1918 privatized addresses to one or many public IP addresses. 

2. A, the inside local address is the address local to the enterprise (private) and the address is inside the enterprise.

3. C, the inside global address is the address public to the enterprise. The address is inside of or controlled by the enterprise. 

4. D. The outside global address is the address public to the enterprise. The address is outside of the enterprise or outside of its control.

5. Which command will allow you to view the NAT translations active on the router?
```
A. Router#show ip nat translations 
B. Router#show nat translations
C. Router#debug ip nat translations 
D. Router#show translations nat
```

A. A, [show ip nat translations]

6. Which command will display an overview of the current number of active NAT translations on the router, as well as other overview
information?
```
A. Router#show ip nat translations 
B. Router#show ip nat summary
C. Router#show ip nat status
D. Router#show ip nat statistics
```

A. D, the command ```show ip nat statistics``` will display an overview of the number of active NAT translations on the router, as well as other statistical information for the NAT process. 

7. A.

8. D.

9. When configuring dynamic NAT, why must you configure an access list?
- A. The access list allows incoming access from outside global addresses.
- B. The access list allows outgoing access from inside local addresses.
- C. The access list allows outgoing access from outside local addresses.
- D. The access list allows outgoing access from inside global addresses.

A. B, The access list is used to identify IP addresses that are allowed to pass through the NAT process; these are considered the inside local addresses

10. Which command will wipe out all current NAT translations in the NAT table?
```
A. Router#no ip nat translation
B. Router#clear ip nat translation 
C. Router#clear ip nat translation * 
D. Router#clear ip nat
```

A. C

11. Which command will allow you to see real-time network address translations?
```
A. Router#show ip translations 
B. Router#debug ip nat
C. Router#debug ip translations 
D. Router#show ip nat
```

A. B. 

12. C

13. Which command will allow your router to synchronize with a time source of 129.6.15.28?
```
A. Router(config)#ntp server 129.6.15.28 
B. Router#ntp server 129.6.15.28
C. Router(config)#ntp client 129.6.15.28 
D. Router#ntp client 129.6.15.28
```

A. A. 

14. Which command configures the router or switch to trust its internal time clock?
```
A. Router(config)#ntp server
B. Router(config)#ntp master
C. Router(config)#ntp clock source 
D. Router(config)#ntp trusted
```

A. B. 

15. Which command will allow you to see if the router or switch is using NTP?
```
A. Router#show clock detail 
B. Router#show ntp
C. Router#show time
D. Router#show time source
```

A. A.

16. Which command will allow you to view the time details from a
configured server?
- A. Router#show clock detail
- B. Router#show ntp detail
- C. Router#show ntp associations detail
- D. Router#show ntp skew

A. C

17. Which protocol and port does NTP use for time synchronization by default?
- A. TCP/161 
- B. TCP/123 
- C. UDP/69 
- D. UDP/123

A. D. NTP uses UDP port 123

18. Which command will help you diagnose if the router or switch is getting an answer back from an NTP server?
- A. Router#show ntp
- B . Router#show ip ntp
- C.Router#debug ntp packets 
- D. Router#debug ntp messages

A. D, [debug ntp packets] will allow for the verification of packets received from an NTP server.

19. Which is a best practice for setting up NTP?
- A. Always configure the time source to a DNS address.
- B. Configure all devices to a public NTP server.
- C. Configure all devices to different NTP servers for redundancy. 
- D. Configure all devices as master servers.

A. A.

20. Which command will allow you to view the time drift observed by NTP?
- A. Router#show ntp
- B. Router#show ip ntp status 
- C. Router#show ntp status
- D. Router#debug ntp drift

A. C.

21. Which command sets the time zone of a router for Pacific Standard Time?
- A. Router(config)#clock timezone pacific 
- B. Router(config)#clock timezone pst -8 0 
- C. Router(config)#timezone pacific
- D. Router(config)#timezone pst -8

A. B. -8 from UTC with a 0 minutes offset

22. You are configuring NTP on your switch. You want to configure the switch so if any interface fails, NTP will still be available. Which type of interface should you use? Choose the best answer.
- A. Tunnel interface
- B. NTP interface
- C. Loopback interface
- D. Switched Virtual Interface (SVI)

A. C.

23. Which command will configure NTP to use the internal loopback interface?
- A. Switch(config)#ntp source loopback 0 
- B. Switch(config)#ntp loopback 0
- C. Switch(config)#ntp master loopback 0 
- D. Switch(config)#ntp clock loopback 0

A. A.

24. Which command will set the router’s internal clock to 2:24 August 1, 2019?
- A. Router(config)#clock set 2:24:00 1 august 2019 
- B. Router#clock set 2:24:00 1 august 2019
- C. Router(config)#clock set 2:24:00 august 1 2019
- D. Router#clock 2:24:00 1 august 2019

A. B.

25. Which statement is correct about reverse lookups?
- A. A reverse lookup is when the request needs to be reversed to another DNS server.
- B. A reverse lookup is the resolution of an IP address to FQDN.
- C. A reverse lookup is when the DNS queried can answer the request without asking another DNS server.
- D. A reverse lookup is the resolution of an FQDN to an IP address.

A. B, a reverse lookup is when the FQDN is resolved from an IP address. This is useful when you want to identify an IP address. 


26. Which record type is used for an IPv4 address mapping to FQDN for DNS queries?
- A. The A record
- B. The CName record 
- C. The PTR record 
- D. The AAAA record

A. C, the PRT (pointer record) is used to look up IP addresses and return FQDNs that are mapped to them. 

27. What gets appended to hostname queries for DNS resolution? 
- A. The DNS domain name
- B. The DNS zone
- C. The host header
- D. The hostname PTR record

A. A

28. Which is the most secure method of name resolution for routers and switches?
- A. DNS
- B. PTR records
- C. Static hostname entries 
- D. LLMNR

A. C. (configured locally)

29. Which type of DNS record holds the IPv4 IP address for a hostname?
- A. The A record
- B. The CName record 
- C. The PTR record 
- D. The AAAA record

A. A.

30. What limits the amount of time that a DNS entry is available in the DNS cache?
- A. An A record
- B. TTL
- C. SOA
- D. Default of 5 minutes

A. B, the TTL limits the amount of time a DNS entry will be available in the DNS cache. 

31. Which message is sent from the DHCP client to the DHCP server to confirm the offer of an IP address?
- A. Acknowledgment 
- B. Discover
- C. Offer
- D. Request

A. A.

32. What form of communication does a DHCP client use to initially acquire an IP address?
- A. Layer 3 broadcast 
- B. Layer 3 multicast 
- C. Layer 3 802.1Q 
- D. Layer 3 unicast

A. A, DHCP uses Layer 3 broadcasts by sending packets to 255.255.255.255 for initial DHCP discovery. 

33. At what point of the lease time will the client ask for a renewal of the IP address from the DHCP server?
- A. One-quarter of the lease 
- B. One-half of the lease
- C. Seven-eighths of the lease 
- D. End of the lease

A. B

34. Which statement is correct about the DHCP process?
- A. The DHCP server is responsible for maintaining the life cycle of an IP address.
- B. DHCP uses multicasting between the client and server.
- C. The DHCP client is responsible for maintaining the life cycle of an IP address.
- D. The DHCP lease is negotiated between client and server.

A. C, after the initial Discover, Offer, Request and Acknowledge, it is the responsibility of the client to maintain the lease of the IP address.

35. Which transport protocol does DHCP use?
- A. UDP 
- B. ICMP 
- C. TCP 
- D. RARP

A. A, DHCP uses UDP as a connectionless protocol for the DORA packets. 
