### PORT FORWARDING

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
