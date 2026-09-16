### Tcpdump

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

# sudo = Run the command as administrator
* `tcpdump` → packet capture tool
* `-i` → interface
* `ens5` → interface to listen on

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
