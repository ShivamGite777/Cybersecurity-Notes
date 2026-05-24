
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







### Bus topology
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


