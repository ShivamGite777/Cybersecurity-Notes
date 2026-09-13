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

