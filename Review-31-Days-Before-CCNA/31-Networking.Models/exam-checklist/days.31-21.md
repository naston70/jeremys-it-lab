## CCNA Checklist Days 31-21 

## Create a diagram of the layered models

###### OSI Model 

**7. Application** - Network process to Application
**6. Presentation** - Data Representation and Encryption
**5. Session** - Interhost communication 
**4. Transport** - End to end communication and reliability
**3. Network** - Best path determination and IP addressing
**2. Data-Link** - MAC and LLC
**1. Physical** - Media, Signal and Binary Transmission 

###### TCP Model 
 
**Application** - (Application, Session, Transport)

**Transport** - Transport

**Internet** - Network 

**Network Access** - Network Access and Internet 

#### Describe details of sending an email from source to destination 

First the sender enters the email address of the recipient along with the message using an email application.
Then the 'send' button is clicked and the email goes to the Mail Transfer Agent (MTA) via the SMTP protocol. 

Next is the DNS lookup. The system sends a request to find out the corresponding MTA of the recipient with the help of the MX record. In the DNS zone for the receivers addresses domain, there will be an MX record (Mail Exchanger). This is a DNS resource record which specifies the mail server of a domain. So after the DNS lookup, a response is given to the requested mail server with the IP address of the recipients mail server.

The next step is the transfer of the message between mail severs. The STMP protocol is used for this communication. 

###### Protocols used for email service

POP3, IMAP and SMTP. SMTP is used to forward the email while the other two are used to retrieve email from an email server

IMAP uses port 143 and over SSL 993
POP3 uses port 110 and 995
SMTP uses 25, 2525 and 465


## Describe the CSMA/CD process

Carrier Sense Multiple Access with Collision Detection is a MAC method used notably in early Ethernet technology for LAN networking. It uses carrier sensing to defer transmissions until no other stations are transmitting. This is used in combination with collision detection in which a transmitting station detects collisions by sensing transmission from other stations while it is transmitting a frame. (wiki)

Half-Duplex networks use CSMA/CD, commonly in networks with repeaters and hub as all their ports are in the same collision domain. 

## Purpose of a MAC Address

Network functionality in the OSI model is subdivided into layers. MAC addresses function at the Data-Link Layer allowing computers/ NICs to identify themselves at this level. Also can be used in filtering and data recovery

## Describe structure and purpose of IPv4

The IPv4 packet is composed of a number of different fields that can be used by the source and intermediary devices to determine the way a specific packet us treated when being transported. These are the different fields within:

| Version 4 bits || IHL 4 bits || TOS 8 bits || Length 16 bits |
|Identification 16 bits| |Flags 4 bits| |Fragment Offset 12 bits|
| TTL 8 bits | | Protocol 8 bits | | Checksum 16 bits |
|Source Address 
|Destination address
| Options 24 bits | | Padding 8 bits |

###### Version Field