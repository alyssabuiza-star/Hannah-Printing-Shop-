# 10. UML Deployment Diagram — Provisional

**Scope:** Provisional runtime nodes and artifacts. Generic hosting names are used because the final provider and implementation settings must be confirmed.

```mermaid
flowchart LR
    Device["Customer / Staff Device<br/>Execution environment: Browser"]
    Web["Web Hosting Node<br/>Artifact: Web UI"]
    App["Application Runtime Node<br/>Artifact: Application/API"]
    DB[("Database Node<br/>Artifact: Relational database")]
    FileStore[("Private File Storage Node<br/>Artifact: Uploaded documents")]

    Device -->|HTTPS| Web
    Web -->|HTTPS / API requests| App
    App -->|SQL over private network| DB
    App -->|Private storage API or file I/O| FileStore
```

**Key:** Nodes represent runtime environments; labels inside nodes identify deployed artifacts; every connection is labelled with a protocol or access method.

**Provisional assumptions to confirm:** Hosting provider, application runtime, database engine, private file storage, backups, and access controls. No secrets, credentials, or real server addresses are included.
