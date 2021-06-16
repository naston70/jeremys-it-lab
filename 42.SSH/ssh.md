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
