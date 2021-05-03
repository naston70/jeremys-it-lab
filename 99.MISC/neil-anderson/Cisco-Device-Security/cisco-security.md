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














