# Gas Value Chain

In the context of marketing of piped gas.

Frame conditions and Equinor's implementation.


Improvement List

Improvement Dashboard

![Send :fontawesome-solid-paper-plane:](https://forms.office.com/e/zFgZ9ahas6){ .md-button }

## Gas Market

``` mermaid
flowchart LR
    subgraph Upstream
    GasField --> Processing
    Processing --> Liquefaction
    end
    subgraph Midstream
    Processing --> Transport-Network
    Liquefaction  --> Shipping
    Shipping --> Re-gasification
    Re-gasification --> Transport-Network
    Transport-Network --> Storage
    Transport-Network --> Utilities
    Storage --> Utilities
    end
    subgraph Downstream
    Utilities --> Consumers 
    end
    
```

### Pricing and derivates

[Study on the functioning of the European Gas Market](https://www.ice.com/publicdocs/Oxera_Study_into_the_Functioning_of_the_European_Gas_Market.pdf)



### Gas bilateral agreement and trading

A contractual agreement to deliver a volume pr period for the contract period.

Bilateral contract:
``` mermaid
flowchart LR
    Customer <-- Contract --> Equinor
    Customer -- Nominates volume --> EDIGAS
    Customer -- Nominates volume --> Portal
    Customer -- Nominates volumes --> Email
    Equinor -- Allocate/Nominate volume --> Dispatch
    Dispatch -- Allocate --> EDIGAS
    EDIGAS -- Volumes --> Dispatch
    Portal --> Equinor
    Email --> Equinor
    
    
    Equinor -- Invoices volumes --> Customer
```

Trading:
``` mermaid
flowchart LR
    Trader -- Initiate deal --> ENTITY{UK or US}
    ENTITY -- US --> US{OTC or Exchange}
    ENTITY -- UK --> UK{OTC or Exchange}
    UK -- Exchange --> UK_EX[Directly, Trayport, Call]
    UK -- OTC --> UK_OTC[Trayport via broker or trader]
    UK_OTC --> Endur
    UK_EX --> ICE
    ICE --> Endur
    US -- OTC --> Endur
    US -- Exchange --> ICE
    Endur --> SAP
    Endur --> Invoice
```

#### Volumes

[EDIGAS](https://www.edigas.org/) is communication standard for exchanging information regarding physical flow of gas.

In cases where EDIGAS is not used, the exhange of information will be in a format specific in the contract (mail, portals etc). This will be a complicating factor in operations.


### Actors

The actors in the European Gas marked is defined by Easee gas

[Easee Gas](https://easee-gas.eu/membership-segments)

- Producer or Production Facility Operator (Equinor)
- Transmission System Operator (Gassco)
- Distribution System Operator
- Storage System Operator (Equinor / DC)
- LNG System Operator
- Trader & Shipper (Equinor / DC)
- Supplier (Equinor)
- End-user or Final Customer
- Prosumer

### Standards

Energy contracts:
[EFET](https://www.efet.org/)

Communication between actors in the gas market
[EDIGAS](https://easee-gas.eu/edig-s)

Open invoice standards (not in use)
[PEPPOL](https://peppol.org/)

#### Pricing
Gas prices are for typically indexed on the hubs when dealing in Europe:

- Hub-Spot
- Oil indexation
- Regulated prices

The prices are delivered through Morningstar. 

#### Derivates

Over the counter (**OTC**): Bespoke agreements

**Exchange**: Standard contracts that are trades on exchanges and centrally cleared

The common derivates are:
 - Futures (Exchange)
 - Forwards (OTC)
 - Options (Exchange)
 - Swaps (OTC)

 #### Contract

- Price
- Volume
- Delivery
- Invoice terms
- Force majeur
- Nomination terms

The [EFET](https://efet.org/files/documents/EFET%20General%20Agreement%20Natural%20Gas%20V2.0(a).pdf) is contract standard for the structure of the contract and some of the terms.

## Equinor 

### IT Architecture

Description of overall system components and capabilities. It does not describe the business processes.

[EITA](https://ea.equinor.com/companyea/?oid=3d69c350-7a81-480f-b869-d255f87e6a5c)


### Management System

The management system explain what requirement need to be met for specific business processes. It does not desccribe business processes.

[Management System](https://aris.equinor.com/#default/item/c.L3ProcessClusterMap.Production.AJ0msLHeEeA2QABQVrsUrw.-1/~AYBbIm1vZGVsVmlld2VyNCJd)

### IT Systems - Commercial Gas Operations

``` mermaid
flowchart LR
    style Gas_grid fill:#1979ff
    style Price_sources fill:#1979ff
    Gas_grid -- EDIGAS --> Dispatch
    Dispatch <-- AST / Volumes --> Endur
    Dispatch -- Volumes --> EnergyBoss
    Trading_platforms -- Deals --> Endur
    Endur -- PDF --> Invoice_UK
    Invoice_UK -- Email --> Customer
    Endur -- Prices --> EnergyBoss
    Endur -- PnL/Exposure --> SAP_BW
    Endur -- Deals --> CRisk
    Endur -- Post --> SAP_FI
    EnergyBoss -- Post --> SAP_FI
    EnergyBoss -- PDF --> Invoice_ASA
    Dispatch --> EnergyBossValidaton
    MorningStar --> EnergyBossValidaton
    Invoice_ASA -- Email --> Customer
    MorningStar -- Prices --> Endur
    Price_sources --> MorningStar
 
```

#### Systen overview
| System | Description | Responisible|
|:-----  | :-----      | :-----      |
| Dispatch  | Equinor developed software for handling the physcial flow of gas | BIP (Setup), SO (Operations) |
| Endur  | Energy Trading and Risk Management system, that enables data flow across trading, operations, credit, contract and account functions | BIP |
| EnergyBoss  | Equinor developed software for invoicing gas contract and handling the SDFI split with Norwegian government | DHG |
| |     |     |
| Morningstar  | Price provider that gathers price data from multiple sources | DDI |
| Trading Platforms  | Trading platform such as Trayport (screentrading) | ODL |
| |     |     |
| SAP FI  | SAP Financial module, used for posting invoices, payment settlement, distribution, tax etc | F&C |
| SAP BW  | SAP Business Warehouse, used for generating Profit and Loss dashboard and marked exposure | F&C |
| CRisk  | Application used for credit risk | Risk |
| ICertis  | Contract archive | ODL |
| Leads  | Sales lead to contract mgmt | GM |

