# 2. C4 Container Diagram — Hannah Printing Shop System

**Scope:** Logical application containers and the main communication paths. Technology choices are provisional and must be confirmed against the actual repository.

```mermaid
flowchart LR
    Customer[Customer<br/>Mobile or desktop browser]
    Staff[Shop Staff / Administrator<br/>Browser]
    UI["Web UI Container<br/>Pages and forms<br/>Technology: confirm from repository"]
    App["Application / API Container<br/>Authentication, request rules,<br/>queue and status workflow<br/>Technology: confirm from repository"]
    DB[("Relational Database<br/>Users, services, requests,<br/>statuses and payment records")]
    Storage[("Private File Storage<br/>Uploaded print documents")]

    Customer -->|HTTPS: use pages, upload files, submit requests| UI
    Staff -->|HTTPS: review requests, manage services/users| UI
    UI -->|HTTPS / application requests| App
    App -->|SQL / database protocol| DB
    App -->|Private file I/O or storage API| Storage

    classDef user fill:#eef5ff,stroke:#3b6ea8,color:#111;
    classDef app fill:#e8f5e9,stroke:#3a7d44,color:#111;
    classDef data fill:#fff4df,stroke:#b7791f,color:#111;
    class Customer,Staff user;
    class UI,App app;
    class DB,Storage data;
```

**Key:** Browser roles are users, UI and Application/API are software containers, and Database/File Storage are data containers.

**Container decision:** This draft shows the Web UI and Application/API as two logical containers. Confirm whether the implementation and deployment actually separate them before final submission. Framework, database engine, hosting provider, and storage technology remain provisional.
