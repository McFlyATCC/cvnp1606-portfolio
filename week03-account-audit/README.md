# CVNP1606 - Week 04
## Ticket: CVNP1606-W03-003

### Student
Matthew McCullough

### Ticket Information

| Field | Value |
|---------|---------|
| Ticket ID | CVNP1606-W03-003 |
| Submitted By | Jordan Lee, Nexus Support Services Lead Technician |
| Affected System | ACME-W11-BASELINE / ACME Kiosk Machine |
| Priority | High |
| Topic | Local User Administration and Least-Privilege Access Control |

---

# Scenario Summary

ACME required new accounts for seasonal staff and kiosk usage. Additionally, the existing local Administrators group had not been audited, creating a potential security risk. The objective was to create appropriate local user accounts, assign permissions according to least-privilege principles, verify User Account Control (UAC) behavior, audit group membership, and document the rationale behind access decisions.

The work focused on ensuring users received only the permissions necessary to perform their assigned job duties while reducing unnecessary administrative access.

---

# Objectives

- Create local seasonal staff accounts.
- Create local kiosk account(s).
- Verify standard user permissions.
- Audit local group membership.
- Export audit results using PowerShell.
- Validate UAC behavior.
- Document least-privilege decisions.
- Produce audit evidence for review.

---

# Tools Used

## Windows Administrative Tools

- Settings App
- Local Users and Groups (`lusrmgr.msc`)
- User Account Control (UAC)
- Computer Management

## PowerShell

Commands used included:

```powershell
Get-LocalUser
```

```powershell
Get-LocalGroupMember -Group "Administrators"
```

```powershell
New-LocalUser
```

```powershell
Add-LocalGroupMember
```

## Documentation Tools

- Visual Studio Code
- Git
- GitHub
- Markdown

---

# Steps Taken

## 1. Audited Existing Accounts

Reviewed all local users and groups to establish a baseline of current system access.

```powershell
Get-LocalUser
```

```powershell
Get-LocalGroupMember -Group "Administrators"
```

---

## 2. Created Seasonal Staff Account

Created a local user account for seasonal employees.

Example:

```powershell
New-LocalUser
```

Verified the account was created successfully and assigned only standard user permissions.

---

## 3. Created Kiosk Account

Created a dedicated kiosk account for shared workstation usage.

The account was configured as a standard local user to prevent unauthorized changes to the operating system.

---

## 4. Reviewed Group Membership

Confirmed newly created accounts were members of the local Users group and not members of the Administrators group.

Verified least-privilege controls were maintained.

---

## 5. Tested UAC Functionality

Attempted administrative functions while logged in as a standard user.

Observed UAC prompts requiring administrative credentials before elevated actions could be performed.

---

## 6. Exported Audit Results

Executed a PowerShell audit and exported findings to:

```text
local-users-export.txt
```

The report included:

- Local users
- Administrators group membership
- Compliance verification notes

---

# Security Findings

### Seasonal Staff Account

| Control | Status |
|----------|----------|
| Standard User | ✅ |
| Local Administrator | ❌ |
| Least Privilege Applied | ✅ |

### Kiosk Account

| Control | Status |
|----------|----------|
| Standard User | ✅ |
| Local Administrator | ❌ |
| Least Privilege Applied | ✅ |

### Administrators Group

- Reviewed membership.
- Verified approved administrative accounts.
- Confirmed seasonal and kiosk accounts were not granted elevated privileges.

---

# Access Control Rationale

Administrative privileges should be granted only when a user has a documented business need to perform system-level tasks such as software installation, service management, or operating system troubleshooting.

Seasonal staff and kiosk users do not require administrative permissions to perform routine business operations. Assigning standard user access reduces organizational risk while still allowing users to complete assigned work.

Any request for elevated privileges should be reviewed and escalated through established IT and security approval processes before administrative rights are granted.

---

# Evidence List

The following evidence was collected during ticket resolution:

- Screenshot of created seasonal account
- Screenshot of created kiosk account
- Screenshot of Users group membership
- Screenshot of Administrators group membership
- PowerShell command output
- Exported audit report (`local-users-export.txt`)
- UAC validation results
- Least-Privilege Access Memo

---

# Ticket Resolution Summary

The seasonal staff and kiosk accounts were successfully created and verified as standard users. Local administrative group membership was audited and documented. UAC testing confirmed elevation controls were functioning properly. Audit results were exported and retained as evidence. The final configuration aligns with least-privilege security principles and supports ACME operational requirements.

---

# AI Disclosure

Generative AI (Microsoft Copilot) was used as a learning aid to:

- Explain Windows account management concepts.
- Assist with PowerShell scripting.
- Review troubleshooting steps.
- Improve technical writing quality.
- Format documentation and reports.

All commands were executed, validated, and documented by the student. Final review and verification of results were performed manually.

---

# Portfolio Card

## Local User Administration and Least-Privilege Access Control

**Environment:** Windows 11

**Skills Demonstrated:**

- Windows user administration
- Local group management
- PowerShell auditing
- User Account Control validation
- Least-privilege implementation
- Security documentation
- Technical reporting

**Artifacts Produced:**

- Local user audit report
- PowerShell export file
- Ticket documentation
- Access control memo
- GitHub README

**Outcome:**

Successfully implemented and verified secure local account administration practices using least-privilege principles while producing audit-ready documentation and supporting evidence.
