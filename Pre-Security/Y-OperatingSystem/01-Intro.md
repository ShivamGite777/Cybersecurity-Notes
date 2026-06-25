### Operating System (OS)

## What is an Operating System?

An Operating System (OS) is system software that acts as a bridge between the user, applications, and computer hardware.

Examples:
 Windows
 Linux
 macOS

# Airport Analogy

 Hardware = Airport infrastructure
 Applications = Airlines & passengers
 Operating System = Air Traffic Control

The OS manages and coordinates everything.

# System Privilege Layers

## Kernel Space

Core part of the OS
Direct access to hardware
Manages CPU, RAM, storage, and devices
Highest privileges

## User Space

Runs applications
Cannot access hardware directly
Uses system calls to request services from the kernel

# Building on our airport analogy, let's zoom in on the concept of privilege separation. The kernel space is the control tower, a strictly secured area where only trusted air-traffic controllers (the kernel) work. They alone can directly control the runways, radar, and other hardware. Applications in the user space are like airlines and passengers on the ground. They can't enter the tower or touch the equipment. Instead, they radio requests (system calls) to the tower, which handles them safely. This separation keeps the OS reliable: one faulty app can't crash the whole system, just as no airline can operate safely without the tower's control.


## Operating System Duties

# Process Management

 Creates and manages programs
 Allocates CPU time

Example:
 Running browser and music player together

# Memory Management

  Allocates RAM
  Protects process memory
  Uses virtual memory when RAM is low

# File System Management

 Organizes files and folders
 Handles permissions and metadata

Example:
Creating folders
Saving files


# User Management

 Manages user accounts
 Handles authentication and permissions

Example:
 Logging in with a password


## Device Management

Manages hardware devices using drivers

Example:
Connecting a mouse or printer

<img width="1620" height="593" alt="image" src="https://github.com/user-attachments/assets/e5718e8f-5e3b-427a-b35e-f3d4ee2bab2b" />


## Operating System Security

# Authentication

 Verifies user identity
 Passwords and biometrics

# Permissions

 Controls access to files and resources

# Isolation

Separates processes using Kernel/User Space

# System Protection

 Protects critical system files

 ### GUI (Graphical User Interface)

GUI allows users to interact with the computer using graphics such as icons, windows, buttons, and menus.

## Features
 Easy to use
 Visual interface
 Uses mouse and keyboard

## Examples
 File Explorer
 Desktop
 Settings App

### CLI (Command-Line Interface)

CLI allows users to interact with the computer by typing commands.

## Features
 Text-based interface
 Faster for advanced tasks
 Requires command knowledge

## Examples
bash
ls
cd
pwd

### Windows Overview

## Windows Evolution
  
  Early  computers used **MS-DOS** (command-line only).
 In 1985, Microsoft released **Windows 1.0**.
 Introduced GUI with windows, menus, and mouse support.
 Modern Windows evolved from these early versions.

# Authentication

Authentication = Verifying user identity before accessing Windows.

Methods:
Password
PIN
Biometrics

## Account Types

### Guest
 Temporary access
 Limited permissions

### Standard User
Everyday use
 Cannot make system-wide changes

### Administrator
 Full system control
 Can install software
 Manage users and settings


# Windows Desktop

The Desktop is the main workspace after login.

## Main Components

### Desktop
 Contains files, folders, and shortcuts

### Taskbar
 Quick access to apps and system tools


# Desktop Features

### Desktop Icons
 Shortcuts to apps and folders

### Start Menu
 Open apps, settings, and power options

### Search
 Find files, folders, apps, and settings

### Task View
 Shows all open windows

### Pinned Apps
 Frequently used applications

### Network & Audio
 Internet and sound settings

### Date & Time
 Calendar and clock

### Notifications
 System and application alerts
 
# Start Menu

The Start Menu is the central access point in Windows.

Used for:
 Applications
 Settings
  Files
 Power options

 
## Built-in Windows Tools
# Notepad
 Text editor

# File Explorer
 File and folder management

# Calculator
 Calculations

# Paint
 Basic image editing

## About Your PC

Displays system information:

 Device Name
 CPU
 RAM
 Windows Version
 System Type

## File Explorer

Used to manage files and folders.

Functions:
 Open files
 Create folders
 Copy/Move files
 Search files

## Folder Structure

Windows uses a hierarchical folder structure.

Example:

C:\Users\Administrator\Desktop

Folders can contain:
 Files
 Subfolders

Common Locations:
 Desktop
 Documents
 Downloads

## File Path

A file path shows the location of a file or folder.

Example:

C:\Users\Administrator\Desktop\TryHatMe Onboarding


## Applications in Windows can be installed either through the Microsoft Store or by downloading installer files (.exe/.msi) from trusted websites. 
## Uninstalling is the process of removing an application from Windows using Settings, Control Panel, Microsoft Store, or the application's own uninstaller.



## Windows Defender Firewall
Windows Defender Firewall is a built-in firewall designed to help protect your computer from unauthorized network traffic. It monitors network connections and applies rules that determine whether the connections are allowed or denied. The firewall operates on different network profiles, allowing you to create custom rules or specify applications that are permitted.

Domain: Used when a system is connected to an organization’s domain network
Private: Intended for trusted networks, such as a home or lab environment 
Public: Used for untrusted networks, such as public Wi-Fi

<img width="1048" height="424" alt="image" src="https://github.com/user-attachments/assets/b83bf262-f22e-4628-ba2c-5d02a6e93629" />


### Windows Defender Firewall

Firewall = Controls network traffic entering and leaving a computer.

## Inbound Rules
 Control incoming traffic.
Example: Remote Desktop.

## Outbound Rules
 Control outgoing traffic.
  Example: Browser accessing the internet.

## Connection Security Rules
 Secure communication between devices.
 Uses authentication and encryption.

## Rule Information
 Name
 Group
  Network Profile (Public/Private/Domain)
 Status (Enabled/Disabled)
 Action (Allow/Block)

## Functions
 Create new rules.
 Edit existing rules.
 Filter rules.


<img width="520" height="185" alt="image" src="https://github.com/user-attachments/assets/fc7d89f8-a2c3-4512-93bb-5721d17759fe" />

