# Lab Architecture

This lab simulates a simplified small business network.

---

## Host System

The host machine runs Oracle VirtualBox which manages the virtual machines used in the lab.

---

## Virtual Machines

### DC01

Role: Domain Controller

Operating System: Windows Server 2022

Responsibilities:

- Active Directory services
- DNS server
- DHCP server
- user authentication

---

### CLIENT01

Role: Employee workstation

Operating System: Windows 10

Responsibilities:

- domain login
- application usage
- troubleshooting scenarios

---

### LINUX01

Role: Linux server

Operating System: Ubuntu Server

Responsibilities:

- SSH access practice
- Linux administration basics

---

## Network Concept

All systems communicate inside a virtual network managed by VirtualBox.

Example network layout:
Virtual Network
│
├── DC01 (Domain Controller)
│
├── CLIENT01 (Workstation)
│
└── LINUX01 (Linux Server)

---

## Key Services in the Lab

| Service          | Purpose                    |
| ---------------- | -------------------------- |
| Active Directory | centralized authentication |
| DNS              | name resolution            |
| DHCP             | automatic IP configuration |
| RDP              | Windows remote access      |
| SSH              | Linux remote access        |

---

## Safety

All machines run inside virtual machines.  
If the lab breaks, the virtual machines can be reset without affecting the host computer.
