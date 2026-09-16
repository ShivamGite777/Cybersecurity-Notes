<img width="812" height="481" alt="image" src="https://github.com/user-attachments/assets/c4800d26-7e41-4de3-977c-855021afbb39" />### Tcpdump

`tcpdump` is a command-line tool used to **capture and view network packets**.

It is mainly used for:

* Network troubleshooting
* Packet analysis
* Learning protocols
* Security investigation

---

## 1. Check Network Interfaces

```bash
ip a s
```

# Meaning

* `ip` → Linux command for network information
* `a` → address
* `s` → show

It shows the network interfaces available on the system.

Example:

```text
lo
ens5
```

* `lo` → loopback interface
* `ens5` → network interface

---

## 2. Capture Packets

```bash
sudo tcpdump -i ens5
```

# Meaning
# Start capturing network packets coming through the ens5 network interface.
# sudo = Run the command as administrator
* `tcpdump` → packet capture tool
* `-i` → interface
* `ens5` → ens5 is simply the name of a network interface (network card) on a Linux machine.

**Purpose:** Captures packets coming through `ens5`.

---

## 3. Capture from All Interfaces

```bash
sudo tcpdump -i any
```

# Meaning

* `-i` → interface
* `any` → all available interfaces

**Purpose:** Captures packets from all network interfaces.

---

## 4. Limit Packet Count

```bash
sudo tcpdump -i ens5 -c 5
```

# Meaning

* `-i` → choose interface
* `ens5` → network interface
* `-c` → count
* `5` → number of packets

**Purpose:** Captures only **5 packets** and then stops.

Without `-c`, press:

```text
Ctrl + C
```

to stop the capture.

---

## 5. Show Numeric IP Addresses

```bash
sudo tcpdump -i ens5 -n
```

# Meaning

* `-n` → don't resolve IP addresses
* IP addresses are shown directly

Example:

```text
10.10.117.2
```

instead of a hostname.

---

## 6. Show Numeric IPs and Ports

```bash
sudo tcpdump -i ens5 -nn
```

# Meaning

* `-n` → don't resolve IP addresses
* second `n` → don't resolve port/service names

So `-nn` shows:

```text
IP address + port number
```

Example:

```text
10.10.117.2.22
```

Here:

* `10.10.117.2` → IP address
* `22` → port number

---

## 7. Save Packets to a File

```bash
sudo tcpdump -i ens5 -w data.pcap
```

# Meaning

* `sudo` → run with administrator permission
* `tcpdump` → packet capture tool
* `-i` → interface
* `ens5` → interface name
* `-w` → write/save
* `data.pcap` → output file

**Purpose:** Captures packets and saves them in `data.pcap`.

Stop with:

```text
Ctrl + C
```

`.pcap` is a common format for storing captured network packets.

---

## 8. Read a Saved Capture

```bash
sudo tcpdump -r data.pcap
```

## Meaning

* `tcpdump` → packet analysis tool
* `-r` → read
* `data.pcap` → capture file

**Purpose:** Reads packets from an existing `.pcap` file.

For numeric IPs and ports:

```bash
sudo tcpdump -r data.pcap -nn
```

---

## 9. Verbose Output

```bash
sudo tcpdump -i ens5 -v
```

# Meaning

* `-v` → verbose
* Verbose means **show more details**

More levels:

```text
-v
-vv
-vvv
```

`-vv` gives more details than `-v`.

`-vvv` gives even more details.

---

## 10. Common Examples

# Capture 50 packets

```bash
sudo tcpdump -i eth0 -c 50 -v
```

* `eth0` → Ethernet interface
* `-c 50` → capture 50 packets
* `-v` → show more details

---

## Capture Wi-Fi traffic and save it

```bash
sudo tcpdump -i wlo1 -w data.pcap
```

* `wlo1` → Wi-Fi interface
* `-w` → save packets
* `data.pcap` → saved capture file

---

## Capture from all interfaces

```bash
sudo tcpdump -i any -nn
```

* `any` → all interfaces
* `-nn` → don't resolve IPs or ports

---

## Table

