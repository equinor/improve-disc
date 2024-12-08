::: mermaid
flowchart LR
    Employee -- Improvement Suggestion --> Improvement
    Improvement -- Asses and priortize --> ImpLead
:::


::: mermaid
erDiagram
    Lead ||--|| Lead_Status : lookup

    Lead {
        int lead_id PK
        int lead_status
        string lead_name
        text lead_description
        string ng_deal_id
        string etrm_deal_id
        datetime sign_off_requested
        datetime approval_request
        bool restricted
        datetime restrict_time
        int approvals
        int mandate
        int deal_information
        int pricing_information
        int volume_information
        int contract_information
    }

    Lead_Status {
        int lead_status_id PK
        string lead_status_title
    }

    Lead ||--O{ Approval : contains

    Approval {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

    Lead ||--O{ Mandate : contains

    Mandate {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

    Lead ||--O{ Deal_Information : contains

    Deal_Information {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

    Lead ||--O{ pricing_information : contains

    pricing_information {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

    Lead ||--O{ volume_information : contains

    volume_information {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

    Lead ||--O{ contract_information : contains

    contract_information {
        int approval_id PK
        int lead_id FK
        string role
        boolean recommend
        datetime created_at
        datetime valid_until
        int ops_impl_complexity
        int ops_ops_complexity
        int risk_credit_exposure
        int trading_hedge
        text comment
    }

:::

Mappings

::: mermaid
mindmap
  root((contract))
    Gas trading
      Sale
      Swap
    Upstream
      Purhcase
    Marketing/Origination
      Sale
        End User
        Hub Sales
      Amendment
    Asset Management
        Storage
        Capacity





:::