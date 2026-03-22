# Group Policy

## Goal

The goal of this phase is to configure Group Policy settings in the domain environment and observe how centralized policy affects users and computers.

This phase focuses on common security and administration settings that are widely used in enterprise Windows environments.

---

## Environment

- Domain: corp.local
- Domain Controller: DC01
- Client Workstation: CLIENT01

---

## Purpose

Group Policy allows administrators to centrally configure security settings and operating system behavior for domain users and computers.

This phase will be used to configure:

- password policy
- account lockout policy
- additional workstation controls in later tests

---

## Skills Practiced

- Group Policy Management
- Security policy configuration
- Domain-wide policy deployment
- Policy testing and troubleshooting

---

## Outcome

At the end of this phase, the lab should enforce centralized policy settings that can be tested from domain workstations and user accounts.

---

## Account Lockout Policy Configuration

The Default Domain Policy was edited in Group Policy Management to configure account lockout behavior.

Policy path:

`Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Account Lockout Policy`

The following settings were applied:

- Account lockout threshold: 3 invalid logon attempts
- Account lockout duration: 15 minutes
- Reset account lockout counter after: 15 minutes

### Purpose

These settings were configured to simulate realistic help desk account lockout scenarios and to demonstrate centralized security policy enforcement through Active Directory.

### Result

After policy application, repeated failed sign-in attempts on CLIENT01 triggered an account lockout. The locked account was then managed from DC01 through Active Directory.

---

## Drive Mapping with Group Policy

A Group Policy Object named **Map Company Drive** was created and linked to the domain.

### Configuration Path

User Configuration → Preferences → Windows Settings → Drive Maps

### Settings Applied

- Action: Create
- Location: \\DC01\CompanyFiles
- Drive Letter: H:
- Label: Company Files
- Reconnect: Enabled

### Purpose

This configuration automatically maps a shared network drive for domain users when they log in to a workstation.

### Result

After applying Group Policy and logging into CLIENT01, the mapped drive appeared under "This PC" as:

H: (Company Files)

This demonstrated centralized management of user environments through Group Policy.

### Concepts Learned

- Group Policy Preferences
- User-based policy application
- Centralized drive mapping
- Login-time configuration deployment
