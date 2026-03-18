# Virtual Machine Creation

## Goal

Create the first virtual machine that will act as the domain controller for the lab environment.

This machine will later host Active Directory Domain Services and manage authentication for the lab network.

---

## Virtual Machine Name

DC01

The naming convention used in the lab follows typical enterprise server naming practices.

Example:

DC01 – Domain Controller  
FS01 – File Server  
WEB01 – Web Server

---

## Virtual Machine Platform

Oracle VirtualBox

VirtualBox is used to simulate multiple computers on a single host machine.

---

## VM Configuration

Operating System:

Windows Server 2025 Standard Evaluation (Desktop Experience)

---

## Hardware Configuration

RAM:

8 GB

CPU:

2 virtual processors

Disk:

60 GB

Disk Type:

VDI (VirtualBox Disk Image)

Disk Allocation:

Dynamically Allocated

---

## Boot Configuration

EFI boot mode was enabled.

Modern systems use UEFI firmware instead of legacy BIOS, and enabling EFI allows the virtual machine to simulate modern server hardware.

---

## Network Configuration

Network adapter mode:

NAT

NAT allows the virtual machine to access the internet through the host machine while remaining isolated from the host network.

This configuration is ideal for lab environments.

---

## Storage

The Windows Server installation ISO was attached to the virtual optical drive in VirtualBox.

This allowed the virtual machine to boot from the installation media.

---

## Outcome

A virtual machine named DC01 was successfully created and configured with the necessary resources to install Windows Server.

The system was ready to begin operating system installation.
