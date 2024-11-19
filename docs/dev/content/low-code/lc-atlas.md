# Atlas

[What is Atlas](https://dev.atlas.equinor.com/docs/articles/what-is-atlas/what-is-atlas.html)


## Data products 


### EnergyBoss

### Endur

### Dispatch

## Citizen Analytics on Demand (CAD)

CAD typically have to use cases:

- Construct data products that combines data from different source
- Make your own specific data product (only relevant / limited to a area/department) from raw data (json, xml, xlsx)

[What is CAD](https://dev.atlas.equinor.com/docs/articles/cad/what-is-cad.html)

### CAD Tips and tricks

[CAD Academy](https://dev.atlas.equinor.com/docs/users/cad-academy/README.html)


### User uploads data

In cases where there is structured information in form of .xlsx or similiar, that are of no general interesst for the broader consumers of Atlas data product, one can leverage CAD.

If you don't want to expose the CAD for "data entry" purposes (feeding in files), you make use of PowerPlatform in combination with CAD. This also enabled features for audit logging (what credential uploaded the file, status of data processing).


- Blob event trigger


``` mermaid
sequenceDiagram
    User-->>+PowerApp: Authorize
    PowerApp->>+Blob: Uploads file
    Blob-->>+CAD: Trigger pipeline
    Blob-->>+PowerAutomate: Trigger blob event
    PowerAutomate->>+Dataverse: Write filename and status
    CAD-->>+Notebook: Invoke
    Notebook->>+SQL: Append to db
    Notebook-->>CAD: Status
    CAD-->>PowerAutomate: Trigger webhook
    PowerAutomate->>Dataverse: Update status
    
```