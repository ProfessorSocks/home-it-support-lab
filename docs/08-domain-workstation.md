# Domain Workstation Deployment

## Goal

The purpose of this phase was to deploy a client workstation and join it to the Active Directory domain.

This simulates a real company workstation connecting to the corporate network and authenticating through the domain controller.

---

## Workstation Creation

A new virtual machine was created in VirtualBox to simulate a company employee computer.

Virtual Machine Name:

```
CLIENT01
```

Operating System:

```
Windows 10
```

---

## Virtual Machine Configuration

Allocated Resources:

RAM:

```
4 GB
```

CPU:

```
2 virtual processors
```

Disk:

```
50 GB
```

Disk Type:

```
VDI (VirtualBox Disk Image)
```

Disk Allocation:

```
Dynamically Allocated
```

Network Adapter:

```
NAT
```

---

## Operating System Installation

The Windows installation ISO was attached to the virtual optical drive.

The workstation booted successfully from the installation media.

Windows installation steps included:

- selecting language and keyboard layout
- choosing Windows edition
- selecting custom installation
- installing the operating system on the virtual disk

After installation, the system rebooted automatically.

---

## Workstation Naming

After installation, the workstation was renamed:

```
CLIENT01
```

This follows typical enterprise workstation naming conventions.

Example naming patterns:

```
CLIENT01
CLIENT02
LAPTOP01
```

---

## Domain Join Process

The workstation was joined to the domain using the System Properties interface.

Navigation:

```
Settings → System → About → Rename this PC (Advanced)
```

The workstation was joined to the following domain:

```
corp.local
```

Domain administrator credentials were required to complete the domain join.

After successful authentication, Windows confirmed the workstation had joined the domain.

The system was then restarted.

---

## Domain Authentication Test

After reboot, the login screen displayed the domain login option.

A domain user account was used to log in.

Example login format:

```
CORP\alice
```

or

```
alice@corp.local
```

The domain controller successfully authenticated the login request.

---

## Active Directory Verification

After the workstation joined the domain, the computer object appeared in Active Directory.

Location:

```
Active Directory Users and Computers
→ Computers
→ CLIENT01
```

This confirmed the domain controller recognized the workstation as part of the domain.

---

## Concepts Learned

This phase demonstrated several key enterprise IT concepts:

- Domain join process
- Domain authentication
- Computer objects in Active Directory
- Relationship between workstations and domain controllers

In a corporate network, most employee computers are joined to a domain to allow centralized authentication and management.

---

## Outcome

The lab environment now contains:

```
DC01 (Domain Controller)
CLIENT01 (Domain Workstation)
```

The workstation is able to authenticate users through the domain controller, demonstrating a functioning Active Directory environment.

Future phases will expand the environment with additional services and security policies.

---

## Networking Configuration

Before joining the domain, the workstation DNS was manually configured.

The DNS server was set to the domain controller:

```
DC01 IP Address
```

This step is critical because Active Directory relies on DNS to locate domain controllers.

---

## Domain Join Verification

After joining the domain and restarting the workstation:

- The login screen displayed the domain login option
- Domain credentials were accepted
- Authentication was handled by DC01

---

## Active Directory Confirmation

The workstation appeared in Active Directory:

```
Active Directory Users and Computers
→ Computers
→ CLIENT01
```

This confirms the domain controller successfully registered the workstation.

---

## Key Concepts Learned

- DNS is required for domain communication
- Workstations must point to the domain controller for name resolution
- Domain join requires authentication from a domain administrator
- Active Directory creates computer objects for joined machines
- Domain authentication allows centralized login management

---

## Outcome

The lab environment now simulates a basic enterprise network:

```
DC01 (Domain Controller)
CLIENT01 (Domain Workstation)
```

Users can log into CLIENT01 using domain credentials, and authentication is handled by DC01.

This demonstrates a functioning Active Directory environment.
