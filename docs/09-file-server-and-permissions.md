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

---

## Security Group Configuration

The following Active Directory security groups were created:

- HR_Users
- IT_Users

Test user accounts were added to the appropriate groups to simulate departmental access control.

This follows standard enterprise practice where permissions are assigned to groups rather than directly to individual users.

---

## Folder Creation

The following folders were created on DC01:

- C:\CompanyFiles\Public
- C:\CompanyFiles\HR
- C:\CompanyFiles\IT

These folders were used to simulate a company file share with department-based access controls.

---

## Share Configuration

The parent folder was shared as:

`\\DC01\CompanyFiles`

Share permissions were kept broad enough to allow authenticated access, while detailed access restrictions were enforced through NTFS permissions on the subfolders.

---

## NTFS Permission Design

Permissions were configured as follows:

### Public

- Authenticated Users: Read

### HR

- HR_Users: Modify
- Administrators: Full Control
- SYSTEM: Full Control

### IT

- IT_Users: Modify
- Administrators: Full Control
- SYSTEM: Full Control

Restricted folders were configured to prevent unauthorized department access.

---

## Troubleshooting and Permission Correction

During testing, a user in the HR group was initially able to access the IT folder unexpectedly.

### Root Cause

The restricted folders inherited broad NTFS permissions from the parent `CompanyFiles` directory.

### Fix

Inheritance was disabled on the restricted subfolders, inherited permissions were converted into explicit permissions, and broad access entries were removed. Only the intended department group, Administrators, and SYSTEM were retained.

### Lesson Learned

NTFS inheritance can unintentionally make restricted folders more accessible than intended. Department folders should be reviewed carefully to verify effective access.

---

## Access Testing

Access was tested from CLIENT01 using domain user accounts.

Expected results:

### HR user

- Public: Accessible
- HR: Accessible
- IT: Access denied

### IT user

- Public: Accessible
- HR: Access denied
- IT: Accessible

The final configuration matched the intended access model.

---

## Concepts Learned

This phase provided hands-on practice with:

- Windows file sharing
- Share permissions
- NTFS permissions
- Security groups
- Group-based access control
- Access troubleshooting
- Permission inheritance

---

## Outcome

The lab environment now supports shared network storage with department-based permissions.

Current lab components:

- DC01 — Domain Controller, DNS server, file server
- CLIENT01 — Domain workstation

This phase simulated a common enterprise file server scenario and reinforced how access control is managed in Windows environments.

---

## Access Testing Note

Shared folder access was also tested using the UNC path format:

`\\DC01\CompanyFiles`

This reinforced the importance of correct share naming and demonstrated that shared drive issues may be caused by simple path errors rather than network or permission failures.
