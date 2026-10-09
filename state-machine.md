# 7. UML State Machine Diagram — PrintingRequest Status

**Scope:** Lifecycle of the main entity, `PrintingRequest`. State names correspond to the `RequestStatus` enumeration in `class.md`.

```mermaid
stateDiagram-v2
    [*] --> SUBMITTED: Customer submits request
    SUBMITTED --> UNDER_REVIEW: Staff opens request
    UNDER_REVIEW --> REJECTED: Staff rejects request
    UNDER_REVIEW --> ACCEPTED: Staff accepts request
    ACCEPTED --> QUEUED: Queue order assigned
    QUEUED --> PROCESSING: Staff starts printing
    PROCESSING --> COMPLETED: Printing finished
    COMPLETED --> PICKED_UP: Customer collects documents
    REJECTED --> [*]
    PICKED_UP --> [*]
```

**Key:** Rounded states represent the current condition of a printing request; arrow labels identify events that trigger transitions.

**Validation note:** If the implemented system allows other transitions, revise this diagram and the `RequestStatus` enumeration together so they remain consistent.
