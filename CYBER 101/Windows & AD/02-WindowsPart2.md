### System Configuration (MSConfig)

## MSConfig

**MSConfig (System Configuration)** is a built-in Windows utility used to **troubleshoot and configure how Windows starts**.
It helps diagnose **startup and boot-related issues**.
**Note:** Local Administrator privileges are required to open MSConfig.

Open MSConfig:

```text
Win + R
↓
msconfig
```
<img width="665" height="467" alt="WhatsApp Image 2026-08-01 at 3 16 35 PM" src="https://github.com/user-attachments/assets/f2945a6c-2100-454d-a4f8-a470b38ad59e" />
<img width="812" height="617" alt="image" src="https://github.com/user-attachments/assets/8ada848d-9971-4255-9cbb-cd5e37e45140" />


Controls how Windows starts.

Startup modes:

- **Normal Startup** → Loads all drivers and services.
- **Diagnostic Startup** → Loads only essential drivers and services.
- **Selective Startup** → User chooses what Windows loads.

## 2️⃣ Boot

Controls **Windows boot options**.

Used to configure:

- Safe Mode
- Boot timeout
- Default operating system
- Boot logging
- Debugging options

 **Boot = How Windows loads before the login screen.**

## 3️⃣ Services

Displays all Windows services.
A **service** is a background application that runs without user interaction.

Examples:

- Windows Update
- Print Spooler
- Windows Defender

Services may be:

- Running
- Stopped

## 4️⃣ Startup

Shows applications configured to start automatically after user login.
**Note:** Modern Windows uses **Task Manager** to manage startup apps.
On **Windows Server**, startup programs can be viewed using:

```text
Win + R
↓
shell:startup
```
## 5️⃣ Tools

Provides shortcuts to useful Windows administration and troubleshooting tools.

Examples:

- Task Manager
- Command Prompt
- System Information
- Registry Editor


# 🖥️ Advanced System Settings

Open:

```text
Search
↓
View advanced system settings
```

Used to configure:

- Performance
- Virtual Memory (Page File)
- Startup & Recovery

## Page File (Virtual Memory)

A **Page File** is disk space used as **virtual memory** when physical RAM becomes full.

```text
RAM Full
    ↓
Windows Uses Page File
    ↓
Applications Continue Running
```

Information available:

- Drive location
- Initial size
- Maximum size
- Automatically managed or not

## Startup and Recovery

Used to configure Windows crash recovery.

If Windows crashes (BSOD), it can create a **Crash Dump** for analysis.

Crash dump types:

- Automatic Memory Dump
- Kernel Memory Dump
- Small Memory Dump (256 KB)
- Complete Memory Dump
- None

Crash dumps help administrators and security analysts determine the cause of system crashes.

### Cybersecurity Importance

MSConfig helps security professionals investigate:

- Windows startup configuration
- Boot configuration
- Background services
- Startup applications
- Windows troubleshooting tools

It is commonly used during **Windows incident response and forensic investigations**.

# Investigating Suspicious Startup Activity

## 1. Check MSConfig

```text
Win + R
↓
msconfig
```

Review:

- Services
- Startup configuration

Look for:

- Unknown services
- Suspicious entries

## 2. Check Startup Applications

Open:

```text
Ctrl + Shift + Esc
↓
Task Manager
↓
Startup Apps
```

Look for:

- Unknown applications
- Suspicious publishers
- Unnecessary startup programs

## 3. Check Startup Folder

```text
Win + R
↓
shell:startup
```

Also check:

```text
shell:common startup
```

Programs here automatically start when users log in.

## 4. Investigate Suspicious Files

Check:

- File location
- Publisher
- Digital Signature
- File Properties
- Creation Date
- Running Process

Never assume a file is malicious based only on its name.


## 5. Investigate Services

Open:

```text
Win + R
↓
services.msc
```

Review:

- Service Name
- Description
- Startup Type
- Status
- Executable Path

Look for unusual or unexpected services.


# 🔄 Investigation Workflow

