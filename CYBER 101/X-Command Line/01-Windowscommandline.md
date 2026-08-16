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

---

# Connecting to the Target Machine Using SSH

From the TryHackMe AttackBox, open the terminal and connect using:

    ssh user@10.48.128.86

Credentials:

- **Username:** `user`
- **Password:** `Tryhackme123!`

## First-Time SSH Connection

The first time you connect, SSH will ask if you trust the target machine.

Type:

    yes

Then enter the password.

> Note: The password will not be visible while typing.

---

# Windows PATH

Windows uses the **PATH environment variable** to know where to look for executable commands.

Check environment variables using:

    set

Look for:

    Path=C:\Windows\system32;C:\Windows;...

Commands located in directories listed in the `PATH` can usually be executed without specifying their full path.

---

# `ver`

Displays the Windows operating system version.

Command:

    ver

Example output:

    Microsoft Windows [Version 10.0.17763.1821]

---

# `systeminfo`

Displays detailed information about the system.

Command:

    systeminfo

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

---

# `driverquery`

Displays information about installed device drivers.

Command:

    driverquery

The output can be long.

---

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

---

# `cls`

Clears the Command Prompt screen.

Command:

    cls

---

# Quick Command Summary

| Command | Description |
|---|---|
| `set` | Displays environment variables, including `PATH` |
| `ver` | Displays the Windows version |
| `systeminfo` | Displays detailed system information |
| `driverquery` | Displays installed device drivers |
| `driverquery \| more` | Displays output page by page |
| `help` | Displays help information |
| `command /?` | Displays help for a specific command |
| `cls` | Clears the Command Prompt screen |
| `ssh user@IP` | Connects to a remote machine using SSH |

---

# Quick Summary

- **GUI** → Uses graphical elements such as windows and icons
- **CLI** → Uses typed commands
- **CLI advantages** → Faster, lightweight, automatable, and useful for remote management
- **`cmd.exe`** → Windows Command Prompt
- **PATH** → Directories where Windows searches for executable commands
- **`ver`** → Shows Windows version
- **`systeminfo`** → Shows detailed system information
- **`driverquery`** → Lists installed drivers
- **`| more`** → Shows long output page by page
- **`help`** → Displays command help
- **`cls`** → Clears the terminal
