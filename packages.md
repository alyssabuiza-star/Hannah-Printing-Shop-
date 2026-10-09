# 8. UML Package Diagram — Proposed Application Layers

**Scope:** Proposed folder/package responsibilities and dependencies for the Hannah Printing Shop System.

```mermaid
flowchart TD
    subgraph Presentation["Presentation"]
      Pages[Pages and UI Components]
    end
    subgraph Controllers["Controllers"]
      RequestController[Request Controller]
      StatusController[Status Controller]
      ServiceController[Service Controller]
      UserController[User Controller]
    end
    subgraph Services["Business Services"]
      RequestService[Request Service]
      QueueService[Queue Service]
      FileService[File Service]
      PaymentService[Payment Record Service]
    end
    subgraph DataAccess["Data Access / ORM"]
      Models[Domain Models and Repositories]
    end
    subgraph Storage["Storage"]
      DB[(Relational Database)]
      Files[(Private Uploaded Files)]
    end

    Pages --> Controllers
    Controllers --> Services
    Services --> Models
    Models --> DB
    FileService --> Files

```

**Layering rule:** Presentation calls controllers; controllers use business services; business services access persisted data through the data-access layer, and uploaded files are handled through the File Service rather than accessed directly by the browser.
