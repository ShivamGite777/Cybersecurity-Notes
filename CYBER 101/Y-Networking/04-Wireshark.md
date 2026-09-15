### Wireshark - GUI, PCAP Analysis and File Details

**Wireshark** is a network traffic analyser used to capture, inspect, and investigate network packets.
It allows security analysts and network administrators to understand what is happening on a network.

**Important:** Wireshark is **not an IDS (Intrusion Detection System)**. It does not automatically detect attacks. It mainly allows an analyst to inspect packets and investigate suspicious activity.

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









### Packet Navigation

## Packet Numbers
Wireshark calculates the number of investigated packets and assigns a unique number for each packet. This helps the analysis process for big captures and makes it easy to go back to a specific point of an event.

<img width="1041" height="822" alt="image" src="https://github.com/user-attachments/assets/d303b7a9-95bf-4db5-96a6-34b3360f09b5" />


## Go to Packet
Packet numbers do not only help to count the total number of packets or make it easier to find/investigate specific packets. This feature not only navigates between packets up and down; it also provides in-frame packet tracking and finds the next packet in the particular part of the conversation. You can use the "Go" menu and toolbar to view specific packets.

<img width="1427" height="707" alt="image" src="https://github.com/user-attachments/assets/6d6ae0ce-d198-4a54-957b-43e977cb6054" />
<img width="1373" height="711" alt="image" src="https://github.com/user-attachments/assets/fac7e6f2-3376-4f0e-8109-97963cb1d3fc" />


## Find Packets
Apart from packet number, Wireshark can find packets by packet content. You can use the "Edit --> Find Packet" menu to make a search inside the packets for a particular event of interest. This helps analysts and administrators to find specific intrusion patterns or failure traces.

There are two crucial points in finding packets. The first is knowing the input type. This functionality accepts four types of inputs
(Display filter, Hex, String and Regex).
String and regex searches are the most commonly used search types. Searches are case insensitive, but you can set the case sensitivity in your search by clicking the radio button.

The second point is choosing the search field. You can conduct searches in the three panes
(packet list, packet details, and packet bytes),
and it is important to know the available information in each pane to find the event of interest. For example, if you try to find the information available in the packet details pane and conduct the search in the packet list pane, Wireshark won't find it even if it exists.
<img width="1408" height="711" alt="image" src="https://github.com/user-attachments/assets/de9388c6-4ce2-4ee5-b68f-3913081da1f9" />
<img width="1437" height="786" alt="image" src="https://github.com/user-attachments/assets/c0e8fd23-4e29-4cc6-93cd-197ef4a295f6" />


## Mark Packets
Marking packets is another helpful functionality for analysts. You can find/point to a specific packet for further investigation by marking it. It helps analysts point to an event of interest or export particular packets from the capture. You can use the "Edit" or the "right-click" menu to mark/unmark packets.

Marked packets will be shown in black regardless of the original colour representing the connection type. Note that marked packet information is renewed every file session, so marked packets will be lost after closing the capture file.

<img width="1432" height="716" alt="image" src="https://github.com/user-attachments/assets/afd4b0ba-d4ff-4cbd-85d6-65e989e210fd" />


## Packet Comments
Similar to packet marking, commenting is another helpful feature for analysts. You can add comments for particular packets that will help the further investigation or remind and point out important/suspicious points for other layer analysts. Unlike packet marking, the comments can stay within the capture file until the operator removes them.

<img width="1545" height="706" alt="image" src="https://github.com/user-attachments/assets/5d9d1e2f-3e70-4df1-9b84-1054bcf4b52a" />
<img width="1518" height="756" alt="image" src="https://github.com/user-attachments/assets/9994fd0c-b07b-40f1-90e0-3a96db1fe5f7" />


## Export Packets
Capture files can contain thousands of packets in a single file. As mentioned earlier, Wireshark is not an IDS, so sometimes, it is necessary to separate specific packages from the file and dig deeper to resolve an incident. This functionality helps analysts share the only suspicious packages (decided scope). Thus redundant information is not included in the analysis process. You can use the "File" menu to export packets.

<img width="1457" height="776" alt="image" src="https://github.com/user-attachments/assets/02f222be-dcb1-4dad-baeb-8465bce57e40" />
<img width="991" height="800" alt="image" src="https://github.com/user-attachments/assets/ff51da0c-020a-45fd-8e21-152c8a20ec2a" />


## Export Objects (Files)
Wireshark can extract files transferred through the wire. For a security analyst, it is vital to discover shared files and save them for further investigation. Exporting objects are available only for selected protocol's streams (DICOM, HTTP, IMF, SMB and TFTP).

