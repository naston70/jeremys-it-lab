## OSPF Advanced 

* OSPF routers identify themselves using an OSPF Router ID which is in the form of an IP address 
* This will default to being the highest IP address of any loopback interfaces configured on the router, or the highest other IP address if a loopback doesn't exist
* Loopback interfaces never go down so the router ID will not change
* You can manually specify the Router ID
* Best practice is to use a Loopback or manually set the Router ID 

- If a loopback or higher IP address is configured, the ROuter ID will only change on OSPF process restart.

#### Passive Interface Configuration

```
#router ospf 1
#passive-interface [loopback]
#passive-interface [interface]
```

The interface will be advertised but wont try to form any adjacencies or share any information.

Possible to make ```passive-interface default``` to make all interfaces passive

#### Default Route Injection

Create a default route out to the Internet:
```
#ip route 0.0.0.0 0.0.0.0 203.0.113.2
#router ospf 1
#default-information originate
```

It is undesirable to make static routes out to the Internet on every device so better to create a default static route and let it be learned dynamically

