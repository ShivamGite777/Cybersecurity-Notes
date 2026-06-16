<img width="731" height="470" alt="image" src="https://github.com/user-attachments/assets/5288382e-e8cd-4f85-be8c-5abfef84d8c1" /># VIRTUALIZATION

## Before Virtualization

Rule:

"One Server = One Application"

Examples:

1 Server → Website
1 Server → Database
1 Server → Email Service

### Problems

 High Cost
 Low Resource Utilization
 Slow Deployment
 Difficult to Scale

## What is Virtualization?

Virtualization allows multiple virtual computers to run on a single physical server.

Purpose:
 Better resource utilization
 Lower cost
 Easier management

## Hypervisor

Definition:

A hypervisor is software that manages and allocates resources to Virtual Machines (VMs).

Purpose:
Creates VM
Distributes CPU, RAM, and Storage
keeps VMs isolated from each other

## Virtual Machine (VM)

Definition:

A VM is a virtual computer that runs on a physical server.
Each VM acts like an independent computer.
Features:
 Own Operating System
 Own Applications
 Own Settings
  
## Building Analogy

Physical Server = Building

Virtual Machines (VMs) = Apartments

Applications/OS = Tenants

Hypervisor = Building Manager

## Example of Virtualization

Suppose you have one Physical Server (real computer).

The Hypervisor creates 3 Virtual Machines (VMs):

Physical Server
├── VM 1 (Windows)
├── VM 2 (Linux)
└── VM 3 (Ubuntu)

## Share the Same Hardware

All VMs use the hardware of the same Physical Server.

Shared Hardware:
CPU
RAM
Storage
Network Card
## Each virtual computer, known as a Lab Machine (VM), acts as an independent system with its own operating system, apps, and settings, even though they all share the same physical hardware underneath.



### Types of Hypervisors

## Type 1 Hypervisor (Bare-Metal)
Runs directly on hardware.

Architecture:

Hardware
   ↓
Hypervisor
   ↓
VMs
# Characteristics

High performance
More secure
Used in servers and data centers

# Examples

VMware ESXi
Microsoft Hyper-V
Xen

# Use Cases

Production servers
Database servers
Data centers

### Type 2 Hypervisor (Hosted)
Runs inside an existing operating system.

Architecture:

Hardware
   ↓
Host OS
   ↓
Hypervisor
   ↓
VMs
# Characteristics

Easy to install
Suitable for learning and testing

# Examples

Oracle VirtualBox
VMware Workstation

# Use Cases

Kali Linux labs
Software testing
Malware analysis


### Containers

# Definition

A Container is a lightweight, isolated environment that packages:

 Application
 Dependencies
 Libraries
 Configuration files

Unlike VMs, containers share the host operating system kernel.
<img width="731" height="470" alt="image" src="https://github.com/user-attachments/assets/b4363c66-6f7c-4322-b8f8-d6b37783faf8" />

# Containers must match the host operating system type.

Example:

 Linux Host → Linux Containers ✅
 Linux Host → Windows Containers ❌

### Docker
Docker is an open-source platform used to build, deploy, and manage containers.
It allows applications to run inside containers, making them portable and consistent across different systems
### Example

Suppose you create a Flask website.
Without Docker:

Install Python
Install Flask
Install Dependencies
Configure Server
Run App

With Docker:
Build Docker Image
↓
Upload Image
↓
Server Downloads Image
↓
Run Container
↓
Website Live
# Language = Python
 Framework = Flask
 Application = Your Website
