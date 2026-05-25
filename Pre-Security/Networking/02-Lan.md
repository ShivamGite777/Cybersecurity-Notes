
## LOCAL AREA NETWORK
### STAR TOPOLOGY
DEFINITION
Every device (computer, printer, etc.) connects to one central device
This central device is usually a switch or hub.

The main premise of a star topology is that devices are individually connected via a central networking device such as a switch or hub.
EX DAIGRAM
<img width="218" height="193" alt="image" src="https://github.com/user-attachments/assets/94e828ce-b836-4d8f-b4b4-baeb95c53d26" />

# purpose
the purpose of star topology is to provide a reliable, scalable, and easy-to-manage network using a central device for communication.

# Working
1. Device Connection
Each computer or device is directly connected to a central switch/hub using a cable.
2. Sending Data
When a device wants to send data, it does not send it directly to another device.
3. Data Transfer to Central Device
The sending device sends the data to the central switch/hub.
4. Forwarding Data
The switch/hub checks the destination address and forwards the data to the correct device.
5. Receiving Data
The destination device receives the data from the central device.
# example
<img width="215" height="157" alt="image" src="https://github.com/user-attachments/assets/396013f6-76d0-4e6c-a167-4f637df410ba" />
If PC1 wants to send data to PC3:
 PC1 → Switch → PC3
 PC1 TO PC3 VIA SWITCH
 # ADVANTAGES
 Easy to install and manage
 Easy to add new devices

# DISADVANTAGES
if central device fails , whole network stops
more expensive due to extra cables and devices







### BUS topology
A Bus Topology is a network design where all devices are connected to a single main cable, called the backbone cable.
data for each device travels along the same cable

# purpose

The purpose of bus topology is to connect all devices in a network using a single backbone cable so that data can be transmitted easily and at low cost.
# data flow working
1. Device Connection
All devices are connected to a single backbone cable.
2. Data Transmission
When a device sends data, it is placed on the backbone cable.
3. Data Flow
The data travels in both directions along the cable.
4. Data Reception
All devices receive the data, but only the intended recipient accepts it.
5. Terminators
Terminators are placed at both ends of the cable to stop signal reflection.

data flow through all device , device checks address of packet
# examples
<img width="881" height="553" alt="image" src="https://github.com/user-attachments/assets/1e54b780-4757-4a6f-80a3-c88e9464a9b4" />
PC1 —— PC2 —— PC3 —— PC4

# advantages
easy
cost-efficient

# disadvantages
single point failure lead to system failure,No data will be transmitted.


### RING topology
Ring topology is a network structure in which each device is connected to two neighboring devices, forming a circular path.
## Purpose of Ring Topology
The main purpose of ring topology is to transmit data in an organized manner through a circular path, reducing data collisions.
## Working of Ring Topology
1. Circular Connection
All devices are connected in the form of a ring.
2. Data Transmission
Data travels from one device to the next device in the ring.
3. Forwarding Data
Each device receives the data, checks the destination, and forwards it.
4. Data Reception
The destination device accepts the data, while other devices pass it along.
## Advantages 
Easy to troubleshoot because data moves in one direction
Less chance of netwrok bottlenecks
Handles network traffic better than bus topology
data transmission is more organized
## Disadvantages 
 Data may pass through many devices before reaching destination
 Not efficient for large networks- If one cable breaks, the entire network can fail
 Failure of one device can affect the whole network

# netwrok bottlenecks  - a condition where heavy traffic at one point slows down the entire network.
# Example daigram
<img width="932" height="563" alt="image" src="https://github.com/user-attachments/assets/0d242d9f-697f-44e0-a2fa-71da1169a9f2" />



### SWITCH
A switch is a networking device that connects multiple devices and sends data only to the intended device, improving network efficiency.
# switch has multiple ports
4 8 16 24 32 64 ports

devices connect to a switch using Ethernet cables.
# Example daigram
<img width="1331" height="684" alt="image" src="https://github.com/user-attachments/assets/0e1b0a3c-9135-4519-ad05-323a186b615e" />


### ROUTER
A router is a networking device used to connect different networks and transfer data between them.
A router connects different networks and uses routing to choose the best path for data transfer
## Working of Router
1. Receives Data
The router receives data packets from a device.
2. Checks Destination
It checks the destination IP address.
3. Selects Best Path
The router chooses the best available route.
4. Forwards Data
The data is sent through the selected path.
# Data packets - When a device sends information, the data is broken into small pieces called packets.

# example and daigram 
<img width="1400" height="433" alt="image" src="https://github.com/user-attachments/assets/c7f40c0d-ef6f-4b38-a7ff-f1ba6d29bbe4" />


### Complete the interactive lab attached to this task. What is the flag given at the end?
##  Video
[Watch Video](./02A-lan.mp4)


### SUBNETTING

## Definition
Subnetting is the process of dividing one large network into smaller networks called subnets.

## Purpose of Subnetting
 Organize large networks
  Reduce network traffic
  Improve security
  Use IP addresses efficiently
  Make network management easier

## Working of Subnetting
1. Start with one large network
2. Divide it into smaller subnetworks
3. Assign devices to different subnets
4. Each subnet works independentl

## Advantages

Better network performance
 Reduces congestion
 Easier troubleshooting
Improves security
 Efficient IP usage

## Disadvantages
Complex to configure 
Requires subnet planning
Can be difficult for beginners
# Daigram
<img width="1330" height="811" alt="image" src="https://github.com/user-attachments/assets/61e050fb-0b78-42aa-afb0-d8e1ab0970fc" />

# subnet use ip address in 3 diff ways
<img width="1611" height="406" alt="image" src="https://github.com/user-attachments/assets/69cbca7b-84ce-4851-b55a-06151166621d" />
# Network address
It tells us which network a device belongs to
ex = 192.168.1.0
Last part = 0
Identifies the whole network
Not assigned to devices
# Host address
A Host Address identifies a specific device inside the network.
192.168.1.1 → 192.168.1.254
Examples:
192.168.1.20
192.168.1.100
# Default address
A Default Gateway is usually the router address used to send data outside the network.
ex = 192.168.1.1
or
192.168.1.254
# Broadcast address
A Broadcast Address is a special IP address used to send data to all devices in a network at the same time.
Instead of sending data to one device, it sends it to everyone on the network.
ex = 192.168.1.255
Sends data to all devices
Reserved address














