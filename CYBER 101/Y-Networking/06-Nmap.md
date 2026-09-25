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

 Nmap sends a TCP SYN packet to the target. It is basically asking, “Can I start a TCP connection with you?”

-PA → TCP ACK discovery
```
### A discovery probe simply means a packet Nmap sends to a target to check whether the target is alive/reachable.

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










# Nmap Port Scanning

After finding live hosts with `-sn`, the next step is to find **which network services are running** on them.

A network service is a process listening for incoming connections on a **TCP or UDP port**.

Common ports:

* `22` → SSH
* `53` → DNS
* `80` → HTTP
* `443` → HTTPS

TCP has **65,535 ports** and UDP also has **65,535 ports**.

---

## 1. TCP Connect Scan — `-sT`

```bash
nmap -sT <target>
```

`-sT` performs a **TCP Connect Scan**.

It tries to complete the full TCP three-way handshake:

```text
SYN → SYN/ACK → ACK
```

If the connection succeeds → **port is open**.

If the port is closed → target usually sends:

```text
RST/ACK
```
<img width="1199" height="715" alt="image" src="https://github.com/user-attachments/assets/828f299e-0d7b-41b7-b4c6-950c2435acfd" />
<img width="950" height="552" alt="image" src="https://github.com/user-attachments/assets/aca2e6cd-5c2a-45fe-8f95-0fa041cc7dd9" />

### Simple meaning

`-sT` = **actually establish a TCP connection to check the port.**

---

## 2. SYN Scan — `-sS`

```bash
sudo nmap -sS <target>
```

`-sS` performs a **TCP SYN Scan**.

It only starts the TCP handshake:

```text
SYN → SYN/ACK
```

Then Nmap sends:

```text
RST
```
<img width="1199" height="715" alt="image" src="https://github.com/user-attachments/assets/8eb5ed15-02bc-4bd8-91d5-414fb5632fd6" />


instead of completing the connection.

### Simple meaning

`-sS` = **send SYN, check the response, don't complete the connection.**

It is also called a **half-open scan** and is relatively stealthier than `-sT`.

---

## `-sT` vs `-sS`

| Command | What it does                     |
| ------- | -------------------------------- |
| `-sT`   | Completes TCP connection         |
| `-sS`   | Does not complete TCP connection |

### Easy memory

```text
-sT → Complete connection
-sS → SYN and stop
```

---

## 3. UDP Scan — `-sU`

```bash
sudo nmap -sU <target>
```

`-sU` scans **UDP ports**.

UDP does not use the TCP three-way handshake.

Nmap sends UDP packets and checks the response.

For example, if a UDP port is closed, the target may respond with:

```text
ICMP Destination Unreachable - Port Unreachable
```
<img width="1220" height="735" alt="image" src="https://github.com/user-attachments/assets/0535e680-09d0-4967-8669-6174e1a53d4f" />


### Common UDP services

* `53` → DNS
* `67/68` → DHCP
* `123` → NTP
* `161` → SNMP

### Simple meaning

`-sU` = **check which UDP ports are open.**

---

# 4. Fast Scan — `-F`

```bash
nmap -F <target>
```

`-F` means **Fast mode**.

It scans the **100 most common ports** instead of Nmap's default 1,000 common ports.

### Simple meaning

```text
-F → Scan fewer common ports → Faster
```

---

# 5. Scan Specific Ports — `-p`

You can choose exactly which ports Nmap scans.

### Scan ports 10 to 1024

```bash
nmap -p10-1024 <target>
```

This scans:

```text
10, 11, 12, ... 1024
```

### Scan ports 1 to 25

```bash
nmap -p-25 <target>
```

### Scan all ports

```bash
nmap -p- <target>
```

`-p-` means:

```text
1 → 65535
```

It is equivalent to:

```bash
nmap -p1-65535 <target>
```

### Scan well-known ports

```bash
nmap -p1-1023 <target>
```

Ports `1–1023` are commonly called **well-known ports**.

---

# Quick Command Table

| Option      | Meaning               |
| ----------- | --------------------- |
| `-sT`       | TCP Connect Scan      |
| `-sS`       | TCP SYN Scan          |
| `-sU`       | UDP Scan              |
| `-F`        | Scan 100 common ports |
| `-p10-1024` | Scan ports 10–1024    |
| `-p1-1023`  | Scan well-known ports |
| `-p-25`     | Scan ports 1–25       |
| `-p-`       | Scan all 65,535 ports |

---

# Nmap Flow

```text
-sn
 ↓
Find live hosts

-sT / -sS
 ↓
Find open TCP ports

-sU
 ↓
Find open UDP ports

-p-
 ↓
