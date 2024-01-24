# Sales


## Flow

``` mermaid
 graph LR;
 EB[EnergyBoss Invoice] -- Post --> SAP[SAP FI]
 EB -- Email PDF --> Outlook[Dealhandler mailbox]
 Outlook --> PA_MailTrigger[PowerAutomate: Trigger on mail]
 PA_MailTrigger --> Dataverse[Dataverse: InvoiceTable]
 Dataverse -- New / modified --> PA_TableTrigger[PowerAutomate: Table trigger]
 PA_TableTrigger[PowerAutomate: Table trigger] -- PDF --> Cradl[CradlAI - Parse invoice]
 PA_TableTrigger --> PA_CreateFolder[Folder and files]
 PA_TableTrigger -- PDF --> SignHub[SignHub digital seal]
 Cradl -- Webhook --> PA_WebhookTrigger
 PA_WebhookTrigger -- Invoice --> Dataverse 
 SignHub -- Blob trigger --> PA_BlobTrigger
 PA_BlobTrigger -- Signed PDF --> Dataverse
 Dataverse -- Lookup --> Atlas[Atlas: EnergyBoss and SAP]
 Dataverse -- Email invoice --> EndCustomer[End customer]
 
```