# Help Desk Scenarios

## Goal

The goal of this phase is to simulate realistic help desk and junior IT support tasks inside the lab environment.

These scenarios use the existing Active Directory domain, workstation, file shares, and user accounts to practice troubleshooting, account support, permissions investigation, and root cause analysis.

---

## Environment

Lab systems involved:

- DC01 — Domain Controller, DNS server, file server
- CLIENT01 — Domain workstation

Core services involved:

- Active Directory
- DNS
- Shared folders
- NTFS permissions
- Domain authentication

---

## Purpose

This phase focuses on practicing the kinds of issues commonly handled by entry-level IT support technicians.

Examples include:

- user login failures
- password resets
- account lockouts
- permission issues
- network access problems
- DNS-related failures

---

## Skills Practiced

- Help desk troubleshooting
- Root cause analysis
- User support
- Account management
- Permission troubleshooting
- DNS troubleshooting
- Documentation of incident resolution

---

## Ticket Format

Each scenario should be documented using the following structure:

- Ticket ID
- Issue Title
- Reported Symptom
- Environment
- Initial Hypothesis
- Investigation
- Root Cause
- Resolution
- Prevention / Lesson Learned

---

## Outcome

At the end of this phase, the lab should include multiple realistic support scenarios showing the ability to troubleshoot and resolve common IT issues in a structured way.

---

---

## Ticket 001 — User Cannot Log In and Cannot Access Department Folder

### Reported Symptom

A domain user could not log in successfully due to an incorrect password. After the password was reset and the user signed in, the user was still unable to access the expected department folder.

### Environment

- Domain: corp.local
- Domain Controller: DC01
- Workstation: CLIENT01
- File Share: \\DC01\CompanyFiles
- User account: test domain user

### Initial Hypothesis

Possible causes included:

- incorrect password
- account lockout
- missing group membership
- NTFS permission issue
- stale user logon session not reflecting recent group changes

### Investigation

The login issue was reproduced on CLIENT01 by attempting to sign in with an incorrect password.

The password was reset in Active Directory Users and Computers on DC01, and the user was able to sign in successfully afterward.

A second issue appeared when the user attempted to access the IT folder. The folder could not be opened even though the permissions appeared correct.

The user account was reviewed in Active Directory and it was discovered that the account had only recently been added to the `IT_Users` security group after the user was already signed in.

### Root Cause

The password issue was caused by incorrect credentials.

The folder access issue was caused by the user's current logon session not yet containing the updated security group membership. The security token had been created before the user was added to the `IT_Users` group.

### Resolution

The password was reset in Active Directory.

The user was added to the correct security group.

The user then signed out and signed back in to refresh the security token. After reauthentication, access to the IT folder worked correctly.

### Prevention / Lesson Learned

Password failures should be separated from permission failures during troubleshooting.

When a user is added to a new Active Directory security group, the current logon session may not immediately reflect the new permissions. Signing out and signing back in is often required for the updated group membership to take effect.

---

## Ticket 002 — Account Lockout Simulation Attempt

### Reported Symptom

A lockout scenario was tested by attempting repeated incorrect sign-ins on CLIENT01 using a domain user account.

### Environment

- Domain: corp.local
- Domain Controller: DC01
- Workstation: CLIENT01

### Investigation

Multiple failed sign-in attempts were performed to trigger an account lockout.

However, the account did not become locked, and no locked status appeared in Active Directory Users and Computers.

### Root Cause

The domain did not yet have an account lockout policy configured through Group Policy.

As a result, repeated failed authentication attempts were rejected, but no lockout threshold was enforced.

### Resolution

No immediate remediation was required. The scenario identified a missing security policy rather than a user-specific issue.

### Prevention / Lesson Learned

Account lockout behavior depends on domain password and lockout policies. These settings must be configured in Group Policy before lockout scenarios can be tested realistically.

---

## Ticket 002 — Account Locked Out After Repeated Failed Sign-In Attempts

### Reported Symptom

A domain user was unable to sign in to CLIENT01 after multiple failed password attempts.

### Environment

- Domain: corp.local
- Domain Controller: DC01
- Workstation: CLIENT01
- User account: alice

### Initial Hypothesis

Possible causes included:

- incorrect password
- account lockout due to repeated failed attempts
- keyboard layout issue
- domain connectivity issue

### Investigation

A domain account lockout policy had been configured in Group Policy with a threshold of 3 invalid logon attempts.

On CLIENT01, repeated sign-in attempts were made with an incorrect password until the lockout threshold was reached.

