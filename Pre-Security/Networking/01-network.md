
# Networking

## Definition
Networking is the process of connecting two or more computers/devices so they can communicate and share data, resources, and services.

Examples:
- Sending messages
- Browsing websites
-  Sharing files

# what is internet
## Definition
The Internet is a global network of interconnected computers and devices that communicate and share information worldwide using communication protocols.

# types of network
1.public network
2.private network

# world wibe web 
created by tim berners lee

# devivce on a network
ip add
IP address can be used as a way of identifying a host on a network for a period of time
there are 4 octet in ip add 
limit (o-255)
Example:
192.168.1.10

192 → First octet
168 → Second octet
1 → Third octet
10 → Fourth octet

# Versions of IP Address
## 1.IPv4 

- Most commonly used version
- Uses a 32-bit address
- Divided into four octets
- Written in decimal format

Example:
192.168.1.1

Features:
- Supports about 4.3 billion addresses
- Easy to read and use
- Limited number of addresses

SO OVERCOME THIS PROBLEM THEY INTRODUCE 
# 2.IPv6
128 bit 
 written in hexadecimal
 very large no of address


## MAC 
media access control
permanent address of device
mac is a machine identity
Example: 00:1A:2B:3C:4D:5E 
first six characters represent the company that made the network interface and the last six is a unique number.

Practical

The interactive labs simulate a hotel Wi-Fi network where you have to pay for the service. You'll note that the router is not allowing Bob's packets ( blue) to the TryHackMe website and is placing them in the bin, but Alice's packets (green) are going through fine because she has paid for Wi-Fi. Try changing Bob's MAC address to the same as Alice's to see what happens.
ans - we change mac address of alice - same as bob
<img width="917" height="908" alt="image" src="https://github.com/user-attachments/assets/4f9a3038-4ebf-46aa-86dc-d1c30ae010bd" />


## ping(internet control message protocol)
ICMP (Internet Control Message Protocol) packets to determine the performance of a connection between devices, for example, if the connection exists or is reliable.
## How ICMP Works
When a device sends data and a problem occurs, ICMP sends a message back to inform the sender.
Example:
Destination unreachable
Request timed out
Network unreachable
# ping uses ICMP messages to test connectivity between devices.
ex- ping google.com
Ping sends:
ICMP Echo Request
Receives ICMP Echo Reply
protocol use by ping - icmp
#syntax
ping -c 4 8.8.8.8
-c = count option
4 = number of packets to send
we call them x times bec if they fail in 1 time thats why we call them many times

ping 8.8.8.8
Without -c 4, ping may continue running until you stop it manually Ctrl + Cc