| Option | Meaning                    |
| ------ | -------------------------- |
| `-i`   | Select interface           |
| `-c`   | Packet count               |
| `-w`   | Write/save packets         |
| `-r`   | Read packets               |
| `-n`   | Don't resolve IP addresses |
| `-nn`  | Don't resolve IPs or ports |
| `-v`   | Show more details          |
| `-vv`  | More verbose               |
| `-vvv` | Even more verbose          |






















### Tcpdump Filtering — Host and Port

`tcpdump` can capture a large number of packets. Filtering helps us capture only the traffic we are interested in.

---

## 1. Filtering by Host

Use `host` when you want to capture packets **to or from** a specific IP address or hostname.

## Command

```bash
sudo tcpdump host example.com -w http.pcap
```
<img width="812" height="481" alt="image" src="https://github.com/user-attachments/assets/08f66b82-30f3-459f-9873-f53c30882b5c" />


# Explanation

* `sudo` → Run with root privileges.
* `tcpdump` → Capture network packets.
* `host example.com` → Capture packets to or from `example.com`.
* `-w http.pcap` → Save the captured packets to `http.pcap`.

### Source Host

```bash
sudo tcpdump src host 192.168.1.10
```

Captures packets **coming from** `192.168.1.10`.

### Destination Host

```bash
sudo tcpdump dst host 192.168.1.10
```

Captures packets **going to** `192.168.1.10`.

### IDEA

```text
host       → TO or FROM
src host   → FROM
dst host   → TO
```

---

### Filtering by Port

Port filtering allows `tcpdump` to capture only packets related to a specific **port number** instead of showing all network traffic.

For example, **DNS commonly uses port 53**.

---

## 1. Filter by Port

### Command

```bash
sudo tcpdump -i ens5 port 53 -n
```

### Explanation

* `sudo` → Run with root privileges.
* `tcpdump` → Capture network packets.
* `-i ens5` → Capture packets on the `ens5` network interface.
* `port 53` → Capture packets sent to or received from port `53`.
* `-n` → Display IP addresses without resolving them to hostnames.

### In Simple Words

```text
Capture all traffic involving port 53
on the ens5 interface.
```

---

## 2. Why Port 53?

DNS commonly uses:

```text
UDP → Port 53
TCP → Port 53
```

Therefore:

```bash
sudo tcpdump -i ens5 port 53 -n
```

can capture DNS-related traffic using port `53`.

---

## 3. DNS Query Example

Example output:

```text
192.168.139.132.47902 > 192.168.139.2.53: A? example.org.
192.168.139.132.47902 > 192.168.139.2.53: AAAA? example.org.
```

# A Record

```text
A? example.org
```

Requests the **IPv4 address** of `example.org`.

Example response:

```text
A 93.184.215.14
```

# AAAA Record

```text
AAAA? example.org
```

Requests the **IPv6 address** of `example.org`.

Example response:

```text
AAAA 2606:2800:21f:cb07:6820:80da:af6b:8b2c
```

---

## 4. Source Port Filtering

Use `src port` to capture packets **coming from** a specific port.

## Command

```bash
sudo tcpdump -i ens5 src port 53 -n
```

This captures packets where the **source port is 53**.

Example:

```text
192.168.139.2:53 → 192.168.139.132:47902
```

Here, `53` is the source port.

---

## 5. Destination Port Filtering

Use `dst port` to capture packets **going to** a specific port.

## Command

```bash
sudo tcpdump -i ens5 dst port 53 -n
```

This captures packets where the **destination port is 53**.

Example:

```text
192.168.139.132:47902 → 192.168.139.2:53
```

Here, `53` is the destination port.

---

## Reference

| Command                          | Meaning                    |
| -------------------------------- | -------------------------- |
| `tcpdump -i ens5 port 53 -n`     | Traffic to or from port 53 |
| `tcpdump -i ens5 src port 53 -n` | Traffic from port 53       |
| `tcpdump -i ens5 dst port 53 -n` | Traffic to port 53         |


