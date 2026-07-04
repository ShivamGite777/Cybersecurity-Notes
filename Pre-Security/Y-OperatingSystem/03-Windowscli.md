
### Windows CLI Basics — Navigation Notes

##  Goal

Learn how to navigate the Windows file system using the Command Prompt (CLI).

#  What is the Windows Terminal?

The **Windows Terminal (Command Prompt)** is a text-based interface used to interact with Windows.
 
## Why use CLI?

  Faster than using the GUI
  Gives more control
  Many cybersecurity tools only work in the terminal


# 1. Check Current Directory

## Command

```cmd
cd
```

## Purpose

Displays your current working directory (location).

## Example

```cmd
C:\Users\Administrator
```

## 2. List Files and Folders

# Command

```cmd
dir
```

## Purpose

Lists all visible files and folders in the current directory.

## 3. View Hidden Files

# Command

```cmd
dir /a
```

## Purpose

Displays **all files and folders**, including hidden ones.

> **Note:** Hidden ≠ Secret. Windows simply hides them by default.

## 4. Change Directory

## Go to a folder

```cmd
cd Documents
```

## Go back one folder

```cmd
cd ..
```

## Purpose

Navigate through the Windows file system.

## 5. Search for a File

## Command

```cmd
dir /s task_brief.txt
```

## Purpose

Searches for **task_brief.txt** in the current directory and all subfolders.

> `/s` = Search all subdirectories.

## 6. Navigate to the File

# Command

```cmd
cd <folder_path>
```

## Verify file exists

```cmd
dir
```

## 7. Read File Contents

# Command

```cmd
type task_brief.txt
```

# Purpose

Displays the contents of a text file.

#  Important Commands Summary

| Command | Purpose |
|----------|---------|
| `cd` | Show current directory |
| `cd folder` | Open a folder |
| `cd ..` | Go back one directory |
| `dir` | List files and folders |
| `dir /a` | Show hidden files/folders |
| `dir /s filename` | Search for a file recursively |
| `type filename` | Display file contents |

##  Workflow

```text
cd
        ↓
dir
        ↓
dir /a
        ↓
cd <folder>
        ↓
dir /s task_brief.txt
        ↓
cd <file_folder>
        ↓
type task_brief.txt

###  Windows CLI Basics — Gathering System Information

##  Goal

Learn how to collect basic system information using Windows Command Prompt.

 ### 1. Check Current User

## Command

```cmd
whoami
```

## Purpose

Displays the username of the currently logged-in user.

---

### 2. Check Computer Name

## Command

```cmd
hostname
```

### Purpose

Displays the computer (host) name.

# 3. View Windows System Information

### Command

```cmd
systeminfo
```

### Purpose

Displays detailed information about the Windows system.

### Important Fields

 **OS Name** → Windows edition
 **OS Version** → Windows version/build
 **System Type** → 32-bit or 64-bit architecture

### 4. Check Network Information

## Command

```cmd
ipconfig
```
<img width="542" height="207" alt="image" src="https://github.com/user-attachments/assets/5eca8270-8feb-4892-b1c2-b15045592243" />

## Purpose

Displays the network configuration of the computer.

### Important Information

 **IPv4 Address** → Computer's IP address
 **Default Gateway** → Router/Gateway IP address


# Important Commands Summary

| Command | Purpose |
|----------|---------|
| `whoami` | Show current username |
| `hostname` | Show computer name |
| `systeminfo` | Display Windows system information |
| `ipconfig` | Display network configuration |

##  Workflow

```text
whoami
      ↓
hostname
      ↓
systeminfo
      ↓
ipconfig


## Why These Commands Matter

These are some of the first commands used by:

 Cybersecurity Analysts
 System Administrators
 IT Support Engineers

They help identify:

 Current user
 Computer name
 Windows version
 Network connectivity
