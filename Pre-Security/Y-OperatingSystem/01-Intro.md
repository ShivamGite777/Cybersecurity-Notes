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

