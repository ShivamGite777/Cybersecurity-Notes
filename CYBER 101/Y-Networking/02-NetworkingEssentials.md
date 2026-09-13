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

**Main idea:**

> ARP translates a known **IP address** into the corresponding **MAC address** so devices on the same local network can communicate.
