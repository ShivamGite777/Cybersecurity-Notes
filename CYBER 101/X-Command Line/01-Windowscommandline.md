# Windows Command Line Basics

## CLI vs GUI

### GUI
A **Graphical User Interface (GUI)** allows users to interact with a system using:

- Mouse
- Icons
- Windows
- Menus

### CLI
A **Command-Line Interface (CLI)** allows users to interact with a system by typing commands.

## Advantages of CLI

- **Faster and efficient** once commands are learned
- **Lower resource usage** than a GUI
- Useful for **automation** using scripts or batch files
- Convenient for **remote management**
- Works well on systems with limited resources or slow networks

Example:

Instead of clicking through multiple menus to check your IP address, you can run a command directly.

---

# Windows Command Prompt

Windows Command Prompt is:

`cmd.exe`

It is the default command-line interpreter in Windows.

## Main Uses

- Display system information
- Check network configuration
- Troubleshoot network issues
- Manage files and folders
- Check running processes

# Windows PATH

Windows uses the **PATH environment variable** to know where to look for executable commands.

Check environment variables using:

    set

Look for:
<img width="1533" height="292" alt="image" src="https://github.com/user-attachments/assets/b58ce98f-1fd8-460e-b009-b7570a4798e7" />

    Path=C:\Windows\system32;C:\Windows;...
Commands located in directories listed in the `PATH` can usually be executed without specifying their full path.


# `ver`

Displays the Windows operating system version.

Command:

    ver
<img width="1367" height="131" alt="image" src="https://github.com/user-attachments/assets/dd715dee-e671-4d64-ae50-19cb262549cb" />

Example output:

    Microsoft Windows [Version 10.0.17763.1821]

---

# `systeminfo`

Displays detailed information about the system.

Command:

    systeminfo
<img width="1546" height="333" alt="image" src="https://github.com/user-attachments/assets/c0321f45-3082-4298-9bf9-516d2fdbf20b" />

Information includes:

- Host Name
- OS Name
- OS Version
- OS Manufacturer
- System Configuration
- System Boot Time
- Processor
- Memory
- Windows Directory
- System Directory

Example:

    OS Name: Microsoft Windows Server 2019 Datacenter
    OS Version: 10.0.17763 N/A Build 17763

## System Boot Time

**System Boot Time** means the date and time when Windows was last started or restarted.

# `driverquery`

Displays information about installed device drivers.

Command:

    driverquery

The output can be long.


# Pipe Output with `more`

Use `| more` to display long command output **page by page**.

Example:

    driverquery | more

## Controls

- `Space` → Show next page
- `Ctrl + C` → Exit

---

# `help`

Displays help information for commands.

Example:

    help

You can also get help for a specific command:

    command /?

Example:

    systeminfo /?


# `cls`

Clears the Command Prompt screen.

Command:

    cls




### Windows Command Line - Networking Commands

## `ipconfig` — Check Network Configuration

Displays basic network information:

```text
ipconfig
```

Shows:

* IPv4 Address → Your device's IP address
* Subnet Mask → Defines the network size
* Default Gateway → Usually your router

Example:

```text
IPv4 Address: 10.10.230.237
Subnet Mask: 255.255.0.0
Subnet Mask = Defines the network boundary/range
Default Gateway: 10.10.0.1
Gateway = Where the machine sends traffic when the destination is outside its local network.
```
<img width="1015" height="655" alt="image" src="https://github.com/user-attachments/assets/a18531c1-dd19-4750-8191-ab0b3a6d2425" />

## `ipconfig /all` — Detailed Network Information

```text
ipconfig /all
```

Shows additional information:

* **Physical Address** → MAC Address
* **DHCP Enabled**

# DHCP Enabled: Yes

This means the machine received its network configuration automatically.

Windows Machine
       │
       │ "I need an IP address"
       ▼
DHCP Server
       │
       ├── Gives IP Address
       ├── Gives Subnet Mask
       ├── Gives Gateway
       └── Gives DNS Server
       │
       ▼
Windows Machine configure

* **DNS Servers**
* Network adapter information

  
<img width="749" height="701" alt="image" src="https://github.com/user-attachments/assets/0030e50f-569e-4e63-9ae6-8ae392af654b" />

Example:

```text
Physical Address: 02-B7-DF-1D-0D-99
```

> **MAC Address** = Physical address of a network adapter.

## `ping` — Check Connectivity

```text
ping example.com
```
<img width="698" height="463" alt="image" src="https://github.com/user-attachments/assets/eaa70470-5e80-4a12-b6ef-b38bf8adacf3" />


`ping` sends an **ICMP packet** to check whether a target can be reached.

Example:

```text
Reply from 93.184.215.14: time=78ms
```

This means:

```text
Your Computer → example.com → Reply Received
```

* `time=78ms` → Round-trip response time
* `0% loss` → All packets received successfully

You can replace `example.com` with any reachable domain or IP:

```text
ping google.com
ping 8.8.8.8
```

## `tracert` — Trace Network Route

```text
tracert example.com
```
<img width="763" height="783" alt="image" src="https://github.com/user-attachments/assets/4c9aa8d0-21c8-44d6-b082-0dd5dbcd5b06" />

Shows the **routers (hops)** your traffic passes through before reaching the destination.

Example:

```text
Your PC
   ↓
Router 1
   ↓
Router 2
   ↓
Router 3
   ↓
Destination
```

Each numbered line is called a **hop**.

