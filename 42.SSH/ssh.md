## SSH

By default no password is needed to access the CLI of a cisco IOS device via the console port.
A password can be configured on the console line and a user will then have to enter a password to access the CLI via the console port.

#### Configuration of password on console 
```
R1(config)#line console 0
R1(config-line)#password ccna
R1(config-line)#login
R1(config-line)#end
R1#exit 
...
User Access Verification

Password:
```

#### Console Port Security - login local

Alternatively, you can configure the console line to require users to login one of the configured usernames on the device 
```
R1(config)#username jeremy secret ccnp
R1(config)#line console 0
R1(config-line)#login local
R1(config-line)#end
R1#exit 
...
Username: jeremy
Password:
R1>
```

```
exec-timeout 3 30
```

A useful command which logs out users after a period of inactivity


#### Layer 2 Switch - management IP

- Layer 2 switches don't perform packet routing and don't build a routing table. They aren't IP routing aware. 
- However, you can assign an IP address to an SVI to allow remote connections to the CLI of the switch (using Telnet or SSH)

```
SW1(config)#interface vlan1
SW1(config-if)#ip address 192.168.1.253 255.255.255.0
SW1(config-if)#no shutdown
SW1(config-if)#exit 

SW1(config)#ip default-gateway 192.168.1.254 
```
Configure the switch's default gateway.








