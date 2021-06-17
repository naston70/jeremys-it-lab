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
