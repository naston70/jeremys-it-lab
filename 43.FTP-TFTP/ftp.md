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
