# Microsoft Purview - Compliance, Auditing & Governance

## Overview

Implemented and explored Microsoft Purview to develop practical experience with Microsoft 365 compliance, auditing, content discovery, retention, investigations and governance capabilities.

The objective was to understand how Microsoft 365 workloads including Exchange Online, SharePoint Online, OneDrive for Business, Microsoft Teams and Microsoft Entra ID integrate with Purview to provide centralized auditing and compliance functionality.

---

## Microsoft Purview Exploration

Accessed and reviewed the following Microsoft Purview solutions:

- Audit
- eDiscovery
- Content Search
- Data Lifecycle Management
- Retention Policies
- Role Based Access Controls
- Compliance Administration

---

## Audit Configuration

During initial testing, Microsoft Purview auditing had not previously been enabled within the tenant.

After enabling auditing, activity was generated across multiple Microsoft 365 workloads to build a known data set for investigation and validation.

Activities generated included:

### Microsoft Entra ID

- User administration
- Group membership changes
- Role assignments
- Password reset requests
- Administrative actions

### Exchange Online

- Email send
- Email forward
- Email delete
- Shared mailbox access

### OneDrive for Business

- File upload
- File creation
- File modification
- File deletion
- File restoration
- Access delegation

### SharePoint Online

- Document library activity
- File upload
- File rename
- File deletion
- Recycle Bin activity
- Permission changes

### Microsoft Teams

- Team creation
- Channel creation
- Channel messaging
- File uploads
- Collaboration activities

---

## Audit Investigation Testing

Created controlled audit scenarios to simulate compliance and investigation workflows.

### Example Scenario

Created:

```text
Payroll-2027.xlsx
```

Actions performed:

- Upload
- Rename
- Edit
- Delete
- Restore

Validation data collected:

```text
Created By:
Herty Yankson (FIN)

Deleted By:
Alpha Botchway (HR)

Location:
Finance Team Payroll Library
```

This provided a known activity trail for later audit validation.

---

## Microsoft Teams Investigation Scenario

Created:

```text
Audit Testing Channel
```

Activities performed:

- Posted messages
- Uploaded documents
- Shared files
- Generated collaboration activity

Purpose:

To create audit events across Teams and SharePoint Online workloads.

---

## eDiscovery & Content Search Investigation

Explored:

```text
Purview
→ eDiscovery
→ Content Search
```

Attempted searches across:

- Exchange Online
- SharePoint Online
- OneDrive for Business
- Microsoft Teams

---

## Troubleshooting Findings

### Audit Searches Returning Zero Results

Audit jobs completed successfully but returned:

```text
0 Results
```

Investigation identified likely causes:

- Auditing was enabled after earlier Microsoft 365 activities had already taken place.
- Audit data ingestion requires time before becoming searchable.
- Newly generated activities may take time to appear within Purview searches.

### Learning Outcome

An audit search completing successfully does not necessarily indicate audit records are immediately available.

Administrators should allow sufficient time for audit ingestion before conducting investigations.

---

## eDiscovery Permission Investigation

Encountered:

```text
Missing required permissions to view case.
```

and

```text
You are not a member of the Content Search case.
```

### Discovery

Microsoft Purview uses a dedicated role and permission model.

Holding the Global Administrator role alone does not automatically provide access to:

- eDiscovery Cases
- Content Search Cases
- Compliance Investigations

### Learning Outcome

Purview permissions must be assigned separately through compliance role groups and case memberships.

---

## Compliance Administration Skills Developed

### Auditing

- Audit Search
- Audit Investigation
- Activity Tracking
- User Action Validation

### eDiscovery

- Case Management Concepts
- Content Discovery
- Search Permissions
- Compliance Roles

### Governance

- Compliance Administration
- Data Investigation
- Information Governance Concepts
- Retention Concepts

### Troubleshooting

- Audit Data Ingestion Validation
- Compliance Permission Troubleshooting
- eDiscovery Access Resolution
- Purview Configuration Investigation

---

## Key Learning Outcomes

- Microsoft Purview provides centralized auditing across Microsoft 365 services.
- Audit events require ingestion time before becoming available for investigation.
- OneDrive, SharePoint, Teams and Exchange all contribute audit records to Purview.
- eDiscovery and Content Search use dedicated compliance permissions.
- Compliance administration is separate from traditional Microsoft 365 administration.
- Effective investigations require known audit activity and validation scenarios.

---

## Next Objectives

- Validate successful audit record ingestion.
- Perform Exchange Online audit investigations.
- Perform SharePoint and OneDrive audit searches.
- Configure Retention Policies.
- Configure Retention Labels.
- Explore eDiscovery investigations.
- Implement Data Lifecycle Management controls.

<img width="1897" height="895" alt="image" src="https://github.com/user-attachments/assets/dbbea261-348d-4ff8-aea4-abaa175f03e8" />

<img width="1870" height="880" alt="image" src="https://github.com/user-attachments/assets/55dbdc0f-2961-4667-b0a0-acd202e9f9fe" />

- <img width="1441" height="784" alt="image" src="https://github.com/user-attachments/assets/d042a39f-9cf5-405e-ab51-450175d04e4c" />

```mermaid {preview="true"}
flowchart TB

    Entra["Microsoft Entra ID"]
    Exchange["Exchange Online"]
    Teams["Microsoft Teams"]
    SharePoint["SharePoint Online"]
    OneDrive["OneDrive for Business"]

    Entra --> Purview["Microsoft Purview"]
    Exchange --> Purview
    Teams --> Purview
    SharePoint --> Purview
    OneDrive --> Purview

    Purview --> Audit["Audit Search"]

    Purview --> Content["Content Search"]

    Purview --> EDiscovery["eDiscovery"]

    Purview --> Retention["Retention Policies"]

    Purview --> Governance["Compliance & Governance"]
```

```mermaid {preview="true"}
flowchart LR

    Activity["User Activity"]

    Activity --> Upload["Upload File"]
    Activity --> Edit["Edit File"]
    Activity --> Delete["Delete File"]
    Activity --> Mail["Send Email"]
    Activity --> Teams["Teams Message"]

    Upload --> Ingest["Audit Ingestion"]
    Edit --> Ingest
    Delete --> Ingest
    Mail --> Ingest
    Teams --> Ingest

    Ingest --> Purview["Microsoft Purview"]

    Purview --> Search["Audit Search"]

    Search --> Investigation["Compliance Investigation"]

    Investigation --> Findings["Investigation Findings"]
```