`* * * Request timed out` does not always mean the destination is unreachable; that router may simply not respond to traceroute requests.


## `nslookup` — Find a Domain's IP Address

```text
nslookup example.com
```
<img width="750" height="630" alt="image" src="https://github.com/user-attachments/assets/fc71c04c-5b49-4cb5-ac33-3df9e0e70d8e" />


Asks a DNS server:

> "What IP address belongs to example.com?"

Example:

```text
Name: example.com
Address: 93.184.215.14
```

You can also specify a DNS server:

```text
nslookup example.com 1.1.1.1
```

Here, `1.1.1.1` is the DNS server being used for the lookup.

---

## `netstat` — View Network Connections

```text
netstat
```
<img width="741" height="258" alt="image" src="https://github.com/user-attachments/assets/0e014b4a-6635-476c-afa5-1238178a3889" />


Shows active network connections.

Example:

```text
TCP  10.10.230.237:22  10.11.81.126:53486  ESTABLISHED
```

Meaning:

```text
Local Machine : Port 22
        ↓
Connected to
        ↓
Remote Machine : Port 53486
```

Port `22` is commonly used for **SSH**.

## `netstat -abon`

```text
netstat -abon
```
<img width="749" height="700" alt="image" src="https://github.com/user-attachments/assets/9f13401f-62e5-4491-a9f4-794832faf3aa" />
## PID = Process ID.

Every running program/process in Windows gets a unique number called a PID.

Useful options:

| Option | Meaning                                       |
| ------ | --------------------------------------------- |
| `-a`   | Show all connections and listening ports      |
| `-b`   | Show the program/service using the connection |
| `-o`   | Show the Process ID (PID)                     |
| `-n`   | Show numerical IP addresses and port numbers  |

Example:

```text
TCP  0.0.0.0:22  0.0.0.0:0  LISTENING  2116
[sshd.exe]
```

Meaning:

```text
Port 22
   ↓
LISTENING
   ↓
sshd.exe
   ↓
SSH service
```
## Common Services Seen
Port	Service
22	SSH
135	RpcSs / RPC Endpoint Mapper
3389	Remote Desktop Protocol (RDP)

## Summary

```text
ipconfig        → Basic network information
ipconfig /all   → Detailed info + MAC address
ping            → Check if a target is reachable
tracert         → Show network route/hops
nslookup        → Find domain IP using DNS
netstat         → Show network connections
netstat -abon   → Connections + ports + program + PID
```
### Windows CMD - Files and Directories

## Working with Directories

# `cd` — Show or Change Directory

Show your current directory:

```text
cd
```

Change to a folder:

```text
cd folder_name
```

Example:

```text
C:\> cd Users
C:\Users>
```

Go back one level:

```text
cd ..
```

Example:

```text
C:\Users> cd ..
C:\>
```

### `dir` — List Files and Folders

```text
dir
```

Useful options:

```text
dir /a
```

Shows hidden and system files.

```text
dir /s
```

Shows files in the current directory and all subdirectories.

### `tree` — Show Folder Structure

```text
tree
```

Example:

```text
C:.
├── Desktop
├── Documents
├── Downloads
└── Pictures
```

### `mkdir` — Create Directory

`mkdir` = **Make Directory**

```text
mkdir backup_files
```

Creates:

```text
backup_files
```
### `rmdir` — Remove Directory

`rmdir` = **Remove Directory**

```text
rmdir backup_files
```

Deletes the directory.


# Working with Files

### `type` — Display File Contents

```text
type test.txt
```

Displays the contents of a text file.

---

### `more` — Display Long Files Page by Page

```text
more test.txt
```

Or:

```text
type test.txt | more
```

Controls:

* `Space` → Next page
* `Enter` → Next line

---

### `copy` — Copy Files

```text
copy test.txt test2.txt
```

Creates a copy:

```text
test.txt
test2.txt
```

Copy a file to another folder:

```text
copy test.txt C:\backup
```

---

### `move` — Move Files

```text
move test.txt C:\backup
```

Moves `test.txt` to the `backup` folder.

Example:

```text
move test2.txt ..
```

`..` means the **parent directory**, so the file moves one level up.

---

### `del` — Delete a File

```text
del test.txt
```

Deletes `test.txt`.

---

### `erase` — Delete a File

```text
erase test.txt
```

Does the same thing as `del`.


# Wildcard `*`

The `*` wildcard represents **multiple characters/files**.

Example:

```text
copy *.md C:\Markdown
```

This copies all files ending in `.md`.

Example:

```text
notes.md
windows.md
linux.md
test.txt
```

Only these match:

```text
notes.md
windows.md
linux.md
```

---

# Summary

| Command                 | Description                      |
| ----------------------- | -------------------------------- |
| `cd`                    | Show current directory           |
| `cd folder`             | Enter/change directory           |
| `cd ..`                 | Go back one directory            |
| `dir`                   | List files and folders           |
| `dir /a`                | Show hidden and system files     |
| `dir /s`                | Show files in all subdirectories |
| `tree`                  | Display folder structure         |
| `mkdir folder`          | Create a directory               |
| `rmdir folder`          | Remove a directory               |
| `type file.txt`         | Display text file contents       |
| `more file.txt`         | Read long file page by page      |
| `copy file destination` | Copy a file                      |
| `move file destination` | Move a file                      |
| `del file.txt`          | Delete a file                    |
| `erase file.txt`        | Delete a file                    |
| `*`                     | Match multiple files             |
