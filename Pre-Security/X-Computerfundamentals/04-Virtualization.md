# VIRTUALIZATION

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


