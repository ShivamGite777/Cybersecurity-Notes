### DHCP (Dynamic Host Configuration Protocol)

DHCP automatically provides network configuration to devices when they connect to a network.

### DHCP Provides

* **IP Address + Subnet Mask**
* **Gateway / Router**
* **DNS Server**

### Why DHCP?

* Automatically configures devices
* Saves manual configuration
* Prevents IP address conflicts
* Commonly used by laptops and smartphones

### DHCP Ports

```text
Server → UDP 67
Client → UDP 68
```

## DORA Process

DHCP uses **4 steps**:

```text
Discover → Offer → Request → ACK
```

1. **Discover** → Client searches for a DHCP server.
2. **Offer** → Server offers an available IP.
3. **Request** → Client requests the offered IP.
4. **ACK** → Server confirms the IP assignment.

### Initial DHCP Communication

```text
Source IP      → 0.0.0.0
Destination IP → 255.255.255.255
```

The client uses `0.0.0.0` because it does not have an IP yet.
`255.255.255.255` is the broadcast address.

### Example

```text
DHCP Server → 192.168.66.1
Client gets → 192.168.66.133
```























### ARP (Address Resolution Protocol)
**ARP** is used to find the **MAC address of a device when its IP address is known**.

```text
IP Address → MAC Address
```

### Example

Suppose two computers are on the same network:

```text
Computer A
IP  : 192.168.66.89
MAC : AA:AA:AA

Computer B
IP  : 192.168.66.1
MAC : BB:BB:BB
``` 

Computer A wants to send data to Computer B.

A already knows:

```text
IP = 192.168.66.1
```

But it does not know B's MAC address.

So it uses **ARP**.

---

## ARP Request

Computer A broadcasts:

```text
"Who has 192.168.66.1?"
```

The request is sent to the broadcast MAC address:

```text
ff:ff:ff:ff:ff:ff
```

This means the request is sent to all devices on the local network.

---

## ARP Reply

Computer B recognizes that `192.168.66.1` is its IP and replies:

```text
"192.168.66.1 is at BB:BB:BB"
```

Now Computer A knows:

```text
IP Address       MAC Address
192.168.66.1  →  BB:BB:BB
```

Computer A can now send Ethernet frames to Computer B.

---

## ARP Packet Example

```text
1. Who has 192.168.66.1?
   ↓
2. 192.168.66.1 is at 44:df:65:d8:fe:6c
```

### Simple Flow

```text
Computer A
192.168.66.89
      |
      | ARP Request
      | "Who has 192.168.66.1?"
      ↓
Computer B
192.168.66.1
      |
      | ARP Reply
      | "My MAC is BB:BB:BB"
      ↓
MAC address is learned
```

## Key Points

* **IP Address** → Layer 3 addressing
* **MAC Address** → Layer 2 addressing
* **ARP** → Finds MAC address from an IP address
* **ARP Request** → Broadcast
* **Broadcast MAC** → `ff:ff:ff:ff:ff:ff`
* **ARP Reply** → Contains the target's MAC address

### Remember

```text
DHCP → Gives/configures IP address
ARP  → Finds MAC address for that IP
```
<img width="1000" height="580" alt="image" src="https://github.com/user-attachments/assets/20dafec9-9a9e-4e07-a279-1e3dea6a94ac" />


**Main idea:**

> ARP translates a known **IP address** into the corresponding **MAC address** so devices on the same local network can communicate.
...
>
> ```
>
>
>
> # ICMP (Internet Control Message Protocol)

ICMP is mainly used for **network diagnostics and error reporting**.

Two common commands that use ICMP are:

* `ping`
* `traceroute` / `tracert`

---

## 1. Ping

`ping` is used to:

* Check whether a target is reachable
* Test network connectivity
* Measure **Round-Trip Time (RTT)**
* Check packet loss

### How Ping Works

The computer sends an **ICMP Echo Request** to the target.

```text
Your PC
   |
   | ICMP Echo Request
   | Type 8
   ↓
Target
```

The target responds with an **ICMP Echo Reply**.

```text
Target
   |
   | ICMP Echo Reply
   | Type 0
   ↓
Your PC
```

### ICMP Types

| Message      | ICMP Type |
| ------------ | --------: |
| Echo Request |         8 |
| Echo Reply   |         0 |

### Example

```bash
ping 192.168.11.1 -c 4
```

`-c 4` means **send 4 ping packets and stop**.

Example output:

```text
4 packets transmitted, 4 received, 0% packet loss
```

This means all 4 packets received a reply.

### RTT

**RTT (Round-Trip Time)** is the time required for a packet to travel from the source to the target and for the reply to return.

Example:

```text
Your PC → Server → Your PC
          10 ms
