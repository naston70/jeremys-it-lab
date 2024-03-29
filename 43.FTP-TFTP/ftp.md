## FTP and TFTP

FTP (file transfer protocol) and TFTP (trivial file transfer protocol) are industry standard protocols used to transfer files over a network.

They both use a client-server model
    - clients can use ftp/tftp to copy files from a server 
    - clients can use ftp/tftp to copy files to a server 

As a network engineer the most common use of ftp is in the process of upgrading the operating system of a network device 

FTP can be used to download the latest version of IOS from a server and the reboot the device with the new image 

#### TFTP - Trivial File Transfer Protocol 

- TFTP was first standardized in 1981 
- Named 'Trivial' because it is simple and only has basic features compared to FTP. -
- Only allows a client to copy a file to or from a server 
- Was released after FTP but is not a replacement. It is another tool to use when lightweight simplicity is more important than functionality 
- No authentication, so servers will respond to all TFTP requests 
- No encryption, all data is sent in plain text 
- Best used in a controlled environment to transfer small files quickly 
- TFTP servers listen on UDP port 69
- UDP doesn't provide reliability or retransmission but these features come in the TFTP protocol itself.

#### TFTP Reliability 

- Every TFTP data message is acknowledged
    - if the client is transferring a file to the server the server will send the ACK message
    - if the server is transferring a file to the client the client will send ACK messages

- Timers are used, and if in an expected message isn't received in time the waiting device will resend its previous message 

* TFTP uses 'lock-step' communication. The client and server alternately send a message and then wait for a reply - retransmissions are sent as needed

#### TFTP Connections

TFTP file transfers have three phases:

1. Connection: TFTP clients send a request to the server and the server responds back, initializing the connection 

2. Data Transfer: The client and server exchange TFTP messages. One sends data and the other sends acknowledgments

3. Connection Termination: After the last data message has been sent a final acknowledgment is sent to terminate the connection 


#### File Transfer Protocol 

- FTP first standardized in 1971
- FTP uses TCP port 20 and 21 
- Usernames and passwords are used for authentication, however there is no encryption
- For better security, FTPS can be used 
- SFTP can also be used for greater security 
- FTP is more complex than TFTP and allows not only file transfers, but clients can also navigate file directories, add and remove directories, list files, etc 
- The client sends FT commands to the server to perform these functions

#### FTP Control Connections 

FTP uses two types of connections:
* An FTP control (TCP 21) is established and used to send FTP commands and replies
* When files or data are to be transferred, seperate FTP data (TCP 20) connections are established and terminated as needed

##### Active Mode FTP Data Connections

- The default method of establishing FTP data connections is **active mode**, in which the server initiates the TCP connection 

- In FTP **passive mode**, the client initiates the data connection. This is often necessary when the client is behind a firewall which could block the incoming connection from the server 

Firewalls do not usually permit 'outside' devices to initiate connections. In this case **passive mode** is used and the client (behind the firewall) initiates the TCP connection 

## FTP vs TFTP

FTP:
Uses TCP for connection based communication (20 for data, 21 for control)

TFTP:
Uses UDP 69 for connectionless communication 
------------

FTP: 
Clients can use FTP commands to perform various actions, not just copy files

TFTP: 
Clients can only copy files to or from the server 

------------
FTP:
Has username and password 
TFTP:
No authentication

#### IOS File Systems 
- A file system is a way of controlling how data is stored and received 
- Use the command ```show file systems``` to view on cisco

#### Upgrading Cisco IOS 
 - View current version using ```show version``` command 
 - View contents of flash memory with ```show flash``` 

###### Copy files:

```
#copy source destination
Address or name of remote host []?
Source filename []?
Destination filename [filename]?

example:
#copy tftp: flash:

Enter the TFTP server IP 
Enter the filename on the server 
Enter name to save file as
```

To make IOS use the newly downloaded version:
```
#conf t
(config)#boot system flash: filename
write memory 
```

If this command isn't used IOS will use the first version of IOS it finds 

To clean up the old version use:
```
#delete flash: filename
```

#### Using FTP

```
(config)#ip ftp username cisco
(config)#ip ftp password cisco
(config)#exit

R1#copy ftp: flash:
Address or name of remote host []?
Source filename []?
Destination filename [filename]?
```


Update OS via ftp:

```
(config)#ip ftp username cisco
(config)#ip ftp password cisco
(config)#exit

R1#copy ftp: flash:
Address or name of remote host []?
Source filename []?
Destination filename [filename]?

#conf t
(config)#boot system flash: filename
(config)#exit
#write memory 
#reload


```


