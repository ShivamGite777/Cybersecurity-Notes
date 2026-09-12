
### IP Addresses

## 1. Private vs Public IP Address

A **private IP address** is used inside local networks such as home, college, or company networks.

There are **three private IPv4 ranges**:

| Private Range                   | Example           |
| ------------------------------- | ----------------- |
| `10.0.0.0 – 10.255.255.255`     | `10.20.141.132`   |
| `172.16.0.0 – 172.31.255.255`   | `172.23.182.251`  |
| `192.168.0.0 – 192.168.255.255` | `192.168.250.125` |

### Question

**Which of the following IP addresses is NOT a private IP address?**

* `192.168.250.125` → Private ✅
* `10.20.141.132` → Private ✅
* `49.69.147.197` → **Public ❌**
* `172.23.182.251` → Private ✅

## Answer

**`49.69.147.197`**

It does not belong to any of the three private IP ranges, so it is a **public IP address**.

---

## 2. Valid vs Invalid IP Address

An IPv4 address contains **four numbers (octets)** separated by dots.

Example:

```text
192.168.1.10
```

Each octet must be between:

```text
0 – 255
```

### Question

**Which of the following IP addresses is NOT a valid IP address?**

* `192.168.250.15` → Valid ✅
* `192.168.254.17` → Valid ✅
* `192.168.305.19` → **Invalid ❌**
* `192.168.199.13` → Valid ✅

### Answer

**`192.168.305.19`**

The third octet is:

```text
192.168.305.19
        ↑
       305
```

Since `305` is greater than `255`, this is **not a valid IPv4 address**.

## A port number uses two octets; consequently, it ranges between 1 and 65535; port 0 is reserved. (The number 65535 is calculated by the expression 216 − 1.)




### Encapsulation

**Encapsulation** is the process where each networking layer adds its own **header** (and sometimes a **trailer**) to the data before passing it to the next layer.

## Encapsulation Flow

```text
Application Data
       ↓
TCP Segment / UDP Datagram
       ↓
IP Packet
       ↓
WiFi / Ethernet Frame
```

## Example

Suppose you send:

```text
Hello
```

The data is encapsulated step by step:

```text
Application
    ↓
Hello

Transport Layer
    ↓
[TCP Header][Hello]
    ↓
TCP Segment

Network Layer
    ↓
[IP Header][TCP Header][Hello]
    ↓
IP Packet

Data Link Layer
    ↓
[Frame Header][IP Header][TCP Header][Hello][Trailer]
    ↓
Frame
```






### Telnet


**TELNET (Teletype Network)** is a network protocol used for **remote terminal connections**.

It allows us to connect to a remote system and send **text commands**.

Telnet uses **TCP** and can connect to services running on different TCP ports.

> ⚠️ Telnet is insecure because it does not encrypt communication. **SSH** is preferred for secure remote access.

---

# Telnet Lab

In this lab, the target machine has three services:

| Service | Port | What it does                      |
| ------- | ---: | --------------------------------- |
| Echo    |  `7` | Sends back whatever you send      |
| Daytime | `13` | Returns the current date and time |
| HTTP    | `80` | Serves web pages                  |

---

## 1. Echo Server — Port 7

Connect using:

```bash
telnet 10.49.181.50 7
```

Anything you type is returned by the server.

Example:

```text
You → Hi
Server → Hi

You → How are you?
Server → How are you?
```

### Closing the connection

Press:

```text
CTRL + ]
```

Then type:

```text
quit
```

---

## 2. Daytime Server — Port 13

Connect using:

```bash
telnet 10.49.181.50 13
```

The server returns the current date and time.

Example:

```text
Thu Jun 20 12:36:32 PM UTC 2024
```

The connection then closes automatically.

```text
Port 13 → Daytime Service
```

---

# 3. Web Server — Port 80

HTTP normally uses **TCP port 80**.

Connect using:

```bash
telnet 10.49.181.50 80
```

After connecting, send:

```http
GET / HTTP/1.1
Host: telnet.thm
```

Press **Enter twice** after the `Host` line.

### What does this mean?

```text
GET /
```

Requests the website's main page.

```text
HTTP/1.1
```

Specifies the HTTP version.

```text
Host: telnet.thm
```

Specifies the website you want to access.

---

## HTTP Response

The server may respond with:

```text
HTTP/1.1 200 OK
Content-Type: text/html
```

### Meaning

```text
200 OK
```

→ The request was successful.

```text
Content-Type: text/html
```

→ The response contains an HTML webpage.

---

# Useful Commands

### Connect to a service

```bash
telnet <IP> <PORT>
```

Example:

```bash
telnet 10.49.181.50 7
```

### Exit Telnet

```text
CTRL + ]
```

Then:

```text
quit
```

---

## Important Points

* **Telnet** → Remote communication using text commands.
* Telnet uses **TCP**.
* **Port 7** → Echo service.
* **Port 13** → Daytime service.
* **Port 80** → HTTP web server.
* Telnet can connect to **any TCP service that is listening on a port**.
* Telnet communication is **unencrypted**.
* **SSH (port 22)** is preferred for secure remote access.

## Quick Memory

```text
7  → Echo
13 → Daytime
22 → SSH
23 → Telnet
80 → HTTP
443 → HTTPS
```

> **Telnet is a client that can create a TCP connection to a specific port and allow you to communicate with the service running on that port.**