```

---

## 2. Why Ping Can Fail

A ping may fail because:

* Target system is offline
* Firewall blocks ICMP
* Network connection has a problem
* Packets are lost

So, no ping reply does **not always mean the target is offline**.

---

# 3. Traceroute

`traceroute` is used to discover the **route/hops** between your computer and a target.

Linux / UNIX:

```bash
traceroute example.com
```

Windows:

```cmd
tracert example.com
```

It shows the routers through which the packet travels.

Example:

```text
Your PC
   ↓
Router 1
   ↓
Router 2
   ↓
Router 3
   ↓
Destination
```

---

## 4. TTL (Time To Live)

Traceroute uses the **TTL field** in the IP header.

TTL indicates how many router hops a packet can survive.

Each router decreases TTL by **1**.

Example:

```text
TTL = 3

Router 1 → TTL = 2
Router 2 → TTL = 1
Router 3 → TTL = 0
```

When TTL becomes `0`, the router drops the packet and sends an:

**ICMP Time Exceeded message → Type 11**

---

## 5. How Traceroute Finds Routers

Traceroute gradually increases the TTL value.
**TTL determines the maximum number of routers (hops) a packet can pass through.**
### TTL = 1

```text
Your PC → Router 1
             ↓
          TTL = 0
             ↓
    ICMP Time Exceeded
```

Traceroute learns:

```text
Hop 1 = Router 1
```

### TTL = 2

```text
Your PC → Router 1 → Router 2
                       ↓
                    TTL = 0
                       ↓
              ICMP Time Exceeded
```

Traceroute learns:

```text
Hop 2 = Router 2
```

It continues until it reaches the destination.

---

## 6. `* * *` in Traceroute

Example:

```text
5  * * *
6  * * *
7  * * *
```

`* * *` means **no response was received** from that hop.

Possible reasons:

* Firewall blocked the response
* Router does not respond to traceroute
* Packet was lost
* ICMP messages were filtered

It does **not necessarily mean the router does not exist**.

---

## 7. Example Traceroute

```text
1  192.168.66.1
2  192.168.11.1
3  100.104.0.1
4  10.149.1.45
5  * * *
6  * * *
7  * * *
8  172.16.48.1
...
16  93.184.215.14
```

This shows the different routers/hops between the source and destination.

The final IP:

```text
93.184.215.14
```

is the destination.

---

## 8. Route Can Change

The route to a destination may change when traceroute is run again.

For example:

```text
Run 1:
PC → Router A → Router B → Server

Run 2:
PC → Router A → Router C → Router D → Server
```

This can happen because networks may have multiple possible paths.

---

## Quick Revision

```text
ICMP → Network diagnostics and error reporting

Ping
→ Checks connectivity
→ Measures RTT
→ Echo Request = Type 8
→ Echo Reply = Type 0

Traceroute
→ Finds route/hops
→ Uses TTL
→ Each router decreases TTL by 1
→ TTL = 0 → Packet dropped
→ ICMP Time Exceeded = Type 11

Linux → traceroute
Windows → tracert

* * * → No response from that hop
```





# Using the example images above, how many bytes were sent in the echo (ping) request?




<img width="892" height="665" alt="image" src="https://github.com/user-attachments/assets/89a6308c-108f-4153-813e-2be7b2f45d42" />







# Routing Protocols

Routing protocols are used by routers to **learn routes and choose paths** for sending data to a destination.

---

## 1. OSPF

**OSPF = Open Shortest Path First**

OSPF allows routers to share information about the **network topology**.

Each router builds a map of the network and uses it to find the **best path** to a destination.

### Example

```text
PC → Router A → Router B → Server
PC → Router C → Router D → Server
```

OSPF compares the available paths and selects the best one.

**Remember:**

```text
OSPF → Network Map → Best Path
```

---

## 2. EIGRP

**EIGRP = Enhanced Interior Gateway Routing Protocol**

EIGRP was developed by **Cisco**.

Routers share information about:

* Networks they can reach
* Bandwidth
* Delay
* Route cost

It uses this information to choose an **efficient route**.

**Remember:**

```text
EIGRP → Cisco → Efficient Route
```

---

## 3. BGP

**BGP = Border Gateway Protocol**

BGP is the main routing protocol used on the **Internet**.

It allows different networks, such as **ISPs and large organizations**, to exchange routing information.

### Example

```text
Network A
    ↓
   BGP
    ↓
Network B
    ↓
   BGP
    ↓
Network C
```

BGP helps data travel between different networks.

**Remember:**

```text
BGP → Internet → Network to Network
```

---

## 4. RIP

**RIP = Routing Information Protocol**

RIP is a simple routing protocol that mainly uses **hop count**.

A **hop** means passing through one router.

### Example

```text
Path A:
PC → R1 → R2 → Server
     2 hops

Path B:
PC → R3 → R4 → R5 → Server
     3 hops
