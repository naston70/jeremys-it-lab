## Line Level Security 


* When a Cisco router or switch is received from the factory no security is configured
* The command line can be accessed via a console cable with no password
* One of the first tasks is to configure security to ensure only authorised administrators can access the device  

#### IOS Command Hierarchy 

- hostname>     User Exec mode
- hostname#     Privileged Exec mode | **'Enable'**
- hostname(config)#     Global configuration mode | **'Configure terminal'**
- hostname(config-if)#  Interface configuration mode | **'interface X'**

#### Basic Line Level Security 

* Minimal password security can be configured through the use of static, locally defined passwords at three different levels 
    - Console line - accessing User Exec mode when connecting via a console cable
    - Virtual terminal VTY line - accessing User Exec mode when connecting remotely via Telnet or SSH Secure Shell
    - Privileged Exec Mode - entering the 'enable' command 
- The levels can be used independently or in combination with each other 
- They can use the same or different passwords 

#### Basic Console Security 

* Only one administrator can connect over a console cable at a time so the line number is always 0
* 'Login' with no following keywords requires the administrator to enter the password configured at the line level to log in 
```
#line console 0
#password Flackbox1
#login
```

#### Basic Telnet Security

- A administrator can use Telnet to connect to the CLI of a router or switch remotely over an IP connection 
- IOS devices do not accept incoming Telnet sessions by default
- An IP address and Virtual terminal VTY line access must be configured

#### Switch Management IP Address 

* A Layer 2 switch is not IP routing aware 
* It does however support a single IP address for management 
* A default gateway also needs to be configured to allow connectivity to other subnets 

**example config:**
```
#interface vlan 1 (or other vlan)
#ip address 192.168.10.10 255.255.255.0
#no shut
#exit
#ip default-gateway 192.168.10.1
```

#### Basic Telnet Security 

- Multiple administrators can connect at the same time. Lines are allocated on a first come first serve basis
- If all configured lines are in use then the additional administrators will not be able to log in 

#### Exec Timeout

* By default an administrator will be logged out after 10 minuted of inactivity 
* You can edit this value with the exec-timeout command
* ```no exec-timeout``` or ```exec-timeout 0``` allows an administrator to be logged in indefinitely 













