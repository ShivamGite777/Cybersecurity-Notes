### Windows Desktop & GUI

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

### Windows User Accounts, Profiles & Groups

## User Account Types

A typical local Windows system has two main types of user accounts:

## Administrator

An **Administrator** has permissions to make system-level changes.

An Administrator can:

- Add users
- Delete users
- Modify groups
- Change system settings
- Perform other administrative tasks

## Standard User

A **Standard User** has limited permissions.

A Standard User can:

- Manage their own files and folders
- Make changes to files/folders they have permission to access

A Standard User generally **cannot perform system-level changes**, such as installing programs that require administrator privileges.


#  Checking User Accounts

One way to view local user accounts is through **Other Users** in Windows Settings.

### Steps:

```text
Start Menu
    ↓
Search "Other Users"
    ↓
Open "Other Users" Settings
```
## 3. User Profiles

When a user account is created, Windows creates a user profile for that user.

# User profiles are stored under:

C:\Users

# For example, if the username is Max:

C:\Users\Max
## 4. User Profile Creation

The user profile is created when the user logs into the computer for the first time.
During the first login, Windows may display messages related to:
# User Profile Service

## 5. Local Users and Groups Management

Windows also provides a tool called:
Local Users and Groups Management
You can open it using:

Windows Key + R

Then type:

lusrmgr.msc

Press Enter.

## 6. Users and Groups

Inside lusrmgr.msc, you will find two main folders:

Local Users and Groups
│
├── Users
└── Groups


# Users

The Users section contains the local user accounts on the computer.

# Groups

The Groups section contains local groups.


## 7. Groups and Permissions

Instead of giving permissions to every user individually, Windows can use groups.
An Administrator can add users to groups.
When a user is added to a group:

# The user inherits the permissions assigned to that group.

For example:

Group: Administrators
        ↓
Permissions assigned to group
        ↓
User added to group
        ↓
User inherits those permissions

A user can also belong to multiple groups.

.
## Simple Example

Imagine a company computer:

Administrator
     │
     ├── Creates User: Max
     │
     └── Adds Max to a Group
              │
              ↓
       Max inherits Group permissions

# This is why groups are important in cybersecurity. Instead of managing permissions for every user separately, administrators can manage permissions at the group level. 

## Windows needs to know:

Who are you? → User Account
What are you allowed to do? → Permissions
What resources can you access? → Groups & Permissions

# Example
User Account
     ↓
Administrator / Standard User
     ↓
User belongs to Groups
     ↓
Groups have Permissions
     ↓
User gets access based on Permissions
Why is this important in cybersecurity?

# Imagine an attacker gets access to a Standard User account. Their abilities may be limited.

But if they manage to gain access to an Administrator account or add themselves to a privileged group, they may be able to:

-Install malicious software
-Create or delete accounts
-Change security settings
-Access sensitive files
-Disable security tools

# Concept
-Administrator	High-level privileges
-Standard User	Limited privileges
-User Profile	Personal environment and files of a user
-C:\Users	Where user profiles are stored
-Groups	Used to manage permissions for multiple users
-Permissions	Define what users can access or change
-lusrmgr.msc	Tool for managing local users and groups
# Hands-on
<img width="1013" height="907" alt="image" src="https://github.com/user-attachments/assets/717665d8-2bec-4bcd-b451-5648c668e762" />

# What is the name of the other user account?
<img width="987" height="813" alt="image" src="https://github.com/user-attachments/assets/20c1e777-ac5c-42d0-9902-2ed4ba1bc4d8" />
<img width="1047" height="927" alt="image" src="https://github.com/user-attachments/assets/6c8c6c27-7e64-493f-96f6-742881d2046f" />

<img width="985" height="802" alt="image" src="https://github.com/user-attachments/assets/b17cd9a2-9a69-4806-91e4-44d9911691e3" />


# What groups is this user a member of?
<img width="1023" height="918" alt="image" src="https://github.com/user-attachments/assets/0bc4397f-b6ee-4b13-b0e2-deeb56c52554" />\

# What built-in account is for guest access to the computer?
<img width="1031" height="912" alt="image" src="https://github.com/user-attachments/assets/04b1f2ff-18dd-43b8-a040-ae88a83bac14" />

# What is the account description?
<img width="947" height="753" alt="image" src="https://github.com/user-attachments/assets/5b358c66-509d-44af-96a1-c65581914e77" />

### User Account Control (UAC)

**UAC** stands for **User Account Control**.

It is a Windows security feature that helps prevent **unauthorized or malicious changes** to the system.


## Administrator Accounts

An **Administrator** has high-level privileges and can make system-level changes.

An Administrator can:

- Install programs
- Change system settings
- Modify system files
- Add or delete users
- Modify groups

## Security Risk

If malware runs under an Administrator account, it may run with the user's permissions and potentially make changes to the system.

```text
Administrator User
        ↓
Runs Malware
        ↓
Malware runs with user's permissions
        ↓
May make system changes
```

### Windows Account Types & UAC

## Standard User
The user does NOT have Administrator privileges.
When they try the same privileged action:
        ↓
Tries to perform privileged action
        ↓
UAC asks for Administrator credentials
        ↓
Administrator username + password
        ↓
Correct credentials
        ↓
Action runs with Administrator privileges

 The Standard User needs someone with Administrator privileges to authenticate.

## Built-in Administrator

- A special **Administrator** account built into Windows.
- Has very high-level privileges.
- By default, **UAC does not apply to this account in the same way** as it does to normal Administrator accounts.
- Normally does not receive the standard UAC consent prompt for privileged actions.
- If an attacker gains access to this account, they may have significant control over the system.
- Therefore, this account should be carefully protected.

##  Normal Administrator

- A regular user account that is a member of the **Administrators group**.
- Has administrative privileges.
- **UAC is normally enabled**.
- When an action requires elevated privileges, a UAC prompt may appear.
- The user must approve the action to run it with elevated privileges.

```text
Normal Administrator
        ↓
Privileged Action
        ↓
UAC Prompt
        ↓
User Approves
        ↓
Action Runs
```
<img width="982" height="577" alt="image" src="https://github.com/user-attachments/assets/22c27347-99cc-408e-b912-c238a157175f" />
<img width="987" height="238" alt="image" src="https://github.com/user-attachments/assets/4e1d3043-bc48-481c-967d-d1f39321eccf" />

# ⚙️ Settings & Control Panel

- **Settings** → Modern Windows interface for changing common system settings.
- **Control Panel** → Older interface for advanced and traditional system settings.

### Examples

**Settings:**
- Network & Internet
- Accounts
- Personalization
- Windows Update
- <img width="557" height="744" alt="image" src="https://github.com/user-attachments/assets/ce9fc9bc-d97f-45dd-b894-065d545a686f" />

**Control Panel:**
- Programs and Features
- User Accounts
- Network settings
- Devices and Printers
- <img width="725" height="323" alt="image" src="https://github.com/user-attachments/assets/f245ec6f-f1ac-4439-9280-62be9e317b01" />

## Settings is the modern interface; Control Panel provides many traditional/advanced options.
