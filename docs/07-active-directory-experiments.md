# Active Directory Experiments

## Goal

After successfully deploying the first Domain Controller (DC01) for the `corp.local` domain, several exploratory experiments were performed to better understand how Active Directory functions in a real enterprise environment.

These experiments focused on the core components of Active Directory including:

- Organizational Units
- Security Groups
- Group Policy
- DNS
- PowerShell administration

The goal was to simulate common administrative tasks performed by system administrators and help desk engineers.

---

# Experiment 1 — Organizational Units (OU Structure)

## Purpose

Organizational Units are used to logically organize objects within Active Directory.
They allow administrators to apply policies, delegate permissions, and structure the directory similar to a company's organizational structure.

## Actions Performed

The following Organizational Units were created under the domain:

```
corp.local
│
├── Employees
├── IT
├── Servers
└── Workstations
```

Test user accounts were moved into the **Employees** OU to simulate employee account organization.

## Concepts Learned

- OUs provide structure to Active Directory environments.
- Group Policy is typically applied at the OU level.
- Large organizations may have dozens or hundreds of OUs.

---

# Experiment 2 — Security Groups

## Purpose

Security groups are used to manage permissions efficiently.
Instead of assigning permissions directly to users, organizations assign permissions to groups and add users to those groups.

## Actions Performed

A new security group was created:

```
Group Name: IT_Admins
Group Scope: Global
Group Type: Security
```

Test user accounts were added as members of the group.

## Concepts Learned

Typical enterprise permission model:

```
Users → Security Groups → Resource Permissions
```

Example:

```
Alice → IT_Admins → Server Access
```

This simplifies large-scale permission management.

---

# Experiment 3 — Group Policy

## Purpose

Group Policy allows administrators to centrally control security policies and configuration settings across domain computers.

## Actions Performed

Group Policy Management was opened through:

```
Server Manager → Tools → Group Policy Management
```

A new Group Policy Object was created:

```
Password Policy Test
```

Policy location:

```
Computer Configuration
Policies
Windows Settings
Security Settings
Account Policies
Password Policy
```

## Concepts Learned

Group Policy can control:

- password requirements
- security restrictions
- desktop settings
- device policies
- software installation

Large organizations use Group Policy to manage thousands of computers.

---

# Experiment 4 — DNS Exploration

## Purpose

Active Directory relies heavily on DNS to locate services and domain controllers.

## Actions Performed

DNS Manager was opened:

```
Server Manager → Tools → DNS
```

The following zone was verified:

```
Forward Lookup Zones
└── corp.local
```

A new host record was created:

```
Hostname: fileserver
IP Address: 192.168.1.100
```

## Concepts Learned

Domain computers use DNS to locate domain controllers during authentication.

Without DNS, domain login would fail.

---

# Experiment 5 — Active Directory PowerShell Queries

## Purpose

PowerShell is commonly used by administrators to automate Active Directory management tasks.

## Actions Performed

PowerShell commands were executed to query the directory.

List all users:

```
Get-ADUser -Filter *
```

List all computers:

```
Get-ADComputer -Filter *
```

## Concepts Learned

PowerShell allows administrators to automate management of large environments.

Large enterprise environments often contain:

- tens of thousands of users
- thousands of computers
- multiple domain controllers

Automation is critical for managing environments at this scale.

---

# Experiment Outcome

These experiments provided hands-on experience with the core components of Active Directory:

- directory structure
- identity management
- DNS integration
- policy management
- administrative automation

The domain controller **DC01.corp.local** is now functioning as the identity and directory service for the lab environment.

These experiments helped reinforce the relationship between:

- Active Directory
- DNS
- Group Policy
- User authentication

Future lab phases will introduce domain workstations and additional services into the domain.