```

**Port filtering helps reduce the amount of traffic displayed by focusing only on a specific network service.**









# Tcpdump – Protocol Filtering, Logical Operators & PCAP Analysis

## 1. Filtering by Protocol

`tcpdump` can filter packets based on the network protocol.

### Common Protocol Filters

```bash
tcpdump tcp
tcpdump udp
tcpdump icmp
tcpdump ip
tcpdump ip6
```

| Command        | Meaning           |
| -------------- | ----------------- |
| `tcpdump tcp`  | Show TCP packets  |
| `tcpdump udp`  | Show UDP packets  |
| `tcpdump icmp` | Show ICMP packets |
| `tcpdump ip`   | Show IPv4 packets |
| `tcpdump ip6`  | Show IPv6 packets |

### Example

```bash
sudo tcpdump -i ens5 icmp -n
```

### Meaning

* `sudo` → Run with administrator privileges
* `tcpdump` → Capture and analyse packets
* `-i ens5` → Capture on the `ens5` interface
* `icmp` → Show only ICMP packets
* `-n` → Do not resolve IP addresses to hostnames

### ICMP Example

ICMP is commonly used by tools such as:

```bash
ping
```

For example, when you ping a host, you will usually see:

* **ICMP Echo Request** → Request sent to the destination
* **ICMP Echo Reply** → Reply received from the destination

ICMP can also be used by tools such as `traceroute`, where you may see **ICMP Time Exceeded** messages.

---

# 2. Logical Operators

`tcpdump` allows multiple filters to be combined using logical operators.

The three important operators are:

```text
and
or
not
```

---

## 2.1 AND Operator

`and` means **both conditions must be true**.

### Syntax

```bash
tcpdump condition1 and condition2
```

### Example

```bash
tcpdump host 1.1.1.1 and tcp
```

This shows:

> TCP traffic involving `1.1.1.1`.

Another example:

```bash
tcpdump host example.com and tcp port 443
```

This filters traffic that:

* involves `example.com`
* uses TCP
* uses port `443`

---

## 2.2 OR Operator

`or` means **either condition can be true**.

### Syntax

```bash
tcpdump condition1 or condition2
```

### Example

```bash
tcpdump udp or icmp
```

This shows:

> UDP packets OR ICMP packets.

---

## 2.3 NOT Operator

`not` is used to **exclude** a condition.

### Syntax

```bash
tcpdump not condition
```

### Example

```bash
tcpdump not tcp
```

This shows:

> Packets that are not TCP.

---

# 3. Combining Port and Protocol Filters

Filters can be combined to monitor specific services.

## SSH Traffic

SSH normally uses TCP port `22`.

```bash
tcpdump -i any tcp port 22
```

### Meaning

* `-i any` → Capture packets from all available interfaces
* `tcp` → Only TCP traffic
* `port 22` → Traffic using port 22

---

## NTP Traffic

NTP normally uses UDP port `123`.

```bash
tcpdump -i wlo1 udp port 123
```

This captures:

> UDP traffic using port 123.

---

## HTTPS Traffic

HTTPS normally uses TCP port `443`.

```bash
tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap
```

This captures:

> TCP HTTPS traffic involving `example.com`

and saves the capture to:

```text
https.pcap
```

### Important

`-w` means **write/save the captured packets to a file**.

---

# 4. Reading a PCAP File

A `.pcap` file contains captured network packets.

Use `-r` to read an existing capture file.

### Read the complete file

```bash
tcpdump -r traffic.pcap
```

### Read only the first 5 packets

```bash
tcpdump -r traffic.pcap -c 5 -n
```

### Meaning

* `-r traffic.pcap` → Read packets from `traffic.pcap`
* `-c 5` → Stop after 5 packets
* `-n` → Do not resolve IP addresses to hostnames

---

# 5. Filtering Packets from a PCAP File

You can apply filters while reading a `.pcap` file.

### Example

```bash
tcpdump -r traffic.pcap icmp -n
```

This displays only:

> ICMP packets from `traffic.pcap`.

Another example:

```bash
tcpdump -r traffic.pcap tcp port 22 -n
```

This displays:

> TCP traffic using SSH port 22.

---

# 6. Counting Packets

The Linux pipe `|` can send the output of one command to another command.

### Example

```bash
tcpdump -r traffic.pcap src host 192.168.124.1 -n | wc
```

Here:

```text
tcpdump → filters and displays packets
    |
    ↓
