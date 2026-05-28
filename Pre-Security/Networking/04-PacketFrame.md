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

