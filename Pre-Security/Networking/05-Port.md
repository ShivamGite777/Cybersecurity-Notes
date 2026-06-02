<img width="885" height="893" alt="image" src="https://github.com/user-attachments/assets/2298d6a3-e1b9-4688-8439-7016a7e77960" />### PORT FORWARDING

## Definition
 Port forwarding allows devices outside a network to access a specific device inside the network.
 Configured on a router.
  Maps a public port to a private IP address and port. 
  So an outside client can access the private-network server through the router, not directly.

## Why It Is Needed
Devices inside a private network use private IP addresses (e.g., 192.168.1.x).
Private IP addresses cannot be accessed directly from the Internet.
Port forwarding tells the router where to send incoming traffic.

- Makes services like websites, SSH, and RDP accessible from the Internet.

## Working

Port Forwarding Rule:

Port 80 → 192.168.1.10

When traffic arrives on Port 80, the router forwards it to 192.168.1.10.

## Example 

Home Network:

Laptop      → 192.168.1.5
Phone       → 192.168.1.20
Cat Server  → 192.168.1.10


Router Public IP:

82.62.51.70

Internet user opens:

82.62.51.70:80

Router checks:

Port 80 → 192.168.1.10

Router forwards the request to the Cat Server.

Internet User
      ↓
Router
      ↓
Cat Server

The cat website loads successfully.

## Key Point
 Router acts as a receptionist.
 Port forwarding tells the router which device should receive incoming traffic.

# Example daigram

<img width="1029" height="844" alt="image" src="https://github.com/user-attachments/assets/38a533eb-7e1e-4b0b-9498-99273ece1dcc" />
<img width="1493" height="614" alt="image" src="https://github.com/user-attachments/assets/cf5f1cf1-6c7e-4ba0-bebc-be22428a9d68" />


### FIREWALL
A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can configure a firewall to permit or deny traffic from entering or exiting a network based on numerous factors

Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is UDP, TCP or both?)
 
 Firewall controls incoming and outgoing network traffic.
 Allows or blocks traffic based on rules.
 
## What It Checks
 Source Address
 Destination Address
 Port Number
 Protocol (TCP/UDP)

## Stateful Firewall (TCP)
 Tracks the entire connection.
 Makes decisions based on connection history.
 More secure but uses more resources.

## Stateless Firewall (UDP)
Checks packets individually.
Uses fixed rules.
Faster but less intelligent.

## Cat Website Example 

Internet User
↓
Firewall
↓
Cat Website Server

Firewall decides:

 Allow Traffic

or

 Block Traffic

## Port Forwarding = Where should traffic go?
## Firewall = Should traffic be allowed?


## PRACTICAL
Deploy the static site attached to this task.

Malicious traffic are marked as the packets in red. The legitimate traffic are the packets marked green. The protocol you need to block is port 80. Configure the firewall to prevent the malicious packets from reaching the web sever 203.0.110.1.


<img width="928" height="803" alt="image" src="https://github.com/user-attachments/assets/463b4abc-25ea-481c-9504-7c4fe8a277ac" />
<img width="879" height="825" alt="image" src="https://github.com/user-attachments/assets/7b923496-7c09-410b-ad4d-40af0aaa5dc4" />
<img width="848" height="787" alt="image" src="https://github.com/user-attachments/assets/5a3ae48e-5ffb-49b2-986e-3fb596337a9a" />
<img width="927" height="836" alt="image" src="https://github.com/user-attachments/assets/414097d5-267b-4734-b3da-22201c50efcb" />


### VPN (Virtual Private Network)
A VPN (Virtual Private Network) creates a secure private tunnel over the Internet between devices.
Think of it as a secret tunnel that only authorized devices can use. 

## Definition
 Creates a secure encrypted tunnel over the Internet.
 VPN = A secure encrypted tunnel that allows private communication over the Internet.
 Allows devices on different networks to communicate securely.
## Why is VPN Used?

A VPN is used to make communication over the Internet secure and private.
Without a VPN, your data travels normally across the Internet.
With a VPN, your data travels through an encrypted tunnel that protects it from others.

## Benefits

### Privacy
Encrypts network traffic.
Protects data from being viewed by others.

### Anonymity
 Helps hide traffic from intermediaries.

### Remote Access
Connects networks in different locations.

## Cat Example 

Without VPN:

Laptop
↓
Public Wi-Fi
↓
Cat Website

With VPN:

Laptop
↓
VPN Tunnel 
↓
Cat Website

Traffic is encrypted and secure.
VPN = Secure tunnel that makes a remote device act like it is inside the private network.

## VPN Technologies

# PPP
Provides authentication and encryption.
Verifies user identity before connection.
Uses keys/certificates for secure communication.
PPP checks:

Username ✔
Password ✔

Then allows the connection.
# Memory
PPP = Authentication + Encryption

## PPTP
Creates VPN tunnels.
Easy setup.
Weak security.

## IPSec
Strong encryption.
More difficult to configure.
Example 
Without IPSec:
Cat Photo
↓
Internet

With IPSec:
Cat Photo 🔒
↓
Internet
Even if someone captures the data, they cannot read it.
Advantages
Strong encryption
Very secure
Disadvantages
Harder to configure
Memory
IPSec = Strong Encryption
## Key Point

VPN = Secure encrypted tunnel between devices over the Internet.

## VLAN (Virtual Local Area Network) 
A VLAN allows a single physical network to be divided into multiple separate virtual networks.
Even though devices use the same switch and Internet connection, they are separated into different groups.
## Ex daigram
<img width="1120" height="780" alt="image" src="https://github.com/user-attachments/assets/381316a8-0042-416f-87b5-097e51c339cb" />


By using VLAN, SALES data stays separate from ACCOUNTING data

## NETWORK STIMULATOR
Deploy the static site attached to this task. And experiment with the network simulator. The simulator will break down every step a packet needs to take to get from point a to b. Try sending a TCP packet from computer1 to computer3 to reveal a flag.

<img width="885" height="893" alt="image" src="https://github.com/user-attachments/assets/3345414a-533f-44b0-99f6-3090ee41d0b2" />

<img width="1077" height="918" alt="image" src="https://github.com/user-attachments/assets/749997d0-afd5-47ce-a57e-cd8e9b0659a4" />

