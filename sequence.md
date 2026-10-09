# 5. UML Sequence Diagram — Request Submission, Status Updates, and Pickup Payment

**Scope:** A higher-risk workflow involving uploaded files, request persistence, status changes, and payment recording.

```mermaid
sequenceDiagram
    actor Customer
    participant UI as Web UI
    participant App as Application
    participant DB as Database
    participant Staff as Shop Staff

    Customer->>UI: Enter request details and upload file
    UI->>App: Submit request and file metadata
    App->>App: Validate required details and file
    alt Request is invalid
        App-->>UI: Return validation errors
        UI-->>Customer: Show errors for correction
    else Request is valid
        App->>DB: Save request and queue information
        DB-->>App: Return saved request identifier
        App-->>UI: Return request number and initial status
        UI-->>Customer: Display confirmation and status
        Staff->>App: Review request
        App->>DB: Retrieve request details
        DB-->>App: Return request details
        App-->>Staff: Show request for review
        alt Request rejected
            Staff->>App: Set status to REJECTED
            App->>DB: Persist updated status
            DB-->>App: Confirm update
            App-->>Staff: Confirm status update
        else Request accepted
            Staff->>App: Set status to ACCEPTED / QUEUED
            App->>DB: Persist updated status
            DB-->>App: Confirm update
            Staff->>App: Update status to PROCESSING, then COMPLETED
            App->>DB: Persist status changes
            DB-->>App: Confirm updates
            App-->>Customer: Make updated status available to view
            Customer->>Staff: Visit shop to pick up documents and pay
            Staff->>App: Record payment made at pickup
            App->>DB: Save payment record and pickup status
            DB-->>App: Confirm saved record
            App-->>Staff: Confirm payment/pickup record
        end
    end
```

**Key:** Solid arrows are requests/actions; dashed arrows are replies. No external payment gateway is called. Payment is recorded only after the customer pays at the shop.
