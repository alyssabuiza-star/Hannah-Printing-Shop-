# 4. UML Activity Diagram — Submit Printing Request to Pickup

**Scope:** Core workflow from customer submission through staff processing and in-shop pickup.

```mermaid
flowchart TD
    Start((Start)) --> C1

    subgraph Customer["Customer"]
      C1[Prepare document and request details]
      C2[Upload file and submit request]
      C3[Check request status and pickup information]
      C4[Visit shop and pay at pickup]
    end

    subgraph System["System"]
      S1[Validate file and request details]
      D1{Are details valid?}
      S2[Save request and assign queue order]
      S3[Display request number and status]
      S4[Update status and pickup information]
      S5[Record payment details submitted by staff]
    end

    subgraph Staff["Shop Staff"]
      T1[Review submitted request]
      D2{Accept request?}
      T2[Ask customer to correct details]
      T3[Process printing request]
      T4[Mark request completed]
      T5[Confirm pickup and record in-shop payment]
    end

    C2 --> S1 --> D1
    D1 -- "No" --> T2 --> C1
    D1 -- "Yes" --> S2 --> S3 --> T1 --> D2
    D2 -- "No" --> S4 --> C3
    D2 -- "Yes" --> T3 --> S4 --> C3
    T3 --> T4 --> S4
    S4 --> C4 --> T5 --> S5 --> End((End))
```

**Key:** Diamonds are decisions; branch labels are guard conditions. Payment is made in person at pickup, not through an online gateway.
