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
