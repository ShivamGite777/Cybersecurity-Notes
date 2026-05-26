
### OSI MODEL


The OSI model (or Open Systems Interconnection Model) is an essential model used in networking.  This critical model provides a framework dictating how all networked devices will send, receive and interpret data.
<img width="850" height="588" alt="image" src="https://github.com/user-attachments/assets/3c9518f1-6fdd-4c77-9f82-59ae7a6ab8cc" /> 
There are 7 layers in OSI MODEL
The OSI (Open Systems Interconnection) model is a conceptual framework used to understand how data travels from one computer to another over a network.

Data flows:

Sending: Layer 7 → Layer 1
Receiving: Layer 1 → Layer 7

## PHYSICAL LAYER
 PHYSICAL TRANSMISSION OF DATA
 Devices use electrical signals to transfer data between each other in a binary numbering system (1's and 0's).
 For example, ethernet cables connecting devices

Example:
 Cat image converted into electrical or wireless signals


## DATA LINK
The Data Link Layer is responsible for physical addressing using MAC addresses and preparing data for transmission.

It means the Data Link Layer uses a device's MAC address to identify the exact physical device on a local network.
You download a cat image. 
EXAMPLE = PHYSICAL ADDRESSING

The website sends data to your Wi-Fi network.

Inside your network there may be:

Laptop 
Phone 
TV 

All devices may be on the same network.

So the router asks:
 “Which exact device should get this cat image?”

The answer is through the MAC address.
Example:

Laptop MAC = 00:1A:2B:3C:4D:5E

The Data Link Layer attaches this MAC address:

Destination MAC: 00:1A:2B:3C:4D:5E

Now the router knows:

👉 “Send it to this laptop only.”

That process is called physical addressing.

Why is it called “physical” addressing?
Because the MAC address belongs to the actual network hardware (NIC) inside the device.

Unlike IP addresses:
IP → can change
MAC → tied to the network device

Physical addressing using MAC = using a device’s hardware address to deliver data to the exact device. 
DATA LAYER DOES THIS THINGS
1. PHYSICAL ADDRESSING
2. FRAME CREATION
   It packages data into a frame:
   [MAC Address + Data + Error Check]
3. ERROR DETECTION
EX =   
Checks:
 “Did the cat image data get corrupted while traveling?”
4. NODE-TO-NODE DELIVERY
Moves data between connected devices:
Example:
Router → Laptop



### Role of NIC (Network Interface Card) in Data Link Layer
The NIC (Network Interface Card) is the hardware component that helps the Data Link Layer communicate with the network.
1. Stores the MAC Address
2.  Sends and Receives Frames
3.  Checks Destination MAC Address
# Cat Example

You download a cat image.

Router sends cat image frame:
Destination MAC: 00:1A:2B:3C:4D:5E
Your NIC checks:

 “Does this MAC match my MAC?”

If yes:
 Accept cat image
 Pass to upper layers



 ### NETWORK LAYER

Responsible for routing and packet reassembly
Uses IP addresses for communication
Determines the best path for data transfer
Routers operate at this layer
Routers are called Layer 3 devices

1. Logical Addressing
Uses IP addresses to identify source and destination.
Example:
Source IP: 192.168.1.5
Destination IP: 142.xx.xx.xx

2. Routing
Routing determines the most optimal path for data packets to travel from source to destination.
Example:
Router A → Router B → Router C → Laptop

3. Packet Forwarding
Moves packets from one network to another.
# EX DAIGRAM
<img width="1357" height="569" alt="image" src="https://github.com/user-attachments/assets/5800325d-96ac-45a8-8338-86fbc9488a97" />
# OPTIMAL PATH PROTOCOL
OSPF (Open Shortest Path First) 
RIP (Routing Information Protocol)