Scan all ports
```

### Remember

**Host discovery** → `-sn`
**TCP Connect** → `-sT`
**TCP SYN** → `-sS`
**UDP** → `-sU`
**Fast scan** → `-F`
**Specific/all ports** → `-p`





# HANDS-ON LAB


## How many TCP ports are open on the target system at 10.48.149.131?
<img width="952" height="560" alt="image" src="https://github.com/user-attachments/assets/03eb1461-64aa-4233-9317-ffd06961a8c6" />


## Find the listening web server on 10.48.149.131 and access it with your browser. What is the flag that appears on its main page?
## Find Web Server and Flag

## Find Web Server and Flag

Target:

```bash
10.48.149.131
```

First scan the target for open ports:

```bash
nmap 10.48.149.131
```

From the scan, we found:

```text
8008/tcp  open  http
```

This means a **web server is running on port 8008**.

Open it in a browser:

```text
http://10.48.149.131:8008
```

The flag displayed on the **main webpage** is the answer.

<img width="982" height="852" alt="image" src="https://github.com/user-attachments/assets/c8c60736-8a8d-497c-a6e2-fe3bedf65bb5" />




# Nmap - OS Detection, Version Detection & Scan Options

Nmap can do more than just find open ports. It can also try to identify the **Operating System**, **service versions**, and other information about a target.

---

## 1. OS Detection

Nmap can try to identify which operating system is running on a target.

```bash
sudo nmap -sS -O 192.168.124.211
```

### Meaning

* `sudo` → run with administrator/root permission
* `nmap` → network scanning tool
* `-sS` → TCP SYN scan
* `-O` → OS detection
* `192.168.124.211` → target IP address

Example output:

```text
Running: Linux 4.X|5.X
OS details: Linux 4.15 - 5.8
```

Nmap checks different network characteristics and makes an **educated guess** about the OS.
<img width="951" height="687" alt="WhatsApp Image 2026-09-25 at 9 44 20 AM" src="https://github.com/user-attachments/assets/9cd14100-82c8-4a80-82a1-1684398fb904" />


### Important

OS detection is **not always 100% accurate**.

For example, Nmap may detect:

```text
Linux 4.15 - 5.8
```

while the actual system could be running:

```text
Linux 5.15
```

So OS detection should be treated as an estimate.

---

## 2. Service and Version Detection

Finding an open port tells us that something is listening, but it doesn't always tell us exactly **which software or version** is running.

For this, use `-sV`.

```bash
sudo nmap -sS -sV 192.168.124.211
```

### Meaning

* `sudo` → administrator/root permission
* `nmap` → scanning tool
* `-sS` → TCP SYN scan
* `-sV` → service and version detection
* `192.168.124.211` → target IP

Example:

```text
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.10
```

Here we know:

* `22/tcp` → TCP port 22
* `open` → port is accepting connections
* `ssh` → service is SSH
* `OpenSSH 8.9p1` → detected software/version

### Purpose of -sV

It gives more information about the software running on open ports.

For example:

```text
80/tcp open http Apache 2.4.57
```

Now we know the target is running an Apache web server and Nmap detected its version.

---

## 3. Aggressive Scan

Instead of separately using multiple detection options, Nmap provides `-A`.

```bash
sudo nmap -A 192.168.124.211
```

### Meaning

* `-A` → enables several advanced detection features
* Target IP → system you want to scan

`-A` includes:

* OS detection
* Service/version detection
* Script scanning
* Traceroute
* Other advanced detection features

For example:

```bash
sudo nmap -O -sV 192.168.124.211
```

can be replaced with:

```bash
sudo nmap -A 192.168.124.211
```

### Imp

```text
-A = More information about the target
```

---

## 4. Forcing the Scan with `-Pn`

Normally Nmap first performs **host discovery** to check whether the target is online.

If the target doesn't respond to those discovery probes, Nmap may assume:

```text
Host is down
```

and may not perform the normal port scan.

Use `-Pn` to tell Nmap to treat the target as online.

```bash
sudo nmap -Pn 192.168.124.211
```

### Meaning

* `sudo` → administrator permission
* `nmap` → scanning tool
* `-Pn` → skip host discovery and scan the target anyway
* IP → target address

### Flow

Without `-Pn`:

```text
Is host online?
       ↓
No response
       ↓
Host may be marked down
       ↓
Port scan may not happen
```

With `-Pn`:

```text
Don't check host discovery
       ↓
Assume host is online
       ↓
