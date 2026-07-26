### Windows Desktop & GUI

## Overview

The **Windows Desktop** is the main screen shown after logging into a Windows computer.

**GUI (Graphical User Interface)** allows users to interact with Windows using icons, menus, buttons, and windows instead of commands.

Before accessing the Desktop, users usually need to enter valid **username and password** credentials.

## Main Components

# 1. Desktop
The main workspace where you can find:
- Files
- Folders
- Shortcuts
- Applications

Right-clicking the Desktop opens a **Context Menu** with options like:
- Create new files/folders
- Arrange icons
- Display Settings
- Personalize

# 2. Start Menu
Provides quick access to:
- Installed applications
- Recently added programs
- Settings
- Documents & Pictures
- User account options
- Power options

Apps can be added using **Pin to Start**.

# 3. Taskbar
Usually located at the bottom of the screen.

Used to:
- Access open applications
- Launch pinned applications
- Switch between application
- Hovering over an app icon can show a preview.

# 4. Notification Area
Usually located at the bottom-right of the screen.

Commonly displays:
- Date & Time
- Volume
- Network/Wi-Fi
- Battery

# 5. Display Settings
Used to configure:
- Screen resolution
- Screen orientation
- Multiple monitors

# 6. Personalize
Used to customize the Windows appearance:
- Background/Wallpaper
- Colors
- Themes
- Fonts

# Context Menu

A **Context Menu** appears when you right-click an item.

It provides actions related to that item, such as:
- Open
- Copy
- Rename
- Delete
- Properties

## Cybersecurity Relevance

Understanding the Windows GUI is important for cybersecurity because security professionals often work with Windows systems.

It provides the foundation for learning:
- Windows Administration
- Command Prompt
- PowerShell
- Windows Security
- Security Investigations

##  Key Takeaways

- **GUI** = Graphical User Interface
- **Desktop** = Main workspace
- **Start Menu** = Access apps and system options
- **Taskbar** = Manage open and pinned applications
- **Notification Area** = System status information
- **Display Settings** = Configure screens
- **Personalize** = Customize appearance
- **Right-click** = Open Context Menu



### Windows File Systems: FAT & NTFS

##  What is a File System?

A **file system** is used by an operating system to store, organize, and manage files and folders on a storage device.

The file system used by modern versions of Windows is **NTFS**

## FAT

**FAT** stands for **File Allocation Table**.

Before NTFS, Windows used file systems such as:

- **FAT16**
- **FAT32**
- **HPFS (High Performance File System)**

# FAT Today

FAT-based file systems are still commonly found on:

- USB devices
- MicroSD cards
- Memory cards

However, FAT is traditionally **not used for Windows installations** on modern personal computers, laptops, or Windows servers.


## NTFS

**NTFS** stands for **New Technology File System**.

NTFS is the main file system used by **modern Windows installations**.

For example, the Windows operating system is typically installed on the **C: drive**:

```text
C:\ → NTFS
```
## File System
    ↓
Manages files and folders
    ↓
Modern Windows → NTFS
    ↓
Features:
├── Supports large files
├── File & folder permissions
├── Compression
├── Encryption (EFS)
└── Journaling


## NTFS Journaling

NTFS is known as a **journaling file system**.

In case of a system failure, NTFS can automatically repair folders and files on the disk using information stored in a **log file (journal)**.

This journaling feature is **not possible with FAT**.

### Simple Flow

```text
System Failure
      ↓
NTFS checks the Journal (Log File)
      ↓
Uses the stored information
      ↓
Helps repair the File System
<img width="1002" height="635" alt="image" src="https://github.com/user-attachments/assets/b8dc2068-d3f6-401e-8f15-cba8aa646a02" />
```
## File Permission


<img width="723" height="507" alt="image" src="https://github.com/user-attachments/assets/7615891d-ea95-4261-b057-d84d53f7972c" />
## Alternate Data Streams (ADS)

# What is ADS?

**ADS (Alternate Data Streams)** is a file attribute specific to the **Windows NTFS (New Technology File System)**.

Every file has at least one data stream:

```text
$DATA
File
├── Main Data Stream ($DATA)
└── Alternate Data Stream (ADS)
```
# ADS (Alternate Data Streams) is a feature of the NTFS file system that allows a file to store extra data that is not normally visible in Windows File Explorer.

# Simple example:

Imagine you have:

# photo.jpg

Normally, it contains:

# photo.jpg → Main image data

With ADS, it can also have hidden extra data:

photo.jpg
├── Main data → The actual image
└── ADS → Additional hidden data



### Windows Folder & System32

## Windows Folder

The **Windows folder** contains important files required by the Windows operating system.

The traditional location is:

```text
C:\Windows
```
# %windir% → Environment variable representing the Windows directory.
<img width="782" height="589" alt="image" src="https://github.com/user-attachments/assets/48f8120f-e373-4c25-a7da-b36a345dfd22" />
# Why use %windir%?

Because Windows might not always be installed on the C: drive.

For example:

- D:\Windows

In that case:

- %windir% = D:\Windows

## Why is System32 Important in Cybersecurity?

System32 is important because it contains many **critical Windows system files and tools** used by cybersecurity professionals.

- 🔍 **Security Investigations** → Analysts may examine System32 when investigating compromised Windows systems.
- 🦠 **Malware Detection** → Attackers may disguise malware as legitimate Windows files, so knowing normal system files helps detect suspicious activity.
- 🕵️ **Digital Forensics** → Investigators may examine System32 files for evidence of attacks or unauthorized changes.
- 🛠️ **Security Tools** → System32 contains important tools such as `cmd.exe`, `ipconfig.exe`, `netstat.exe`, and `whoami.exe`.
- ⚙️ **System Administration** → Understanding these tools helps security professionals manage and investigate Windows systems.

## Key Takeaway

Understanding **System32** helps cybersecurity professionals investigate Windows systems, detect malware, analyze attacks, and perform digital forensics.

 **Warning:** Do not randomly delete or modify System32 files because they are critical to Windows and doing so can make the operating system unusable.

<img width="1252" height="630" alt="image" src="https://github.com/user-attachments/assets/18ca9dee-ea1e-4289-9f3a-86cb52e27db5" />

