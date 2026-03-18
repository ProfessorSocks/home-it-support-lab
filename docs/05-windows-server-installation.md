# Windows Server Installation

## Goal

Install Windows Server on the DC01 virtual machine to prepare it for domain controller deployment.

---

## Boot Process

The virtual machine was started and booted from the attached Windows Server installation ISO.

The Windows Setup environment launched successfully.

---

## Installation Settings

Language:

English

Keyboard Layout:

US

Time and Currency Format:

Default

---

## Windows Edition Selected

Windows Server 2025 Standard Evaluation (Desktop Experience)

The Desktop Experience edition was selected because it provides the graphical interface required for easier administration and learning.

Server Core was not selected because it relies entirely on command line management.

---

## Installation Type

Custom Installation

This option installs a new copy of Windows Server on the virtual disk.

The upgrade option was not used because the virtual machine did not contain a previous Windows installation.

---

## Disk Configuration

The virtual disk presented to the installer appeared as:

Drive 0 – Unallocated Space

Size:

60 GB

Windows automatically created the required system partitions.

---

## Installation Process

Windows Setup performed the following stages:

Copying Windows files  
Getting files ready for installation  
Installing features  
Installing updates  
Finishing up

The system rebooted automatically once installation completed.

---

## Administrator Account

After installation, Windows prompted for creation of the Administrator password.

This account is the default administrative account for Windows Server.

The password was configured during setup.

---

## First Login

After the reboot, the system was unlocked using:

Ctrl + Alt + Delete

Because the system was running in VirtualBox, the key combination was sent using:

Right Ctrl + Delete

The Administrator account was used to log in.

---

## Initial Server Environment

Upon login, the Server Manager dashboard automatically launched.

Server Manager provides centralized access to:

- server roles
- features
- system configuration
- administrative tools

This interface is commonly used for Windows Server administration.

---

## Outcome

Windows Server was successfully installed and the DC01 virtual machine became operational.

The server was ready for role installation and domain controller promotion.