Perform the scan
```

---

## 5. Combining Options

Nmap options can be combined.

Example:

```bash
sudo nmap -sS -O -sV 192.168.124.211
```

This performs:

* `-sS` → SYN scan
* `-O` → OS detection
* `-sV` → service/version detection

Or use:

```bash
sudo nmap -A 192.168.124.211
```

for multiple advanced detection features.

---

## 6. Important Difference

### `-O`

Answers:

> **What OS might be running?**

Example:

```text
Linux 4.X|5.X
```

### `-sV`

Answers:

> **What service/software and version is running?**

Example:

```text
OpenSSH 8.9p1
```

### `-A`

Answers several questions:

> **What OS, services, versions, routes and other information can Nmap discover?**

### `-Pn`

Answers:

> **Can I scan this host even if host discovery gets no response?**


## Useful Commands

### OS detection

```bash
sudo nmap -sS -O TARGET
```

### Service/version detection

```bash
sudo nmap -sS -sV TARGET
```

### Advanced scan

```bash
sudo nmap -A TARGET
```

### Scan a host that appears down

```bash
sudo nmap -Pn TARGET
```

### Combine OS + version detection

```bash
sudo nmap -sS -O -sV TARGET
```

---

## TryHackMe Question

**Question:**

> What is the name and detected version of the web server running on `10.49.187.254`?

Run:

```bash
sudo nmap -sV 10.49.187.254
```

Then check the output:

```text
PORT   STATE   SERVICE   VERSION
```

Look for the **web service**, usually `http` or `https`.

The **SERVICE** column gives the service name and the **VERSION** column gives the detected software/version.

### Example

```text
80/tcp   open   http   Apache httpd 2.4.57
```

Answer format:

```text
Apache httpd 2.4.57
```
<img width="957" height="650" alt="image" src="https://github.com/user-attachments/assets/f1cfb7fa-4e8e-4333-98a4-19911d8ce9e4" />






# Nmap - Scan Timing & Performance

Nmap provides options to control **how fast or slow a scan runs**.

Scan speed can affect how many packets are sent and how quickly the target is scanned.

---

## 1. Timing Templates

Nmap has **6 timing templates**:

| Option | Name       | Speed     |
| ------ | ---------- | --------- |
| `-T0`  | paranoid   | Very slow |
| `-T1`  | sneaky     | Slow      |
| `-T2`  | polite     | Slower    |
| `-T3`  | normal     | Default   |
| `-T4`  | aggressive | Fast      |
| `-T5`  | insane     | Very fast |


### T0
<img width="1200" height="420" alt="image" src="https://github.com/user-attachments/assets/34815fcf-89df-4e05-a213-e9bdb20545b3" />
### T1
<img width="1200" height="425" alt="image" src="https://github.com/user-attachments/assets/f0a574b7-44f2-4abd-8f7b-6ac3bc489001" />
### T2
<img width="1200" height="425" alt="image" src="https://github.com/user-attachments/assets/af0af70f-d88f-43ca-a90b-a034c74cf4c7" />
### T3
<img width="1200" height="425" alt="image" src="https://github.com/user-attachments/assets/3f0589a6-c8e7-4dd0-8895-10f55f5033b1" />
### T4


### Example

```bash
sudo nmap -sS -T4 TARGET
```

### Meaning

* `sudo` → run with administrator/root permission
* `nmap` → network scanning tool
* `-sS` → TCP SYN scan
* `-T4` → use aggressive timing
* `TARGET` → target IP/hostname

The same timing can also be written using its name:

```bash
sudo nmap -sS -T aggressive TARGET
```

So:

```text
-T4 = -T aggressive
```

---

## 2. Why Control Scan Speed?

A faster scan sends packets more quickly.

A slower scan adds more delay between packets.

```text
T0 → Very slow
T1 → Slow
T2 → Slower
T3 → Normal
T4 → Fast
T5 → Very fast
```

The actual scan time depends on the **network, target, and packet loss**.

---

## 3. Fast Scan Example

```bash
sudo nmap -sS -T4 -F TARGET
```

### Meaning

* `-sS` → SYN scan
* `-T4` → aggressive timing
* `-F` → fast scan (scan fewer common ports)
* `TARGET` → target system

---

## 4. Parallelism

Nmap can control how many probes are active at the same time.

```bash
sudo nmap --min-parallelism 10 --max-parallelism 50 TARGET
```

### Meaning

* `--min-parallelism 10` → minimum 10 probes at once
* `--max-parallelism 50` → maximum 50 probes at once

Nmap normally adjusts this automatically depending on network conditions.

---

## 5. Packet Rate

Nmap can control the number of packets sent per second.

```bash
sudo nmap --min-rate 100 --max-rate 500 TARGET
```

### Meaning

* `--min-rate 100` → minimum 100 packets/second
* `--max-rate 500` → maximum 500 packets/second

These rates apply to the **whole scan**, not just one host.

---

## 6. Host Timeout

You can set the maximum time Nmap should wait for a target.

```bash
sudo nmap --host-timeout 30s TARGET
```

### Meaning

* `--host-timeout` → maximum time to wait for a host
* `30s` → 30 seconds
* `TARGET` → target system

Useful when a host or network connection is very slow.

---

## Summary

| Option              | Meaning                         |
| ------------------- | ------------------------------- |
| `-T0`               | Paranoid                        |
| `-T1`               | Sneaky                          |
| `-T2`               | Polite                          |
| `-T3`               | Normal/default                  |
| `-T4`               | Aggressive                      |
| `-T5`               | Insane                          |
| `--min-parallelism` | Minimum parallel probes         |
| `--max-parallelism` | Maximum parallel probes         |
| `--min-rate`        | Minimum packets/second          |
| `--max-rate`        | Maximum packets/second          |
| `--host-timeout`    | Maximum time to wait for a host |

