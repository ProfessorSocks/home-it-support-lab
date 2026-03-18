# VirtualBox Setup

## Goal

Set up Oracle VirtualBox and prepare the environment for building a virtualized IT support lab.

The lab will simulate a small business network using multiple virtual machines running different operating systems.

---

## What is Virtualization

Virtualization allows multiple operating systems to run on a single physical computer.

Each virtual machine behaves like a separate computer with its own:

- CPU allocation
- RAM allocation
- storage disk
- operating system
- network interface

This allows safe experimentation without affecting the host system.

---

## Why Virtualization is Used in IT

Virtualization is widely used in enterprise environments for:

- server consolidation
- testing environments
- training labs
- disaster recovery
- software testing
- infrastructure simulation

Using virtual machines allows IT professionals to safely test configurations and troubleshoot problems.

---

## Virtualization Software Used

This lab uses:

Oracle VirtualBox

VirtualBox allows creation and management of virtual machines on a local computer.

Features used in this lab include:

- VM creation
- ISO-based OS installation
- virtual networking
- snapshots
- resource management

---

## Host System Specifications

Host computer used for the lab:

RAM: 32 GB  
CPU: Intel Core i7  
Storage: sufficient free disk space

These resources allow multiple virtual machines to run simultaneously.

---

## Planned Virtual Machines

| Machine  | OS                  | Role                 |
| -------- | ------------------- | -------------------- |
| DC01     | Windows Server 2022 | Domain Controller    |
| CLIENT01 | Windows 10          | Workstation          |
| LINUX01  | Ubuntu Server       | Linux administration |

Additional machines may be added later.

---

## Resource Allocation Plan

### DC01

RAM: 8 GB  
CPU: 2 cores  
Storage: 60 GB

### CLIENT01

RAM: 6 GB  
CPU: 2 cores  
Storage: 50 GB

### LINUX01

RAM: 4 GB  
CPU: 2 cores  
Storage: 25 GB

---

## Virtual Networking Concept

VirtualBox provides several network modes.

This lab will primarily use:

NAT networking

NAT allows virtual machines to access the internet while remaining isolated from the host network.

Benefits:

- safe experimentation
- no interference with home network
- internet access for updates

Later phases may explore additional networking modes.

---

## VM Snapshots

Snapshots allow saving the state of a virtual machine.

This allows rollback if something breaks.

Example snapshot workflow:

1. clean OS install
2. snapshot
3. configuration changes
4. new snapshot

If a mistake occurs, the VM can be restored instantly.

---

## Safety Considerations

Virtual machines run in an isolated environment.

Even if the operating system inside the VM becomes corrupted, the host system remains unaffected.

If a virtual machine becomes unusable it can simply be deleted and recreated.

---

## Next Step

Create the first virtual machine and install Windows Server.

This machine will later become the domain controller for the lab environment.
