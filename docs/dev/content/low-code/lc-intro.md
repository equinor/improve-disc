# Platform overview

There are currently 4 well established platform in Equinor for doing low-code development

 - Microsoft PowerPlatform (Automate, Apps)
 - Microsoft Fabric (Generic Data)
 - Atlas CAD (M&S Data platform)
 - Blue Prism Automate (Robotic Process Automation)

There is established an dedicated Power Platform environment for MMP. 

## Resources

| **System**    | **Description** | **Access** | **Links** |
|---------------|-----------------|------------|-----------|
| PowerBI       |                 |            |           |
| PowerPlatform |                 |            |  [M&S PowerPlatform Dev](https://make.powerautomate.com/environments/e933e4bc-1758-4a04-9ea1-44ff9a1269c8/home)         |
| Atlas CAD     |                 |            |  [Atlas COG](https://web.azuresynapse.net/?workspace=%2fsubscriptions%2ffd2a1b0e-280d-48f3-b7c5-1b9c0b796c70%2fresourceGroups%2fcad-cog-s1-rg-m81%2fproviders%2fMicrosoft.Synapse%2fworkspaces%2fcad-cog-s1-syn-m81)         |
| Atlas         |                 |            |           |
| GitHub        |                 |            |           |
| DevOps        |                 |            |           |



## Power Platform Governance

### User Management

The accesses for any "product" that you make and make available in **production** (Sharepoint sites, PowerApps, PowerBI) should be administered through an AD group. 

``` mermaid
sequenceDiagram
    participant User
    participant AccessIT
    participant SecurityRole
    User->>AccessIT: Apply for role
    loop Approval
        AccessIT->>AccessIT: Approve/Decline
    end
    AccessIT->>SecurityRole: User is added to group, grants security role
```


#### AccessIT (User Groups)
AccessIT is used to administrate user groups

#### Security roles (PowerPlatform)
Make security roles that you grant to.   

# Services

## PDF interpretation

In the topic of PDF interpretation, there are three fundamental methods:

 - Text scraping
 - AI: Bounding box annotation
 - AI: Annotation

Under the topic of AI, there can be managed and unmanaged models

### CradlAI (Annotation, managed)

CradlAI is a 3rd party software as a service for a pure AI driven model with a inbuilt workflow enginge for define threshold. In use cases involving invoices etc, where it is essential with defined rules this a preferred solution.



### AIBuilder (Bounding box, unmanaged)

AIBuilder is a PowerPlatform component for leverage AI capabilities in an low code environment. It ranges from extracting structured/unstructured data from PDF document to sentiment analysis in texts etc. The service is very generic and you will have to implement control logic yourself. 

## PDF sign/seal

There is established a solution for digital sealing / signing of invoice documents. The purpose of this is to lock an invoice for editing and sign it with Equinor digital signatur in order to it an offical and secure document.


# Documentation and showcasing

# Development service providers

You are strongly encourged to involve an improvement leader with M&S, prior to ordering a service

- COG
- COL
- CAM

The following offerings are available as a service in ServiceNow:

Business Process Automation

Center for Enablement

Atlas Data Squads 