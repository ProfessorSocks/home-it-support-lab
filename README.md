# Home IT Support Lab

This project documents the creation of a **virtualized home IT support lab** built using VirtualBox.  
The goal of the lab is to simulate a small company network environment in order to practice real-world IT support tasks such as system administration, network troubleshooting, Active Directory management, and remote system access.

This repository documents the full process of planning, building, troubleshooting, and learning from the lab environment.

---

## Project Goals

The purpose of this project is to gain practical experience with the skills commonly required for entry-level IT support roles.

Skills practiced in this lab include:

- Windows administration
- Help desk troubleshooting
- Root cause analysis
- TCP/IP networking
- DNS and DHCP configuration
- Subnetting fundamentals
- VPN concepts
- Active Directory administration
- Remote Desktop
- SSH remote access
- Virtual machine management
- Technical documentation

---

## Lab Environment

The lab simulates a small company network using virtual machines.

Planned machines:

| Machine  | Role                             |
| -------- | -------------------------------- |
| DC01     | Windows Server domain controller |
| CLIENT01 | Windows client workstation       |
| LINUX01  | Ubuntu server for SSH practice   |

These systems run inside **Oracle VirtualBox** on the host computer.

---

## Tools Used

- Oracle VirtualBox
- Windows Server 2022 Evaluation
- Windows 10
- Ubuntu Server LTS
- GitHub for documentation and version control

---

## Repository Structure

home-it-support-lab/
├── README.md
├── docs/
├── diagrams/
├── screenshots/
├── tickets/
└── notes/

### docs/

Contains the main documentation for the project.

- Project overview
- Learning plan
- Lab architecture
- Setup guides
- Networking notes
- Troubleshooting scenarios
- Lessons learned

### diagrams/

Network diagrams and system architecture diagrams.

### screenshots/

Screenshots documenting the setup process and troubleshooting steps.

### tickets/

Simulated help desk tickets documenting issues, investigations, root causes, and resolutions.

### notes/

Reference material such as command lists and technical terminology.

---

## Why This Project Exists

This project is designed to demonstrate practical technical ability and documentation skills.  
Instead of only listing technologies on a resume, the lab provides evidence of:

- hands-on experimentation
- systematic troubleshooting
- clear technical documentation
- real problem-solving workflows

---

## Expected Outcomes

By completing this lab I expect to be able to:

- build and manage virtual machines
- configure Windows Server and Active Directory
- troubleshoot networking problems
- manage user accounts and domain logins
- remotely access systems using RDP and SSH
- document technical problems and solutions clearly

---

## Current Status

Planning and documentation phase.

Next step: build the first virtual machine and install Windows Server.
