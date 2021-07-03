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