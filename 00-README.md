# Microsoft 365 Enterprise Administration Lab

## Overview

This project documents the design, deployment, administration, security configuration, and management of a Microsoft 365 enterprise lab environment built to simulate a real-world corporate IT environment.

The objective was to develop practical experience in Microsoft 365 administration, Microsoft Entra ID, Exchange Online, SharePoint Online, Microsoft Teams, Identity Management, Security Administration and Helpdesk Operations.

The environment follows enterprise administration principles including:

- Role-Based Access Control (RBAC)
- Least Privilege Access
- Identity & Access Management
- Microsoft 365 Security Best Practices
- User Lifecycle Management
- Departmental Resource Separation
- Audit & Compliance Monitoring

---

# Lab Architecture

```text
                     ┌─────────────────────┐
                     │ Microsoft 365 Tenant│
                     └──────────┬──────────┘
                                │
                                ▼
                      ┌───────────────────┐
                      │ Microsoft Entra ID│
                      └─────────┬─────────┘
                                │
      ┌─────────────────────────┼─────────────────────────┐
      │                         │                         │
      ▼                         ▼                         ▼
 Exchange Online         Microsoft Teams          SharePoint Online
      │                         │                         │
      ▼                         ▼                         ▼
 Shared Mailboxes      Teams & Channels        Department Sites
 Distribution Lists    Team Membership         Document Libraries
 Mail Enabled Groups   Permissions             File Management
```

---

# Environment Overview

## Company

```text
Solotech Innovations
```

Departments:

- Customer Service Group (CSG)
- Information Technology (IT)
- Human Resources (HR)
- Finance (FIN)
- Sales (S.O)

---

# Users

## Standard Users

Created:

```text
20 Cloud Users
```

Configured:

- User Accounts
- Department Assignment
- Job Titles
- Licenses
- Microsoft 365 Service Access

Services Verified:

- Outlook Online
- Exchange Online
- SharePoint Online
- OneDrive for Business
- Microsoft Teams
- Microsoft Copilot

---

# Microsoft Entra ID Administration

## User Management

Implemented:

- User Creation
- User Modification
- User Disablement
- User Lifecycle Management

---

## Group Management

### Security Groups

```text
HR-Team
IT-Team
Finance-Team
Finance-Payroll-Team
Finance-Projects-Team
Sales-Team
CSG-Team
```

---

## Mail Enabled Security Groups

Created:

```text
HR-Mailbox
IT-Mailbox
Finance-Mailbox
Sales-Mailbox
CSG-Mailbox
```

Used for:

- Exchange Administration
- Shared Mailbox Access
- Resource Separation

---

# Exchange Online Administration

## Shared Mailboxes

Created:

```text
- hr@solotechinnovations.onmicrosoft.com
- finance@solotechinnovations.onmicrosoft.com
- sales@solotechinnovations.onmicrosoft.com
- csg@solotechinnovations.onmicrosoft.com
- it-support@solotechinnovations.onmicrosoft.com
```

Configured:

- Full Access
- Send As
- Delegated Permissions

### Tested

✅ Shared Mailbox Access

✅ Outlook Web Access

✅ Delegation

✅ Mailbox Discovery

✅ Access Removal

---

## Distribution Lists

Created:

```text
HR-All
IT-All
Finance-All
Sales-All
CSG-All
```

Validated:

- Internal delivery
- Group membership
- Department communications

---

# Administrative Structure

Implemented dedicated administrator accounts.

## Global Administrator

```text
admin@solotechinnovations.onmicrosoft.com
```

Responsibilities:

- Tenant Management
- Identity Administration
- Licensing
- Security Administration

---

## Exchange Administrator

```text
exchange.admin@solotechinnovations.onmicrosoft.com
```

Responsibilities:

- Mailboxes
- Distribution Groups
- Mail Flow
- Exchange Online

---

## SharePoint Administrator

```text
sharepoint.admin@solotechinnovations.onmicrosoft.com
```

Responsibilities:

- Sites
- Libraries
- Permissions
- OneDrive Administration

---

## Teams Administrator

```text
teams.admin@solotechinnovations.onmicrosoft.com
```

Responsibilities:

- Teams
- Channels
- Teams Policies

---

## Helpdesk Administrator

```text
helpdesk.admin@solotechinnovations.onmicrosoft.com
```

Responsibilities:

- Password Resets
- User Support
- Account Administration

---

# RBAC Validation

Administrative permissions were tested using separate administrator accounts.

Validated:

✅ Helpdesk Admin cannot access Teams Admin Centre

✅ Helpdesk Admin cannot access SharePoint Administration

✅ Helpdesk Admin cannot access Security Diagnostics

✅ Least Privilege Model enforced

Example:

```text
Helpdesk Admin
    │
    ├─ Reset Passwords
    ├─ Manage Users
    │
    └─ Cannot:
         • Administer Teams
         • Administer SharePoint
         • View Security Reports
```

---

# Multi-Factor Authentication

Implemented MFA across privileged accounts.

Protected Accounts:

- Global Administrator
- Exchange Administrator
- SharePoint Administrator
- Teams Administrator
- Helpdesk Administrator

Authentication Methods:

- Microsoft Authenticator

---

# Microsoft Teams Administration

Created Department Teams

```text
HR TEAM
IT TEAM
FINANCE TEAM
SALES TEAM
CSG TEAM
```

---

