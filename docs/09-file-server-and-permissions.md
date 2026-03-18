# File Server and Permissions

## Goal

The goal of this phase is to configure shared folders on the domain controller and control access using Active Directory users and security groups.

This simulates a basic company file server environment where different departments have access to different folders.

---

## Planned Shared Structure

The following shared folders will be created on DC01:

- Public
- HR
- IT

These folders will be shared to domain users through the network.

Example UNC path:

`\\DC01\CompanyFiles`

---

## Access Model

Access will be controlled using security groups.

Planned design:

- HR users → access HR
- IT users → access IT
- All users → access Public

This follows common enterprise permission practices where permissions are assigned to groups instead of directly to users.

---

## Concepts Practiced

- File sharing
- NTFS permissions
- Share permissions
- Security groups
- Domain-based access control
- Access testing from a workstation

---

## Outcome

At the end of this phase, the lab environment should support shared network folders that can be accessed from CLIENT01 based on domain permissions.
