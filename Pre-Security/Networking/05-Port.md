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
