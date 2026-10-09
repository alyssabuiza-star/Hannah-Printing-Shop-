# 9. UML Component Diagram — Application/API Components

**Scope:** Main application components, their interfaces, and dependencies. External services are not assumed in this MVP.

```mermaid
flowchart LR
    UI[Web UI]
    Auth[Authentication Component]
    Request[Request Management Component]
    Queue[Queue and Status Component]
    File[File Service]
    Payment[Payment Record Component]
    Persistence[Persistence Adapter]
    DB[(Relational Database)]
    FileStorage[(Private File Storage)]

    UI -->|Sign-in/session interface| Auth
    UI -->|Request and status interface| Request
    Request -->|Queue/status interface| Queue
    Request -->|File upload/retrieval interface| File
    UI -->|Payment record view| Payment
    Request -->|Repository interface| Persistence
    Queue -->|Repository interface| Persistence
    Auth -->|User repository interface| Persistence
    Payment -->|Payment repository interface| Persistence
    File -->|Private storage interface| FileStorage
    Persistence -->|Database driver / SQL interface| DB
```

**Interfaces:** Authentication provides sign-in/session handling; Request Management provides request operations; Queue and Status provides queue/status operations; File Service provides private file upload/retrieval; Payment Record provides in-shop payment entry; Persistence Adapter provides repository access to the relational database.

**Security boundary:** The browser must not access private uploaded files or the database directly. Payment is recorded by staff after in-person payment.
