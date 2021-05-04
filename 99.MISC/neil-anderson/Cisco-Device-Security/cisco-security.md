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

#### Securing VTY lines with Access Lists

* It is possible to apply an Access List to control access to the VTY lines
* This can be used to limit Telnet and SSH access to only an administrators workstation

**example config:**
```
#access-list 1 permit host 10.0.0.10

#line vty 0 15
#login 
#password example123
#access-class 1 in 
```

- An unauthorised IP will be refused connection 


#### Basic Privileged Exec Security 

- When you connect over the console or VTY line you will land at the User Exec prompt which has a very limited set of commands available
- To get superuser access the 'enable' command is required 
- This can be secured with a password 

[old command]
```
#enable password Password123
```

* using this command the enable password can be viewed in plain text in the running configuration. This can be a security concern 

#### Enable Secret 

* An enable secret performs the same function as the enable password 
* The enable secret is always shown in encrypted form in the running configuration
* If both are enabled the enable secret password will be used
* Best practice is to configure an enable secret but not an enable password 

#### Service Password-Encryption 
- The service password encryption command encrypts all passwords in the running configuration
- It is best practice to enable this   

```service password-encryption
```

#### Line Level Security Lab Demo 


```
[securing line access:]

#conf t
#line console 0
#password example123
#login
#exit

[allow access via telnet:]

#conf t 
#line vty 0 15 (all lines)
#password example123
#login 

[This allows enable access via telnet]

#enable secret example123 (encrypted)

[encrypts all passwords in running-config:]

#service password-encryption
```


## Usernames and Privilege Levels 

* With line level security all administrators log in with the same password 
* More granular security can be provided by configuring individual usernames and passwords for different administrators

```
#username admin1 secret example123
#username admin2 secret example456
#line console 0
#login local (use local usernames)
#line vty 0 15 
#login local 
```

#### Privilege Levels 

* There are 16 levels of admin access (0-15) on a Cisco router or switch
* Usernames can be assigned to a privilege level, default is 1
* You can also configure different password for direct access to the different levels
* Each command in IOS can be assigned a privilege level. An administrator must be logged in with that Privilege level or higher to run the command 

- By default, three levels of Privilege are used -  zero, user and Privileged.
- Zero-level access allows only five commands - logout, enable, disable, help and exit
- User level (level 1) provides very limited read-only access to the router. When you enter User Exec Mode users are at Privilege Level 1 by default
- Privileged level (level 15) provides complete control over the outer. 'enable' is at level 15

## SSH 

SSH vs Telnet:

* All telnet communications cross the network in plain text 
* If somebody sniffs the traffic it would be possible to see all commands and usernames and passwords 
* All SSH traffic is encrypted 
* If this traffic is sniffed it is not readable 
* Best practice is to disable telnet and only allow SSH for administrator CLI access 

- A digital certificate with a key length of at least 768 bits must be generated to enable SSH encryption
```
#ip domain-name example.com 
#crypto key generate rsa 

The name of the keys with be hostname.example.com 
...
How many bits in the modulus [512]: 768
```

