<img width="1488" height="757" alt="image" src="https://github.com/user-attachments/assets/18ad0ca0-10fc-4fa2-a51e-9a65bd12ca28" />
<img width="1047" height="657" alt="image" src="https://github.com/user-attachments/assets/529d9467-e548-4859-a531-e75074e5d606" />


## Time Display Format
Wireshark lists the packets as they are captured, so investigating the default flow is not always the best option. By default, Wireshark shows the time in "Seconds Since Beginning of Capture", the common usage is using the UTC Time Display Format for a better view. You can use the "View --> Time Display Format" menu to change the time display format.
<img width="1531" height="452" alt="image" src="https://github.com/user-attachments/assets/facccb66-f820-4c3e-bddb-a0dae1602c00" />


## Expert Info
Wireshark also detects specific states of protocols to help analysts easily spot possible anomalies and problems. Note that these are only suggestions, and there is always a chance of having false positives/negatives. Expert info can provide a group of categories in three different severities. Details are shown in the table below.
<img width="1841" height="632" alt="image" src="https://github.com/user-attachments/assets/a7134a28-6b99-420d-bf61-658d535d54ca" />

### HANDS ON


## Use the "Exercise.pcapng" file to answer the questions. Search the "r4w" string in packet details. What is the name of artist 1?
under http
<img width="930" height="727" alt="image" src="https://github.com/user-attachments/assets/7bccc523-037e-4dd5-8a15-54e0e5d7a001" />


## Go to packet 12 and read the packet comments. What is the answer?
   Note: use md5sum <filename> terminal command to get MD5 hash
# Ans 
 -Open Exercise.pcapng.
- Press Ctrl + G → enter 12.
 -Read Packet Comment.
 -It says to go to packet 39765.
 -Press Ctrl + G → enter 39765.
 -Find JPEG File Interchange Format.
- Go to File → Export Objects → HTTP.
- Select the JPEG → Save.
- Open Kali Terminal.
- Go to Downloads:


## There is a ".txt" file inside the capture file. Find the file and read it; what is the alien's name?

# Ans
Same 
Use Cat



## Look at the expert info section. What is the number of warnings?
# Ans
-Expert Info → Warnings
-Open Exercise.pcapng.
-Click Analyze.
-Select Expert Information.
-Look for Warnings.
-Read the number shown.




























































### Wireshark - Packet Filtering

## Overview

Wireshark provides powerful filtering options that help analysts reduce network traffic and focus on packets related to an investigation.

There are two main types of filters:

- **Capture Filter** → Filters packets while capturing them.
- **Display Filter** → Filters packets after they have been captured.

> **Golden Rule:** If you can click on it, you can filter and copy it.

---

## Apply as Filter

**Apply as Filter** allows you to filter packets based on a selected field or value.
This is the most basic way of filtering traffic
### How to use

1. Select a packet.
2. Find the field you want to investigate.
3. Right-click the field.
4. Select **Apply as Filter → Selected**.
5. Wireshark automatically creates and applies the filter.

<img width="1341" height="762" alt="image" src="https://github.com/user-attachments/assets/176ee708-e364-4fe5-bd7f-7132a97679d4" />
<img width="1342" height="598" alt="image" src="https://github.com/user-attachments/assets/38d2f491-9908-4c20-bf9c-a7e9dfe02135" />


## Conversation Filter

**Conversation Filter** shows packets related to the same communication.

It can focus on:

- IP addresses
- Ports
- Protocols
- Client and server communication

### Difference

| Feature | Purpose |
|---|---|
| Apply as Filter | Filters a specific field/value |
| Conversation Filter | Shows related communication |
<img width="1363" height="790" alt="image" src="https://github.com/user-attachments/assets/45577949-de07-4b53-bf90-cf9deae4e2d2" />
<img width="1352" height="662" alt="image" src="https://github.com/user-attachments/assets/e50c66c0-00ce-4487-a765-7bad58aaa1ec" />

---

## Colourise Conversation

**Colourise Conversation** highlights packets belonging to the same conversation.

Unlike Conversation Filter, it does **not hide other packets**.

<img width="1336" height="821" alt="image" src="https://github.com/user-attachments/assets/70b8e14c-4360-4d63-b1ad-f79441aa8900" />
<img width="1197" height="762" alt="image" src="https://github.com/user-attachments/assets/5532c749-7818-4c3a-b590-798d865d45ea" />


### Reset

**View → Colorize Conversation → Reset Colorization**

---

## Prepare as Filter

**Prepare as Filter** creates a display filter but does not apply it immediately.
It places the filter in the display filter bar.

You can then:

