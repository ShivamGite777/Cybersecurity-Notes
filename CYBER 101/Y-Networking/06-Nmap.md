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