```text
MSConfig
    ↓
Check Services
    ↓
Task Manager
    ↓
Startup Apps
    ↓
Startup Folder
    ↓
Investigate File
    ↓
Check Publisher & Digital Signature
    ↓
Determine if Legitimate or Suspicious
```

# 🎯 Key Takeaways

- **MSConfig** = Windows System Configuration utility.
- Used mainly for **startup troubleshooting**.
- Contains **General, Boot, Services, Startup, and Tools** tabs.
- **Boot** controls how Windows starts.
- **Services** show background applications.
- **Startup** controls applications that run after login.
- **Tools** provides shortcuts to Windows utilities.
- **Page File** = Virtual memory stored on disk.
- **Crash Dumps** help analyze Windows crashes.
- In cybersecurity, MSConfig helps investigate **startup behavior, services, and persistence mechanisms**.
```
```
# User Account Control (UAC)

UAC controls how Windows alerts users when **apps or users try to make system-level changes**.

Open:
`Control Panel → User Accounts → Change User Account Control settings`

## UAC Levels

| Level | Description |
|---|---|
| **Always Notify** | Highest security. Notifies for apps and user changes. Screen dims. |
| **Notify for Apps** | Default. Notifies when apps make changes. Screen dims. |
| **Notify Without Dimming** | Same as above, but screen does not dim. |
| **Never Notify** | Lowest security. No UAC notifications. **Not recommended.** |

### Key Point

 **Higher UAC level = More security notifications.**
The **UAC slider position** shows the current security level

<img width="948" height="737" alt="image" src="https://github.com/user-attachments/assets/5ab62b93-137a-45d5-93d6-ccd8ed3e9958" />

### Computer Management

**Computer Management (`compmgmt.msc`)** is a built-in Windows administration tool that provides access to different tools used to **manage, troubleshoot, and investigate a Windows system**.

Open it with:

```text
Win + R
↓
compmgmt.msc
```

It has **3 main sections**:

```text
Computer Management
├── System Tools
├── Storage
└── Services and Applications
```


### 🛠️ 1. System Tools

## 📅 Task Scheduler

**Task Scheduler** allows Windows to automatically run programs, scripts, or commands at a specified time or event.

A task can run:

- At system startup
- When a user logs in
- When a user logs off
- At a specific time
- Repeatedly (e.g., every 5 minutes)
- One time only

To view scheduled tasks:

```text
Computer Management
    ↓
System Tools
    ↓
Task Scheduler
    ↓
Task Scheduler Library
```

### Example

```text
SystemInfoDailyLog
        ↓
Runs every day at 10:00 AM
```

A task can also have a one-time trigger:

```text
At 2:50 PM on 6/15/2025
```

### 🔐 Cybersecurity Importance

Attackers can abuse **Scheduled Tasks** to achieve **persistence**.

For example:

```text
Attacker creates scheduled task
        ↓
Task runs automatically
        ↓
Malicious program executes
        ↓
Attacker maintains persistence
```

### 🔎 During Investigation

Check:

- Task name
- Trigger
- Program/command being executed
- Executable path
- Whether the task is legitimate

> **Key Point:** Task Scheduler helps answer: **"What programs or commands are configured to run automatically?"**

---

# 📋 Event Viewer

**Event Viewer** allows you to view events that have occurred on a Windows computer.

The logs act as an **audit trail** that can help you understand activity on the system.

It is useful for:

- Troubleshooting problems
- Investigating system activity
- Investigating security incidents
- Understanding what happened on a system

## Event Viewer has 3 panes

### Left Pane

Shows a hierarchical tree of event log providers and categories.

### Middle Pane

Shows a summary and list of events for the selected provider.

### Right Pane

Contains available actions for the selected event or log.

## Important Windows Logs

Common logs include:

- **Application** → Application-related events
- **Security** → Security-related events
- **System** → Windows system events

### 🔐 Cybersecurity Importance

Event Viewer can help answer:

- Who logged in?
- When did they log in?
- Were there failed login attempts?
- What errors occurred?
- What happened before or after an incident?

