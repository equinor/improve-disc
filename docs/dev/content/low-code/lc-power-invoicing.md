# Cases

- Power purchase for assets
- Dudegon - Contract for Differences (CFD)
- DoggerBank

## Power purchase for assets

Danske Commodities is responsible for power purchases for EPN//MMP OPL assets and the invoicing/posting is handled by COG.  

## Process overview

``` mermaid
sequenceDiagram
    participant Email
    participant PowerAutomate
    participant CradlAI
    participant Sharepoint
    participant Dataverse
    participant Approver
    participant EnergyBoss
    Email->>PowerAutomate: Invoice email
    PowerAutomate->>CradlAI: Send invoice PDF
    PowerAutomate->>Sharepoint: Store basic + Cradl ref
    loop Verify
        CradlAI->>CradlAI: Dealhandler verify invoice interpretation
    end
    PowerAutomate->>Sharepoint: Update invoice information
    PowerAutomate->>Dataverse: Write all invoice information
    PowerAutomate-->>Email: Get attachments
    PowerAutomate->>Sharepoint: Upload attachments
    PowerAutomate->>Sharepoint: Lookup invoice approver
    PowerAutomate->>Approver: Send approval request
    Approver->>PowerAutomate: Approve/Reject
    PowerAutomate->>EnergyBoss: Send for payment
```



## Components

- **Sharepoint**
  - Mapping
  - Dealhandler
  - Approvers
  - Worklist
  - Document storage
  - Landing page
- **Dataverse**
  - Invoice table
- **PowerBI**
  - Invoice overview
- **Approval**
  - Invoice approvals
- **PowerAutomate**
  - Email: Get DC Invoice mails v3
  - Sharepoint list: Archive mail
  - Sharepoint list: Get invoice approval
  - Sharepoint list: Send to EnergyBoss
  - Webhook: Validated invoice Cradl
- **CradlAI**
  - Model and workflow