- Press **Enter** to apply it.
- Add more conditions using **AND / OR**.
<img width="1367" height="705" alt="image" src="https://github.com/user-attachments/assets/9322aceb-ba3a-4526-9a0a-041eb8ac93a6" />
<img width="1372" height="746" alt="image" src="https://github.com/user-attachments/assets/783bbe6c-fa7f-461f-b7b2-0c312f0944ae" />

### Difference

| Feature | Action |
|---|---|
| Apply as Filter | Creates and immediately applies the filter |
| Prepare as Filter | Creates the filter but waits for execution |

---

## Apply as Column

**Apply as Column** adds a selected field as a new column in the Packet List.

This is useful when comparing the same field across multiple packets.

<img width="1377" height="731" alt="image" src="https://github.com/user-attachments/assets/7a9ee2fd-cd60-4a8b-ba88-19542c1a8889" />

<img width="1352" height="618" alt="image" src="https://github.com/user-attachments/assets/c1d54e71-1d51-43b2-baf4-d55c7a9973aa" />

## Follow Stream

**Follow Stream** reconstructs the communication between the client and server.
Instead of viewing individual packets, Wireshark combines the traffic into a readable application-level conversation.

It can help reveal:

- HTTP requests
- HTTP responses
- Usernames
- Passwords
- Other unencrypted data

### How to use

**Right-click packet → Follow → HTTP Stream**

Depending on the protocol, you may also see:

- Follow TCP Stream
- Follow UDP Stream
- Follow HTTP Stream

 
  <img width="1352" height="763" alt="image" src="https://github.com/user-attachments/assets/f073d8c3-7bfa-4d37-8f46-ab7b5324860d" />
  <img width="951" height="708" alt="image" src="https://github.com/user-attachments/assets/ff4532b5-67cb-4b2a-8201-c443327967df" />




### Stream Colours

- **Blue** → Server to Client
- **Red** → Client to Server

# Important

After following a stream, Wireshark automatically applies a display filter.
To remove the filter, click the **X** button on the right side of the display filter bar.
<img width="1887" height="560" alt="image" src="https://github.com/user-attachments/assets/48520a0b-a2e8-4faa-8975-1f7648331e0d" />

---

# Simple Display Filters

## Filter by Protocol

To filter by protocol name, enter the protocol name in the display filter bar.
<img width="1887" height="560" alt="image" src="https://github.com/user-attachments/assets/622adea4-38cc-4214-979e-8af1a9cc462e" />

Example:

`http`

This displays HTTP packets.

Other examples:

`arp`


---

## Filter by TCP Port

### Syntax

`tcp.port == <port>`

Example:

`tcp.port == 80`

This displays packets using TCP port 80.
<img width="1897" height="573" alt="image" src="https://github.com/user-attachments/assets/121acd11-55ed-413e-8d6a-8f8bb4096c74" />

---

## Filter by UDP Port

### Syntax

`udp.port == <port>`

Example:

`udp.port == 53`

This can be used to filter DNS-related UDP traffic.

---

## Filter by IP Address

### Syntax

`ip.addr == <IP address>`

Example:

`ip.addr == 192.168.1.2`

This displays packets where the specified IP address is involved.
<img width="1856" height="578" alt="image" src="https://github.com/user-attachments/assets/db3f2bb7-8841-412c-8896-df0728ac93b1" />


---

## HANDS-ON
Use the "Exercise.pcapng" file to answer the questions.
Go to packet number 4. Right-click on the "Hypertext Transfer Protocol" and apply it as a filter.
Now, look at the filter pane. What is the filter query?


Open Exercise.pcapng.
-Press Ctrl + G.
-Enter 4 → press Enter.
-Packet 4 will be selected.
-In the middle Packet Details pane, find:
-Hypertext Transfer Protocol
-Right-click on Hypertext Transfer Protocol.
-Select Apply as Filter → Selected.
-Look at the Display Filter bar at the top.

<img width="868" height="577" alt="image" src="https://github.com/user-attachments/assets/50b3cf4d-93bb-4cb5-a617-2914c422727a" />
<img width="937" height="467" alt="image" src="https://github.com/user-attachments/assets/d09452ba-e1a7-4291-b77e-d239069eac17" />
<img width="862" height="365" alt="image" src="https://github.com/user-attachments/assets/274c7399-1e3e-4858-acce-5d63692585bf" />


## What is the number of displayed packets?  

<img width="996" height="175" alt="image" src="https://github.com/user-attachments/assets/3bfbbe03-1a3f-403c-a5d6-770a527f131d" />


## Go to packet number 33790, follow the HTTP stream, and look carefully at the responses.
   Looking at the web server's response, what is the total number of artists?


<img width="960" height="782" alt="image" src="https://github.com/user-attachments/assets/44722053-1500-4b17-b7b6-6e40d820545c" />