> **Key Point:** Event Viewer helps answer: **"What happened on this Windows system?"**

It is important for:

- Security monitoring
- Incident Response
- Digital Forensics
- Troubleshooting

---

# 📁 Shared Folders

**Shared Folders** shows folders that are shared over the network.

It contains 3 important sections:

### Shares

Shows folders and resources shared with other users.

Examples of default Windows administrative shares:

```text
C$
ADMIN$
```

### Sessions

Shows users who are currently connected to shared resources.

### Open Files

Shows files and folders currently being accessed by connected users.

You can right-click a shared folder and check its **properties and permissions**.

### 🔐 Cybersecurity Importance

Shared Folders help you understand:

- What resources are accessible over the network
- Who can access them
- Which users are currently connected
- Which files are being accessed

During an investigation, you may check for:

- Unnecessary shares
- Incorrect permissions
- Unexpected users
- Unauthorized access

> **Key Point:** Shared Folders helps answer: **"What resources can other users access over the network?"**

---

# 👤 Local Users and Groups

The **Local Users and Groups** section allows you to manage local:

- Users
- Groups
- Group membership
- User permissions

It is also available through:

```text
lusrmgr.msc
```

Users can belong to multiple groups.

When a user is added to a group, they inherit the permissions assigned to that group.

### 🔐 Cybersecurity Importance

User and group information helps answer:

- Who has access to the computer?
- Which accounts exist?
- Which users are administrators?
- Which groups does a user belong to?
- Does a user have unnecessary privileges?

Example:

```text
User
  ↓
Member of Administrators Group
  ↓
Administrator Privileges
```

> **Key Point:** Users & Groups helps answer: **"Who has access and what privileges do they have?"**

---

# 📊 Performance Monitor (PerfMon)

**Performance Monitor (`perfmon`)** is used to monitor system performance.

It can display performance data:

- In real time
- From previously recorded log files

It can help troubleshoot:

- CPU usage
- Memory usage
- Disk activity
- Network activity

It can monitor:

- Local computers
- Remote computers

### 🔐 Cybersecurity Importance

Performance monitoring can help identify unusual system behavior.

Example:

```text
CPU Usage = 100%
        ↓
Investigate processes
        ↓
Find which program uses CPU
        ↓
Determine if legitimate or suspicious
```

> **Key Point:** Performance Monitor helps answer: **"What is the computer doing and how are its resources being used?"**

---

# 🖥️ Device Manager

**Device Manager** allows you to view and configure hardware devices connected to the computer.

Examples:

- Network adapters
- Hard drives
- Display adapters
- Keyboards
- Mice
- USB devices

You can also disable or configure hardware devices.

### 🔐 Cybersecurity Importance

Device Manager helps you understand the **hardware configuration** of a system.

You can investigate:

- What hardware is installed?
- What network adapters exist?
- Are any devices disabled?
- Are there hardware-related issues?

> **Key Point:** Device Manager helps answer: **"What hardware exists on this computer?"**

---

# 💾 2. Storage

## Disk Management

**Disk Management** is a Windows utility used to manage disks, drives, and partitions.

You can:

- Set up a new drive
- Create partitions
- Extend partitions
- Shrink partitions
- Assign drive letters
- Change drive letters

Example:

```text
Disk 0
├── C: Windows
├── D: Data
└── E: Other Storage
```

### 🔐 Cybersecurity Importance

Disk Management helps you understand:

- Which disks exist
- How partitions are organized
- Where Windows is installed
- Whether additional storage is present

> **Key Point:** Disk Management helps answer: **"How is storage organized on this computer?"**

---

# ⚙️ 3. Services and Applications

## Services

A **Windows Service** is a special type of application that runs in the background.

Services can perform important functions without requiring a user to interact with them.

You can view:

- Display name
- Service name
- Status
- Executable path
- Startup type

To see more information:

```text
Right-click Service
        ↓
Properties
```

---

## 🚀 Service Startup Types

### Automatic

The service starts automatically when Windows boots.

