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


#### Telnet

- Teletype Network  is a protocol used to remotely access the CLI of a remote host 
- Developed in 1969
- Largely replaced by SSH which is more secure 
- Telnet sends data in plain text. No encryption.

The Telnet server (the device being connected to) listens for traffic on **TCP port 23**

#### Telnet Configuration 

```
SW1(config)#enable secret ccna 
- If an enable password isn't configured, you wont be able to access privileged exec mode when connecting via Telnet  

SW1(config)#username jeremy secret ccna 
SW1(config)#access-list 1 permit host 192.168.2.1 (to limit which devices can connect to the VTY lines)s

SW1(config)#line vty 0 15
SW1(config-line)#login local
SW1(config-line)#exec-timeout 5 0
SW1(config-line)#transport input telnet 
SW1(config-line)#access class 1 in 
```

#### SSH 

- Developed in 1995 to replace less secure protocols like telnet
- SSHv2 is the major revision released in 2006
- If a device support both versions 1 and 2 it is said to run 1.99
- SSH provides security features such as data encryption and authentication

The SSH server listens for traffic on TCP port 22

#### SSH support

* IOS images that support SSH will have 'K9' in their name
Use the command:
```
#show ip ssh 
```

For information about the devices SSH capabilities.

After confirming compatibility ssh can then be configured.

#### SSH Configuration: RSA Keys

* To enable and use SSH, you must generate an RSA public and private key pair
* The keys are used for data encryption/decryption, authentication etc.
```
SW1(config)#ip domain name jeremysitlab.com
SW1(config)#crypto key generate rsa 
```

The FQDN of the device is used to name the RSA keys. After the keys have been generated a Syslog message is displayed. Once it is enabled SSH can then be configured. 

```
SW1(config)#enable secret ccna 
SW1(config)#username jeremy secret ccna 
SW1(config)#access-list 1 permit host 192.168.2.1
SW1(config)#ip ssh version 2
SW1(config)#line vty 0 15
SW1(config-line)#login local
SW1(config-line)#exec-timeout 5 0
SW1(config-line)#transport input ssh 
SW1(config-line)#access class 1 in 
```

#### SSH Configuration

1. Configure a host name
2. Configure DNS Domain name
3. Generate RSA key pair
4. Configure enable PW, username/PW 
5. Enable SSHv2 (only) - best practice
6. Configure VTY lines - transport input ssh 

To connect: ssh -l *username* *ip-address* OR ssh *username@ip-address*