wc → counts the output
```

`wc` means **word count**.

You can use:

```bash
wc -l
```

to count the number of lines.

---

# 7. Count ICMP Packets in a PCAP

To count how many packets use ICMP:

```bash
tcpdump -r traffic.pcap icmp -n 2>/dev/null | wc -l
```

### Meaning

| Part              | Meaning                         |
| ----------------- | ------------------------------- |
| `tcpdump`         | Packet analysis tool            |
| `-r traffic.pcap` | Read the PCAP file              |
| `icmp`            | Filter ICMP packets             |
| `-n`              | Don't resolve hostnames         |
| `2>/dev/null`     | Hide error messages             |
| `\|`              | Send output to the next command |
| `wc -l`           | Count output lines              |

The number printed by the command is the **number of ICMP packets** found in the capture.

> **TryHackMe:** Run the command on the provided `traffic.pcap` file and submit the number displayed.

---

# 8. Useful Tcpdump Commands

```bash
# Capture TCP packets
tcpdump tcp

# Capture UDP packets
tcpdump udp

# Capture ICMP packets
tcpdump icmp

# Capture ICMP on a specific interface
sudo tcpdump -i ens5 icmp -n

# TCP traffic involving a host
tcpdump host 1.1.1.1 and tcp

# UDP or ICMP traffic
tcpdump udp or icmp

# Exclude TCP traffic
tcpdump not tcp

# Capture SSH traffic
tcpdump -i any tcp port 22

# Capture NTP traffic
tcpdump -i wlo1 udp port 123

# Capture HTTPS traffic and save it
tcpdump -i eth0 host example.com and tcp port 443 -w https.pcap

# Read a PCAP file
tcpdump -r traffic.pcap

# Read first 5 packets
tcpdump -r traffic.pcap -c 5 -n

# Count ICMP packets
tcpdump -r traffic.pcap icmp -n 2>/dev/null | wc -l
```

---

# 9. Quick Revision

### Protocol Filtering

```text
tcp     → TCP packets
udp     → UDP packets
icmp    → ICMP packets
ip      → IPv4 packets
ip6     → IPv6 packets
```

### Logical Operators

```text
and     → Both conditions
or      → Either condition
not     → Exclude a condition
```

### PCAP Options

```text
-r      → Read a capture file
-w      → Write/save a capture file
-c      → Stop after a specific number of packets
-n      → Don't resolve IP addresses to hostnames
```

### Easy Memory Trick

```text
-w → Write
-r → Read
-c → Count/limit packets
-n → No DNS/name resolution
```

---

# 10. What I Learned

* How to filter packets by **TCP, UDP, ICMP, IPv4 and IPv6**.
* How to combine multiple `tcpdump` filters using **and, or, and not**.
* How to filter traffic by **protocol + port**.
* How to capture specific services such as **SSH, NTP and HTTPS**.
* How to save packet captures into `.pcap` files.
* How to read existing `.pcap` files using `-r`.
* How to limit the number of displayed packets using `-c`.
* How to use `wc -l` to count filtered packet output.
* How to count **ICMP packets** inside a PCAP file.

```
# TABLE

| Command               | Purpose                 |
| --------------------- | ----------------------- |
| `tcpdump host IP`     | Traffic to/from host    |
| `tcpdump src host IP` | Traffic from host       |
| `tcpdump dst host IP` | Traffic to host         |
| `tcpdump port 53`     | Traffic to/from port 53 |
| `tcpdump src port 53` | Traffic from port 53    |
| `tcpdump dst port 53` | Traffic to port 53      |
| `tcpdump tcp`         | TCP traffic             |
| `tcpdump udp`         | UDP traffic             |
| `tcpdump icmp`        | ICMP traffic            |
| `tcpdump ip`          | IPv4 traffic            |
| `tcpdump ip6`         | IPv6 traffic            |
| `tcpdump ... and ...` | Both conditions         |
| `tcpdump ... or ...`  | Either condition        |
| `tcpdump not ...`     | Exclude condition       |
| `-i eth0`             | Select interface        |
| `-n`                  | Don't resolve hostnames |
| `-w file.pcap`        | Save capture            |

``
