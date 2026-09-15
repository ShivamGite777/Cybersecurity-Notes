<img width="921" height="705" alt="image" src="https://github.com/user-attachments/assets/7b49b9ca-6b98-4859-99c4-a39738bb7802" /><img width="906" height="646" alt="image" src="https://github.com/user-attachments/assets/c3e196ae-d181-4791-a819-cf930c761456" /><img width="870" height="612" alt="image" src="https://github.com/user-attachments/assets/6b4d84ca-08bc-4b98-88fa-6ee2d77b7775" />### Wireshark - GUI, PCAP Analysis and File Details

**Wireshark** is a network traffic analyser used to capture, inspect, and investigate network packets.
It allows security analysts and network administrators to understand what is happening on a network.

> **Important:** Wireshark is **not an IDS (Intrusion Detection System)**. It does not automatically detect attacks. It mainly allows an analyst to inspect packets and investigate suspicious activity.

---

## 2. Use Cases of Wireshark

Wireshark can be used for:

# Network Troubleshooting

* Detect network problems.
* Find network congestion.
* Investigate network load and connection failures.
* Troubleshoot communication problems.

# Security Analysis

* Detect suspicious network activity.
* Identify rogue hosts.
* Investigate unusual port usage.
* Analyse suspicious traffic.

# Protocol Analysis

* Learn how network protocols work.
* Inspect packet headers.
* Analyse response codes.
* Inspect packet payloads.
* Understand how data is exchanged between systems.

## Important Point

Wireshark **reads and analyses packets**. It does not modify the packets.
Therefore, finding an anomaly depends heavily on the analyst's knowledge and investigation skills.

---

# 3. Wireshark GUI

When Wireshark starts, its main interface contains several important sections.

| Section                            | Description                                                                                       |
| ---------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Toolbar**                        | Contains menus and shortcuts for capturing, filtering, sorting, exporting and processing packets. |
| **Display Filter Bar**             | Used to filter packets and find specific traffic.                                                 |
| **Recent Files**                   | Shows recently opened capture files.                                                              |
| **Capture Filters and Interfaces** | Shows available network interfaces and capture filters.                                           |
| **Status Bar**                     | Displays information about the current profile and packet statistics.                             |

---

## 4. Important Wireshark Panes

After opening a PCAP file, Wireshark displays packet information in three main panes.

# Packet List Pane

Shows a summary of packets.

It includes information such as:

* Packet number
* Time
* Source
* Destination
* Protocol
* Packet information

You can select a packet from this pane for further investigation.

---

## Packet Details Panel

Shows the detailed protocol information of the selected packet.

For example:

```text
Ethernet
    ↓
IP
    ↓
TCP
    ↓
Application Protocol
```

This allows us to inspect individual fields inside a packet.

---

## Packet Bytes Pane

Displays the raw packet data in:

* Hexadecimal
* ASCII/decoded format

It is useful when investigating the actual contents of a packet.

---

# 5. Loading PCAP Files

Wireshark can open packet capture files such as:

```text
.pcap
.pcapng
```

### Ways to open a PCAP

You can:

1. Use **File → Open**
2. Drag and drop the file into Wireshark.
3. Double-click the file if Wireshark is configured as the default application.

Example:

```text
Exercise.pcapng
```

After opening it, Wireshark displays the captured packets.

---

# 6. Packet Colouring

Wireshark uses colours to make different types of traffic easier to identify.
Packet colours can help analysts quickly notice:

* Different protocols
* TCP traffic
* Errors
* Suspicious or unusual traffic

### Colouring Rules

Wireshark has two types of colouring rules:

### Permanent Rules

Saved in the Wireshark preferences/profile and available in future sessions.

You can access them through:

```text
View → Coloring Rules
```

### Temporary Rules

Temporary colouring can be applied during the current Wireshark session.

---

# 7. Traffic Sniffing

Wireshark can capture live network traffic.

The main capture controls are:

| Button               | Function                |
| -------------------- | ----------------------- |
| 🔵 Blue Shark Button | Start capturing traffic |
| 🔴 Red Button        | Stop capturing          |
| 🟢 Green Button      | Restart capturing       |

The status bar shows information such as:

* Capture interface
* Number of captured packets
* Current capture status

---

# 8. Merge PCAP Files

Wireshark can combine multiple capture files into one.

### Steps

Go to:

```text
File → Merge
```

Then:

1. Select another PCAP file.
2. Wireshark displays the packet information.
3. Click **Open**.
4. The files are merged.
5. Save the resulting capture file.

### Important

Always save the merged PCAP before continuing your analysis.

---

# 9. View PCAP File Details

PCAP file details are useful when investigating or identifying a capture file.

Wireshark can provide information such as:

* File hash
* Capture start time
* Capture duration
* Capture file comments
* Network interface
* Packet statistics
* Total number of packets

### How to Open Capture File Properties

Go to:

```text
Statistics → Capture File Properties
```
<img width="938" height="786" alt="image" src="https://github.com/user-attachments/assets/1029c755-c39a-4a1b-9a2f-8c0b4deac3f4" />
<img width="963" height="806" alt="image" src="https://github.com/user-attachments/assets/060fc0c7-437c-41f8-b27a-341d4e42d6dc" />



You can also click the **PCAP icon at the bottom-left** of the Wireshark interface.

---

# 10. Capture File Comments

A PCAP/PCAPNG file can contain **capture file comments**.

These comments may contain important information such as:

* Investigation notes
* Capture information
* Instructions
* Flags
* Other metadata

### To read the comments:

```text
Statistics
    ↓
Capture File Properties
    ↓
Capture File Comments
```

For the TryHackMe exercise, the flag is hidden in these comments.

---

# 11. SHA256 Hash of the Capture File

### Question

> What is the **SHA256 hash** value of the capture file?

The SHA256 hash can be obtained from the capture file properties.

Open:

```text
Statistics → Capture File Properties
```

Look for:

```text
SHA256
```

The hash is a 64-character hexadecimal value.

Example format:

```text
a1b2c3d4e5f6...
```


# 12. Useful Wireshark Navigation

| Task                 | Wireshark Menu                         |
| -------------------- | -------------------------------------- |
| Open PCAP            | `File → Open`                          |
| Merge PCAPs          | `File → Merge`                         |
| Capture File Details | `Statistics → Capture File Properties` |
| Colouring Rules      | `View → Coloring Rules`                |
| Start Capture        | Blue Shark Button                      |
| Stop Capture         | Red Stop Button                        |
| Restart Capture      | Green Restart Button                   |

---














### Packet Dissection

**Packet Dissection:** Breaking a packet into different protocols and fields to understand its contents.

Example:

```text
Ethernet → IP → TCP → HTTP
```

---

## Packet Details

**Packet Details:** Information about a selected packet shown in Wireshark.

Click a packet in the **Packet List Pane** to view its details.

---

## Frame

**Frame:** Information about the captured packet itself.

Example: packet number, size, capture time.

---

## Ethernet

**Ethernet:** Data Link Layer information.

Contains **MAC addresses**.

---

## IPv4

**IPv4:** Network Layer protocol used for addressing and routing.

Contains:

* Source IP
* Destination IP
* TTL

---

## TTL

**TTL = Time To Live**

Shows how long a packet can remain in the network before being discarded.

Example:
<img width="906" height="646" alt="image" src="https://github.com/user-attachments/assets/ce02da19-597e-4bb5-ae7a-f8b00bf25bff" />


```text
TTL: 64
```

---

## TCP

**TCP = Transmission Control Protocol**

Provides reliable communication between devices.

Contains:

* Source port
* Destination port
* Sequence number
* TCP flags
* Payload length

---

## TCP Payload

**TCP Payload:** The actual data carried inside a TCP segment.

Example:

```text
TCP Segment Len: 500
```
<img width="921" height="705" alt="image" src="https://github.com/user-attachments/assets/747c7170-4617-402e-a6f9-a6dec43aa8c1" />

Here, `500 bytes` is the TCP payload size.

---

## HTTP

**HTTP = Hypertext Transfer Protocol**

Protocol used for communication between web browsers and web servers.

Example:

```text
GET /index.html
```

---

## ETag

**ETag = Entity Tag**

A value used by a web server to identify a specific **version of a resource**.

Example:

```text
ETag: "82ecb-6321-9e904585"
```
<img width="870" height="612" alt="image" src="https://github.com/user-attachments/assets/c9fce230-c600-43c5-bd4c-c63eeee24bd8" />


Used mainly for **web caching**.

---

## XML

**XML = eXtensible Markup Language**

A language used to **store and organize data using tags**.

Example:

```xml
<student>
    <name>Shivam</name>
</student>
```

---

## Extensible

**Extensible:** Something that can be **expanded or customized**.

In XML, you can create your own tags:

```xml
<student>
    <name>Shivam</name>
    <skill>Cybersecurity</skill>
</student>
```

---

## OSI Layers

**OSI Model:** A 7-layer model used to understand network communication.

In Wireshark, packets can be viewed through different protocol layers.

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

---

## IMP

| Term                  | Short Meaning                     |
| --------------------- | --------------------------------- |
| **Packet Dissection** | Breaking down a packet            |
| **Frame**             | Captured packet information       |
| **Ethernet**          | MAC/addressing at Data Link layer |
| **IPv4**              | IP addressing and routing         |
| **TTL**               | Packet lifetime                   |
| **TCP**               | Reliable transport protocol       |
| **TCP Payload**       | Data carried by TCP               |
| **HTTP**              | Web communication protocol        |
| **ETag**              | Resource version identifier       |
| **XML**               | Data storage using tags           |
| **Extensible**        | Can be expanded/customized        |
| **OSI Model**         | 7-layer network model             |