The account was then reviewed in Active Directory Users and Computers on DC01 and was found to be locked.

### Root Cause

The account was locked after repeated failed sign-in attempts triggered the domain account lockout policy.

### Resolution

The account was unlocked in Active Directory on DC01.

After unlocking the account, the user successfully signed in on CLIENT01 using the correct password.

### Prevention / Lesson Learned

Repeated failed sign-in attempts can trigger domain lockout policies. When a user cannot sign in after multiple failed tries, administrators should check both credential accuracy and account lockout status in Active Directory.

---

## Ticket 003 — User Cannot Access Department Folder

### Reported Symptom

A user reported that they could access the shared drive but could not open their department folder.

### Environment

- Domain: corp.local
- Domain Controller: DC01
- Workstation: CLIENT01
- File Share: \\DC01\CompanyFiles
- User account: HR user

### Initial Hypothesis

Possible causes included:

- missing permissions
- incorrect group membership
- NTFS permission issue
- share permission issue

### Investigation

The issue was reproduced on CLIENT01. The user was able to access the shared drive and the Public folder but received an "Access Denied" error when opening the HR folder.

The user's group membership was verified in Active Directory and confirmed to be part of `HR_Users`.

The NTFS permissions on the HR folder were reviewed on DC01. It was discovered that the `HR_Users` group was missing from the folder permissions.

### Root Cause

The HR folder did not have the `HR_Users` group assigned in NTFS permissions.

### Resolution

The `HR_Users` group was added back to the HR folder with Modify permissions.

After applying the change, the user successfully accessed the folder.

### Prevention / Lesson Learned

Access issues should be narrowed down by testing different folders. If only one folder fails, it is often a permissions issue specific to that folder.

NTFS permissions should always be verified when users report access problems to shared resources.

---

## Ticket 004 — Workstation Could Not Contact Domain Resources Due to Incorrect DNS Configuration

### Reported Symptom

A workstation was unable to properly resolve domain resources. Domain-related services such as shared folder access and domain name resolution were not functioning correctly.

### Environment

- Domain: corp.local
- Domain Controller: DC01
- Workstation: CLIENT01

### Initial Hypothesis

Possible causes included:

- DNS misconfiguration
- domain controller offline
- general network connectivity issue
- file share issue
- name resolution failure

### Investigation

The issue was reproduced on CLIENT01 by testing domain-related name resolution and access.

The following commands were used:

- `nslookup corp.local`
- `ping DC01`
- `ipconfig /all`

The workstation’s DNS server setting was reviewed and found to be pointing to a public DNS server instead of the domain controller.

### Root Cause

The workstation was configured to use an incorrect DNS server. Because Active Directory depends on the domain controller’s DNS service to resolve internal domain names, domain resources could not be located correctly.

### Resolution

The DNS server on CLIENT01 was changed back to the IP address of DC01.

After correcting the DNS configuration, domain name resolution and access to shared resources functioned normally again.

### Prevention / Lesson Learned

Domain workstations should use the domain controller as their DNS server in a lab environment like this one. Public DNS servers cannot resolve private Active Directory zones such as `corp.local`.

---

## Ticket 005 — Shared Drive Path Would Not Open from CLIENT01

### Reported Symptom

A user reported that the company shared drive would not open from CLIENT01.

### Environment

- Domain: corp.local
- Domain Controller / File Server: DC01
- Workstation: CLIENT01
- Shared path: `\\DC01\CompanyFiles`

### Initial Hypothesis

Possible causes included:

- incorrect UNC path
- DNS / name resolution issue
- server unreachable
- share unavailable
- folder permissions issue

### Investigation

The shared path was tested from CLIENT01.

An incorrect UNC path was entered first, which failed:

`\\DC01\CompanyFilez`

The correct path was then tested:

`\\DC01\CompanyFiles`

Additional name-resolution testing was performed using:

- `ping DC01`
- `nslookup DC01`
- `nslookup corp.local`

The workstation was also able to access the share successfully when the correct path was used.

### Root Cause

The issue was caused by an incorrect UNC path / share name.

The file server and network connectivity were functioning normally.

### Resolution

The correct shared path was provided and verified:

`\\DC01\CompanyFiles`

After using the correct path, the user was able to access the share successfully.

### Prevention / Lesson Learned

When troubleshooting shared drive issues, it is important to verify the exact UNC path first before assuming a network or permissions problem.

Testing by hostname, by IP, and by subfolder helps isolate whether the issue is related to naming, connectivity, or access control.
