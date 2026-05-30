### PACKET AND FRAMES

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