```text
Windows Boots
    ↓
Service Starts Automatically
```

### Manual

The service starts only when another process or user triggers it.

### Disabled

The service cannot start.

---

### 🔐 Cybersecurity Importance

Attackers can abuse Windows Services to achieve **persistence**.

For example:

```text
Attacker creates/abuses a service
        ↓
Service configured as Automatic
        ↓
Windows boots
        ↓
Service starts
        ↓
Malicious program runs
```

During an investigation, check:

- Service name
- Display name
- Executable path
- Startup type
- Publisher
- Whether the service is expected

> **Key Point:** Services help answer: **"What programs are running in the background, and what starts automatically?"**

---

# 🧩 WMI Control

**WMI = Windows Management Instrumentation**

WMI is a Windows technology that allows computers and servers to be **managed and monitored locally or remotely**.

WMI can be used through:

- PowerShell
- Scripts
- WMI commands
- Administrative tools

WMI can be used to:

- Gather system information
- Manage Windows systems
- Perform administrative tasks
- Manage computers remotely

### 🔐 Cybersecurity Importance

WMI is a legitimate Windows technology, but attackers can also abuse it.

It can potentially be used for:

- Remote administration
- Command execution
- System information gathering
- Persistence

This teaches an important cybersecurity concept:

> **A legitimate Windows feature can be used for both legitimate administration and malicious purposes.**

---

# 🔍 Computer Management from a Cybersecurity Perspective

When investigating a potentially compromised Windows computer, Computer Management provides useful places to investigate.

## Investigation Questions

### 📅 Task Scheduler

> **Are there suspicious tasks configured to run automatically?**

Check:

- Task name
- Trigger
- Command
- Executable path

---

### 📋 Event Viewer

> **What happened on the system?**

Check:

- Login activity
- Failed logins
- System events
- Application events
- Security events

---

### 👤 Users & Groups

> **Who has access to the system?**

Check:

- User accounts
- Administrator accounts
- Group memberships
- Excessive privileges

---

### 📁 Shared Folders

> **What can other users access over the network?**

Check:

- Shared folders
- Permissions
- Active sessions
- Open files

---

### ⚙️ Services

> **Are there suspicious background services?**

Check:

- Service name
- Executable path
- Startup type
- Publisher

---

### 📊 Performance Monitor

> **Is the system behaving unusually?**

Check:

- CPU usage
- Memory usage
- Disk activity
- Network activity

---

### 💾 Disk Management

> **How is the storage organized?**

Check:

- Disks
- Partitions
- Drive letters
- Additional storage


<img width="837" height="482" alt="image" src="https://github.com/user-attachments/assets/04155175-67c7-4180-a0a2-ae0c8a8aa1b8" />

# 🧠 Quick Summary

| Tool | Main Question |
|---|---|
| **Task Scheduler** | What runs automatically? |
| **Event Viewer** | What happened on the system? |
| **Shared Folders** | What is accessible over the network? |
| **Users & Groups** | Who has access and privileges? |
| **Performance Monitor** | What is the system doing? |
| **Device Manager** | What hardware exists? |
| **Disk Management** | How is storage organized? |
| **Services** | What runs in the background? |
| **WMI** | How can Windows be managed programmatically? |

---

# 🎯 Main Cybersecurity Takeaway

**Computer Management is like a control room for a Windows computer.**

As a cybersecurity learner, the goal is to know **where to look when investigating a Windows system**.

```text
Possible Compromise
        ↓
Task Scheduler → Check persistence
        ↓
Event Viewer → Check what happened
        ↓
Users & Groups → Check who has access
        ↓
Shared Folders → Check network access
        ↓
Services → Check background processes
        ↓
Performance Monitor → Check unusual behavior
        ↓
Disk Management → Understand storage
        ↓
WMI → Understand Windows management activity
```

> **Key Concept:** Computer Management is important for **Windows administration, troubleshooting, SOC analysis, incident response, and digital forensics** because it gives you multiple places to understand and investigate the Windows environment.