## Finance Team Structure

### Standard Channels

```text
General
Projects
Budgets
```

### Private Channel

```text
Payroll
```

### Shared Channel

```text
Finance Collaboration
```

---

# Teams Architecture

```text
FINANCE TEAM
│
├── General
├── Projects
├── Budgets
│
├── Payroll (Private)
│
└── Collaboration (Shared)
```

---

# SharePoint Administration

Each Team generated associated SharePoint Sites.

Created Libraries:

```text
Budgets
Projects
Invoices
Payroll
```

---

# SharePoint Permission Model

```text
Finance Team Site
│
├── Budgets
├── Projects
├── Invoices
│
└── Payroll
     │
     └── Finance-Payroll-Team Only
```

Implemented:

✅ Unique Permissions

✅ Group-Based Access

✅ Department Separation

✅ Access Validation

---

# SharePoint Testing

Validated:

Finance User:

✅ Budgets

✅ Projects

✅ Invoices

❌ Payroll

---

Finance Payroll User:

✅ Payroll Access

✅ Full Library Access

---

Non-Finance Users:

❌ Finance Site Access

---

# Microsoft Entra Security

## Conditional Access

Implemented:

### CA001

```text
Require MFA for Administrators
```

Status:

```text
Report Only
```

---

### CA002

```text
Block Legacy Authentication
```

Status:

```text
Report Only
```

---

# Identity Protection

Enabled through:

```text
Microsoft Entra ID P2
```

Investigated:

- Risky Users
- Risky Sign-ins
- Risk Detection Events

Example Detection:

```text
Anomalous Token
Medium Risk
```

Investigation Flow:

```text
Risk Detection
      ↓
Risky User
      ↓
Sign-In Logs
      ↓
Validation
      ↓
Risk Resolution
```

---

# Sign-In Log Analysis

Investigated:

```text
Success
Failure
Interrupted
```

Authentication Events:

```text
50055
50126
50140
```

Used logs to:

- Validate MFA
- Troubleshoot Sign-ins
- Investigate User Activity
- Review Authentication Flows

---

# User Lifecycle Management

## Onboarding

Implemented:

```text
Create User
↓
Assign License
↓
Add Groups
↓
Add Shared Mailbox Access
↓
Add Teams Access
↓
Validate SharePoint Permissions
```

---

## Auditor Access Scenario

Created:

```text
Paul Murphy (FIN)
```

Business Need:

```text
Temporary Finance Auditor
```

Granted:

✅ Finance Team Access

✅ Finance Payroll Access

✅ Shared Mailbox Access

✅ Distribution Lists

✅ SharePoint Access

✅ Team Membership

---

## Auditor Offboarding

Validated:

### Phase 1

Removed:

- Team Memberships
- Security Groups
- Payroll Access

Result:

✅ Immediate SharePoint permission removal

---

### Phase 2

Removed M365 License

Result:

✅ Outlook disabled

✅ SharePoint disabled

✅ Teams lost resources

✅ OneDrive entered grace period

---

### Phase 3

Blocked Sign-In

Result:

✅ Authentication prevented

---

### Phase 4

Reviewed:

- Audit Logs
- Sign-In Logs
- Administrative Changes

---

# Troubleshooting Experience

## Shared Mailboxes

Issue:

```text
Mailbox not visible to users
```

Resolution:

- Investigated delegation
- Validated permissions
- Tested Outlook Web
- Verified Entra ID object

---

## Teams Access

Issue:

```text
Users unable to view Teams resources
```

Resolution:

- Validated team membership
- Reviewed Microsoft 365 Group membership
- Tested permissions

---

## SharePoint Permissions

Issue:

```text
Payroll documents accessible to non-payroll users
```

Resolution:

- Broke inheritance
- Configured unique permissions
- Assigned Payroll Security Group
- Validated access

---

## Identity Protection

Issue:

```text
Risky User flagged
```

Detection:

```text
Anomalous Token
```

Resolution:

- Reviewed sign-in logs
- Investigated activity
- Validated user actions

---

# Skills Demonstrated

## Microsoft Entra ID

- User Management
- Security Groups
- Mail Enabled Groups
- Conditional Access
- Identity Protection
- MFA
- RBAC

---

## Exchange Online

- Shared Mailboxes
- Distribution Lists
- Delegated Permissions
- Mail Enabled Security Groups

---

## Microsoft Teams

- Team Administration
- Private Channels
- Shared Channels
- Membership Management

---

## SharePoint Online

- Site Administration
- Modern Libraries
- Permissions Management
- Access Control

---

## Security

- MFA Deployment
- Conditional Access
- Identity Protection
- Risk Investigation
- Audit Review

---

## Helpdesk Operations

- User Onboarding
- User Offboarding
- Access Requests
- Permission Troubleshooting
- Authentication Troubleshooting

---

# Lab Statistics

```text
Users:                      20+
Admin Accounts:              5
Shared Mailboxes:            5
Distribution Lists:          5
Department Teams:            5
Private Channels:            1+
Shared Channels:             1+
SharePoint Sites:            5
Document Libraries:          4+
Conditional Access Policies: 2
```

---

# Future Enhancements

- Hybrid Identity (Entra Connect)
- OneDrive Administration
- Microsoft Purview
- Retention Policies
- DLP Policies
- Microsoft Graph PowerShell
- Exchange PowerShell Automation
- Compliance Auditing
