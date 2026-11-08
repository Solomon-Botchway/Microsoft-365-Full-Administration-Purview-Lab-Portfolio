## Complete Microsoft 365 Environment Diagram
```mermaid {preview="true"}
flowchart TB

    Users[20 Users]

    Users --> Entra[Microsoft Entra ID]

    Entra --> Groups[Security Groups]
    Entra --> Admins[Admin Roles]
    Entra --> MFA[MFA]
    Entra --> CA[Conditional Access]
    Entra --> Risk[Identity Protection]

    Groups --> Exchange[Exchange Online]
    Groups --> Teams[Microsoft Teams]
    Groups --> SharePoint[SharePoint Online]

    Exchange --> SharedMail[Shared Mailboxes]
    Exchange --> DistLists[Distribution Lists]

    Teams --> HRTeam[HR Team]
    Teams --> ITTeam[IT Team]
    Teams --> FinTeam[Finance Team]
    Teams --> SalesTeam[Sales Team]
    Teams --> CSGTeam[CSG Team]

    SharePoint --> Libraries[Document Libraries]

    Libraries --> Payroll[Payroll Restricted Library]

    Risk --> SignInLogs[Sign-In Logs]
    Risk --> AuditLogs[Audit Logs]
```



## 1. High-Level Microsoft 365 Architecture

```mermaid {preview="true"}
flowchart TB

    User[Users]

    User --> Entra[Microsoft Entra ID]

    Entra --> Exchange[Exchange Online]
    Entra --> Teams[Microsoft Teams]
    Entra --> SharePoint[SharePoint Online]
    Entra --> OneDrive[OneDrive for Business]

    Exchange --> SharedMailboxes[Shared Mailboxes]
    Exchange --> DLs[Distribution Lists]

    Teams --> TeamsChannels[Teams & Channels]

    SharePoint --> Sites[Department Sites]
    Sites --> Libraries[Document Libraries]

    Entra --> CA[Conditional Access]
    Entra --> MFA[MFA]
    Entra --> IDP[Identity Protection]
```

## 2. Finance Department Access Model
```mermaid {preview="true"}
flowchart TB

    User[Finance User]

    User --> FinanceTeam[Finance Team]

    FinanceTeam --> Budgets[Budgets Library]
    FinanceTeam --> Invoices[Invoices Library]
    FinanceTeam --> Projects[Projects Library]

    PayrollUser[Payroll User]

    PayrollUser --> PayrollGroup[Finance-Payroll Group]

    PayrollGroup --> PayrollLibrary[Payroll Library]

    FinanceTeam -. No Access .-> PayrollLibrary
```


## 3. Teams and SharePoint Relationship
```mermaid {preview="true"}
flowchart TD

    Team[Finance Team]

    Team --> Channel1[General]
    Team --> Channel2[Projects]
    Team --> Channel3[Budgets]
    Team --> Channel4[Payroll Private Channel]

    Team --> M365Group[Microsoft 365 Group]

    M365Group --> Site[Finance SharePoint Site]

    Site --> Docs[Documents Library]
    Site --> Budgets[Budgets Library]
    Site --> Projects[Projects Library]
    Site --> Payroll[Payroll Library]
```

## 4. Shared Mailbox Access Model

```mermaid {preview="true"}
flowchart LR

    FinanceUsers["Finance Users"]

    FinanceUsers --> MailGroup["Finance Mail Enabled Group"]

    MailGroup --> SharedMailbox["Finance Shared Mailbox"]

    SharedMailbox --> ReadMail["Read Email"]

    SharedMailbox --> SendAs["Send As Permission"]

    SharedMailbox --> SharedCalendar["Shared Calendar"]
```


## 5. RBAC Model

