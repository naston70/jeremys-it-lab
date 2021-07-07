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
