<img width="981" height="949" alt="image" src="https://github.com/user-attachments/assets/3fa4f974-bf5a-414f-a012-6c11195cdee8" />### PACKET AND FRAMES

## Packet
A packet is a small piece of data used at the Network Layer (Layer 3).
A packet is used to move data across different networks using IP addresses.

# Packet Contains
 Source IP address
 Destination IP address
 Data (payload)

### Frame
A frame is a small piece of data used at the Data Link Layer (Layer 2).
A frame is used to deliver data between devices on the local network using MAC addresses.

# Frame Contains
 Source MAC address
 Destination MAC address
 Packet
 Error checking

### Encapsulation
Encapsulation is the process of wrapping a packet inside a frame.
It means the Data Link Layer adds extra information around the packet before sending it on the local network.


### Packet Headers
Packet headers are extra networking information added at the beginning of a packet to help the packet travel correctly across the network.

# Time To Live (TTL)
Prevents network congestion
Limits how long packet can travel.

# Checksum
 Detects corrupted data

# Source Address
IP address of sender

# Destination Address
IP address of receiver

## Cat Example 

Packet:
"Send cat image to this network/IP"

Frame:
"Send cat image to this exact laptop/device"
### TCP THREE WAY HANDSHAKE
SYN
SYN/ACK
ACK
# Step 1 — SYN
Laptop says:
Hello, can we connect?
This is:
SYN

# Step 2 — SYN/ACK
 Server replies:
 Yes, I received your request.
 Can we connect?
 This is:
 SYN/ACK
 
 # Step 3 — ACK
Laptop replies:
Yes, connection established.
This is:
ACK
Now connection exists.

# EX daigram
<img width="849" height="749" alt="image" src="https://github.com/user-attachments/assets/e78e5938-9d76-4b59-81de-9c10ced83cd8" />


Sequence Number = Current packet
ACK Number = Next packet expected

So:
Seq=0 → ACK=1
Seq=1 → ACK=2
Seq=2 → ACK=3
TCP uses this system to ensure packets arrive in the correct order with no missing data

### TCP Closing a Connection:
example conversation = 
Laptop: FIN
(I am done)

Website: ACK
(I heard you)

Website: FIN
(I am done too)

Laptop: ACK
(I heard you)
<img width="892" height="727" alt="image" src="https://github.com/user-attachments/assets/4f0d0596-8345-4f45-8b1f-514065954381" />

### TCP HEADERS
Source Port      = Which app sent it?
Destination Port = Which app receives it?

Port = Room Number
A port identifies a specific application/service running on that device.
Example:
80   = HTTP (Website)
443  = HTTPS (Secure Website)
25   = SMTP (Email)


Source IP        = Who sent it?
Destination IP   = Who receives it?

Sequence Number  = Current packet number
ACK Number       = Next packet expected

Checksum         = Error checking
Data             = Actual content
Flag             = TCP instructions ( SYN ACK FIN RST )

## TCP Headers Example

Downloading a cat image from a website:

Source Port: 52000 → Browser port
Destination Port: 443 → HTTPS website
Source IP: 192.168.1.5 → Your laptop
Destination IP: 142.xx.xx.xx → Cat website
Sequence Number: 100 → Current packet number
ACK Number: 101 → Next packet expected
Checksum: Valid → Data not corrupted
Flag: ACK → Packet received
Data: Cat Image

## Practical - Handshake

View Site
Help Alice and Bob communicate by re-assembling the TCP handshake in the correct order in the static lab attached to this task!

### TASK
SYN : Can you hear me Bob?
SYN/ACK : Yes, I can hear you!
ACK : Okay Great
DATA : Cheesecake is on sale!
ACK : I Hear ya!
FIN/ACK : I'm all done
FIN/ACK : Yeah Me Too
ACK : Okay, Goodbye

What is the value of the flag given at the end of the conversation?
<img width="943" height="785" alt="image" src="https://github.com/user-attachments/assets/8c96b1b3-94a2-4b18-922c-39dd84ea64d9" />
 #  Why 2 FIN/ACK
There are two FINs because both sides must say "I'm done."
There is only one SYN/ACK because the server can acknowledge the client's SYN and send its own SYN in the same packet.

There is only one SYN/ACK because the server can acknowledge the client's SYN and send its own SYN in the same packet.



## UDP Headers

Time To Live (TTL)
 Limits how long a packet can travel
 Prevents packets from looping forever

Source Address
 IP address of sender

Destination Address
 IP address of receiver

Source Port
 Port used by sender application
 Chosen randomly

Destination Port
 Port of receiving application/service

Data
 Actual information being transmitted


## Cat Example
<img width="981" height="949" alt="image" src="https://github.com/user-attachments/assets/5ad9ac2a-240e-44b7-80b8-99b2d9e7f6cd" />
Bob requests a cat video:

Request:
Bob → Alice

Alice sends:

 Cat Video Packet 1
 Cat Video Packet 2
 Cat Video Packet 3

If Packet 2 is lost:

TCP:
 Resends Packet 2
 Complete video received

UDP:
 Does not resend Packet 2
 Video continues playing
 Some frames may be missing or pixelated

## UDP Communication Flow

Request
↓
Response
↓
Response
↓
Response

## Key Point

TCP:
Reliable
Slower
Uses SYN, ACK, FIN


UDP:
Fast
Unreliable
No SYN
No ACK
No Connection Setup
### UDP IS STATELESS = 
UDP does not keep track of a connection between devices
It sends data and doesn't remember what happened before

### Common Network Protocols & Ports

## FTP (File Transfer Protocol)
 Port: 21
 Used to transfer files between computers
 Example: Downloading or uploading files to a server

## SSH (Secure Shell)
 Port: 22
 Used for secure remote login
 Command-line access to another computer
 Commonly used on Linux servers

## HTTP (HyperText Transfer Protocol)
 Port: 80
 Used to access websites 
 Transfers web pages, images, and videos
 Data is not encrypted

## HTTPS (HyperText Transfer Protocol Secure)
 Port: 443
 Secure version of HTTP
 Uses encryption to protect data
 Used by most modern websites

## SMB (Server Message Block)
 Port: 445
 Used for file and printer sharing
 Allows computers to access shared folders over a network

## RDP (Remote Desktop Protocol)
 Port: 3389
 Used to remotely control another computer 
 Provides a graphical desktop interface
 Commonly used on Windows systems

## Cat Examples 

FTP → Upload cat photos to a server
SSH → Manage a cat server using commands
HTTP → Open a cat website
HTTPS → Open a secure cat website
SMB → Share a cat photos folder
RDP → Control a PC that stores cat photos
 