```

RIP chooses **Path A** because it has fewer hops.

**Remember:**

```text
RIP → Count Hops → Fewer Hops
```

---

## 

| Protocol  | Main Idea                       |
| --------- | ------------------------------- |
| **OSPF**  | Network map and best path       |
| **EIGRP** | Cisco, bandwidth and delay      |
| **BGP**   | Internet and different networks |
| **RIP**   | Fewest hops                     |










# NAT (Network Address Translation)

## What is NAT?

**NAT (Network Address Translation)** is a technique that allows multiple devices with **private IP addresses** to access the Internet using a **single public IP address**.

---

## Why is NAT Needed?

IPv4 provides around **4.3 billion IP addresses**. With the huge increase in Internet-connected devices such as:

* Computers
* Smartphones
* Security cameras
* Smart TVs
* IoT devices
* Smart appliances

the available IPv4 addresses started running out.

NAT helps reduce the need for public IPv4 addresses.

---

## How NAT Works

The main idea of NAT is:

```text
Many Private IP Addresses
          ↓
      NAT Router
          ↓
   One Public IP Address
          ↓
       Internet
```

### Example

Suppose a company has 20 computers:

```text
PC 1  → 192.168.1.10
PC 2  → 192.168.1.11
PC 3  → 192.168.1.12
...
PC 20 → 192.168.1.29
```

These are **private IP addresses**.

Instead of assigning 20 public IP addresses, the company can use one public IP:

```text
Public IP → 212.3.4.5
```

All 20 computers can access the Internet through this single public IP.

---

## Private IP vs Public IP

### Private IP

Private IP addresses are used inside local networks.

Example:

```text
192.168.0.129
```

### Public IP

A public IP address is used to communicate with devices on the Internet.

Example:

```text
212.3.4.5
```

So:

```text
Laptop
192.168.0.129
      ↓
 NAT Router
212.3.4.5
      ↓
   Internet
```

---

# NAT Translation

NAT does not only translate the IP address. It also keeps track of the **port number**.

Suppose a laptop starts a connection:

```text
Private IP:   192.168.0.129
Source Port:  15401
```

The NAT router translates it to:

```text
Public IP:    212.3.4.5
Public Port:  19273
```

Therefore, the web server sees:

```text
212.3.4.5:19273
```

instead of:

```text
192.168.0.129:15401
```

---

## NAT Translation Table

The NAT router maintains a table to keep track of these connections.

| Internal IP   | Internal Port | External IP | External Port |
| ------------- | ------------: | ----------- | ------------: |
| 192.168.0.129 |         15401 | 212.3.4.5   |         19273 |

This means:

```text
192.168.0.129:15401
          ↓
212.3.4.5:19273
```

---

# How the Reply Reaches the Correct Device

When the web server sends a response, it sends it to:

```text
212.3.4.5:19273
```

The NAT router checks its translation table and finds:

```text
212.3.4.5:19273
          ↓
192.168.0.129:15401
```

The router then forwards the response to the correct laptop.

### Complete Flow

```text
Laptop
192.168.0.129:15401
        ↓
      NAT
        ↓
212.3.4.5:19273
        ↓
     Internet
        ↓
   Web Server
        ↓
212.3.4.5:19273
        ↓
      NAT
        ↓
192.168.0.129:15401
        ↓
      Laptop
```

---

# Multiple Devices Using One Public IP

Different devices can use the same public IP because NAT tracks their connections using different port numbers.

Example:

```text
Phone:
192.168.0.130:15402
        ↓
212.3.4.5:19274

Laptop:
192.168.0.129:15401
        ↓
212.3.4.5:19273

Smart TV:
192.168.0.131:15403
        ↓
212.3.4.5:19275
```

The **public IP is the same**, but the **port numbers are different**.

This allows the NAT router to identify which internal device belongs to each connection.

---

## Real-Life Example

A home network may contain:

```text
📱 Phone  → 192.168.1.10
💻 Laptop → 192.168.1.11
📺 TV     → 192.168.1.12
```

All of them can access the Internet through the same public IP:

```text
             Internet
                ↑
        Public IP: 212.3.4.5
                ↑
           Wi-Fi Router
          ↙      ↓      ↘
       Phone   Laptop    TV
       .10      .11      .12
```

---

# Key Points

* **NAT = Network Address Translation**
* NAT translates **private IP addresses** into a **public IP address**.
* Multiple devices can share one public IP.
* NAT routers maintain a **translation table**.
* NAT tracks **IP addresses and port numbers**.
* Private IPs are used inside local networks.
* Public IPs are used for Internet communication.
* NAT helps conserve the limited IPv4 address space.

## 
```text
NAT
↓
Many Private IPs
↓
One Public IP
↓
Internet
```

**Main idea:**

> NAT allows many devices with private IP addresses to access the Internet using a single public IP address by translating IP addresses and port numbers.