```mermaid {preview="true"}
flowchart TB

    GlobalAdmin[Global Administrator]

    ExchangeAdmin[Exchange Administrator]

    TeamsAdmin[Teams Administrator]

    SPAdmin[SharePoint Administrator]

    HelpdeskAdmin[Helpdesk Administrator]

    GlobalAdmin --> Tenant[Tenant Management]

    ExchangeAdmin --> Exchange[Exchange Online]

    TeamsAdmin --> Teams[Teams Administration]

    SPAdmin --> SharePoint[SharePoint Administration]

    HelpdeskAdmin --> Passwords[Password Resets]
    HelpdeskAdmin --> Users[User Support]

    HelpdeskAdmin -. Blocked .-> Exchange
    HelpdeskAdmin -. Blocked .-> Teams
    HelpdeskAdmin -. Blocked .-> SharePoint
```

## 6. Conditional Access Workflow
```mermaid {preview="true"}
flowchart TD

    User[Administrator]

    User --> Login[Sign In]

    Login --> Policy[Conditional Access Policy]

    Policy --> MFA[MFA Required]

    MFA --> Success[Access Granted]

    Policy --> Failure[MFA Not Completed]

    Failure --> Block[Access Blocked]
```

## 7. Identity Protection Investigation
```mermaid {preview="true"}
flowchart TD

    Detection[Risk Detection]

    Detection --> RiskUser[Risky User]

    RiskUser --> Logs[Review Sign-In Logs]

    Logs --> Analyze[Analyze Activity]

    Analyze --> Safe[Mark Safe]

    Analyze --> Reset[Reset Password]

    Reset --> Revoke[Revoke Sessions]

    Revoke --> MFA[Require MFA Re-registration]
```

## 8. Troubleshooting Methodology
```mermaid {preview="true"}
flowchart TD

    Issue[User Reports Issue]

    Issue --> Identify[Identify Service]

    Identify --> Exchange[Exchange]
    Identify --> Teams[Teams]
    Identify --> SharePoint[SharePoint]
    Identify --> Entra[Entra ID]

    Exchange --> LicenseCheck[Check License]
    Teams --> LicenseCheck
    SharePoint --> LicenseCheck
    Entra --> LicenseCheck

    LicenseCheck --> Permissions[Check Permissions]

    Permissions --> Logs[Review Logs]

    Logs --> Resolution[Implement Fix]

    Resolution --> Test[Test with User]

    Test --> Closed[Ticket Closed]
```


## 9. User Onboarding Workflow
```mermaid {preview="true"}
flowchart TD

    A[New Starter Request] --> B[Create User in Entra ID]

    B --> C[Assign License]

    C --> D[Assign Department]

    D --> E[Add Security Groups]

    E --> F[Add Mail Enabled Groups]

    F --> G[Add Distribution Lists]

    G --> H[Grant Shared Mailbox Access]

    H --> I[Assign Team Memberships]

    I --> J[Validate SharePoint Access]

    J --> K[Test Login]

    K --> L[User Ready]
```

## 10. User Offboarding Workflow

```mermaid {preview="true"}
flowchart TD

    A[Termination Request]

    A --> B[Block Sign-In]

    B --> C[Remove Team Memberships]

    C --> D[Remove Group Memberships]

    D --> E[Remove Shared Mailbox Access]

    E --> F[Remove Distribution List Access]

    F --> G[Remove License]

    G --> H[Review Audit Logs]

    H --> I[Disable Account]

    I --> J[Archive / Retain Data]
```
 
## 11. Auditor Access Request Workflow

```mermaid {preview="true"}
flowchart TD

    A[Audit Request Raised]

    A --> B[Create Temporary User]

    B --> C[Assign License]

    C --> D[Add Finance Team]

    D --> E[Add Finance Projects]

    E --> F[Add Finance Payroll]

    F --> G[Add Shared Mailbox Access]

    G --> H[Add Distribution Lists]

    H --> I[Grant SharePoint Access]

    I --> J[Validate Resource Access]

    J --> K[Audit Activities Performed]

    K --> L[Remove Access]

    L --> M[Disable Account]
```



