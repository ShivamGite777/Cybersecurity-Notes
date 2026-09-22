# Nmap 

**Nmap (Network Mapper)** is an open-source network scanning tool used to discover hosts and services on a network.

First released in **1997**.

### Main Uses

* Discover live hosts
* Find open ports
* Identify running services
* Detect service versions
* Perform different types of port scans
* Control scan timing
* Save scan results in different formats

---

## Why Nmap?

Manually checking hundreds or thousands of IP addresses and ports is slow.

Tools like:

* `ping` → can fail if ICMP is blocked by a firewall
* `arp-scan` → generally works only on the local network

Nmap provides a flexible way to automate network and port discovery.

---

## Network Host Discovery

Example network:

```text
192.168.0.1/24
```

A `/24` network contains **256 addresses**.

Usually:

* 1 address → Network address
* 1 address → Broadcast address
* **254 addresses → Usable host addresses**

Nmap can scan the network to find which hosts are **live**.

---

## Port Scanning

After finding a live host, Nmap can check its ports.

Ports identify network services.

Examples:

| Port | Common Service |
| ---- | -------------- |
| 22   | SSH            |
| 25   | SMTP           |
| 53   | DNS            |
| 80   | HTTP           |
| 443  | HTTPS          |

Instead of manually testing ports with tools like `telnet`, Nmap can scan many ports automatically.

---

## Service Detection

Nmap can identify the service running on an open port.

Example:

```text
22/tcp   open   ssh
80/tcp   open   http
```

It can also detect the **version** of the service.

---

## Types of Information Nmap Can Find

```text
Network
   ↓
Live Hosts
   ↓
Open Ports
   ↓
Running Services
   ↓
Service Versions
```

---

## Important Nmap Concepts

### Host Discovery

Find which devices are alive on a network.

### Port Scanning

Check which ports are open, closed, or filtered.

### Service Detection

Identify the service running on an open port.

### Version Detection

Find the version of the detected service.

### Timing

Control how quickly Nmap performs the scan.

### Output

Save or display scan results in different formats.

---

## Basic Example

Scan a single host:

```bash
nmap 192.168.0.10
```

Scan a network:

```bash
nmap 192.168.0.0/24
```

Service/version detection:

```bash
nmap -sV 192.168.0.10
```









# Nmap Host Discovery: Who Is Online?

Host discovery means finding **which devices are currently online/reachable** on a network.

Nmap provides the `-sn` option for this:

```bash
nmap -sn <target>
```

`-sn` = discover live hosts **without scanning their ports/services**.

---

## Specifying Nmap Targets

### 1. IP Range

Scan from `.1` to `.10`:

```bash
nmap -sn 192.168.0.1-10
```

### 2. Subnet

```bash
nmap -sn 192.168.0.1/24
```

`/24` represents:

```text
192.168.0.0 - 192.168.0.255
```

### 3. Hostname

```bash
nmap -sn example.thm
```

---

# Local Network Scanning

A **local network** is a network directly connected to your machine through Wi-Fi or Ethernet.

Example:

```text
Your IP: 192.168.66.89
Network: 192.168.66.0/24
```

Command:

```bash
nmap -sn 192.168.66.0/24
```

Example result:

```text
Nmap scan report for 192.168.66.1
Host is up
MAC Address: ...

Nmap scan report for 192.168.66.88
Host is up
MAC Address: ...

Nmap done: 256 IP addresses (7 hosts up) scanned
```

### Understanding the Output

```text
Host is up
```

→ The device is online/reachable.

```text
MAC Address
```

→ Hardware/network interface address of the device.

Nmap can sometimes identify the **MAC address vendor**, which can give clues about the type/manufacturer of the device.

### How Nmap Finds Local Hosts

For a directly connected network, Nmap can use **ARP requests**.

```text
Nmap → ARP Request → Device
Nmap ← ARP Reply   ← Device
```

If the device responds:

```text
Host is up
```

---

# Remote Network Scanning

A **remote network** is separated from your machine by one or more routers.

Example:

```text
Your machine
192.168.66.89
      |
    Router
      |
    Router
      |
192.168.11.0/24
Target network
```

Command:

```bash
nmap -sn 192.168.11.0/24
```

Example:

```text
Nmap scan report for 192.168.11.1
Host is up

Nmap scan report for 192.168.11.151
Host is up

Nmap scan report for 192.168.11.152
Host is up

Nmap done: 256 IP addresses (5 hosts up) scanned
```

### Why Not ARP?

ARP works on the **local network** and does not cross routers.

For remote hosts, Nmap uses other probes such as:

* ICMP Echo (Ping)
* ICMP Timestamp
* TCP SYN
* TCP ACK

Example:

```text
Nmap → ICMP Echo → Target
Nmap ← ICMP Reply ← Target
```

If the target responds, Nmap knows the host is reachable.

---

# `-PS`, `-PA`, `-PU`

Nmap provides more control over host discovery:

```text
-PS → TCP SYN discovery
-PA → TCP ACK discovery
-PU → UDP discovery
```

These can also be used with specific ports.

---

# List Scan: `-sL`

`-sL` **only lists the targets**. It does not actually scan them.

```bash
nmap -sL 192.168.0.1/24
```

This lists the 256 addresses that Nmap would scan.

Useful for:

```text
Check targets first
      ↓
Then perform the actual scan
```

---

# `-sn` vs `-sL`

| Option           | Purpose                 |
| ---------------- | ----------------------- |
| `-sL`            | List targets only       |
| `-sn`            | Discover live hosts     |
| Normal Nmap scan | Discover ports/services |

---

# Key Takeaways

* **Host discovery** = Find which devices are online.
* `-sn` = Live host discovery without port/service scanning.
* `/24` = 256 IP addresses in the subnet.
* **Local network** → Nmap can use ARP.
* **Remote network** → ARP cannot cross routers, so Nmap uses ICMP/TCP/UDP probes.
* `-sL` = List targets without scanning.
* `-PS` = TCP SYN discovery.
* `-PA` = TCP ACK discovery.
* `-PU` = UDP discovery.
* `-sn` is generally quieter because it doesn't enumerate services.

### Simple Flow

```text
-sL
 ↓
List targets

-sn
 ↓
Find live hosts

Port Scan
 ↓
Find open ports/services
```
