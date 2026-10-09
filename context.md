# 1. C4 System Context Diagram — Hannah Printing Shop System

**Scope:** People and external systems interacting with the Hannah Printing Shop System.

```mermaid
flowchart LR
    Customer[Customer<br/>Uploads files, submits requests,<br/>checks status and pickup information]
    System["Hannah Printing Shop System<br/>Web-based printing request management<br/>and status tracking"]
    Staff[Shop Staff<br/>Reviews requests, processes orders,<br/>updates status, records pickup payment]
    Admin[Administrator<br/>Manages users and printing services]

    Customer -->|Submit files and printing request; view status| System
    System -->|Request status and pickup information| Customer
    Staff -->|Review requests; update status; record payment| System
    System -->|Request queue and customer request details| Staff
    Admin -->|Manage users and service options| System
    System -->|User and service information| Admin

    classDef person fill:#eef5ff,stroke:#3b6ea8,color:#111;
    classDef system fill:#e8f5e9,stroke:#3a7d44,color:#111;
    class Customer,Staff,Admin person;
    class System system;
```

**Key:** People are shown as role boxes; the central box is the system being designed. Arrows describe the purpose of each interaction.

**Boundary note:** The MVP does not use an external payment processor and does not include online payment or delivery.
