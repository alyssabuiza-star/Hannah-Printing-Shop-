# 11. Entity Relationship Diagram (Draft) — Hannah Printing Shop

**Scope:** Draft relational tables derived from the class diagram. Fields containing personally identifiable information (PII) are marked `[PII]`.

```mermaid
erDiagram
    USERS ||--o{ PRINTING_REQUESTS : submits
    PRINTING_REQUESTS ||--|{ REQUEST_ITEMS : contains
    PRINTING_SERVICES ||--o{ REQUEST_ITEMS : selected_for
    REQUEST_ITEMS ||--o{ UPLOADED_FILES : includes
    PRINTING_REQUESTS ||--o| PAYMENT_RECORDS : has

    USERS {
      int user_id PK
      string name_PII
      string email_PII
      string role
    }
    PRINTING_REQUESTS {
      int request_id PK
      int customer_id FK
      datetime submitted_at
      string status
      string pickup_info
    }
    REQUEST_ITEMS {
      int item_id PK
      int request_id FK
      int service_id FK
      int copies
      string print_options
      string notes
    }
    PRINTING_SERVICES {
      int service_id PK
      string name
      string description
      decimal base_price
    }
    UPLOADED_FILES {
      int file_id PK
      int item_id FK
      string file_name
      string storage_path
      string mime_type
    }
    PAYMENT_RECORDS {
      int payment_id PK
      int request_id FK
      decimal amount
      datetime paid_at
      string method
    }
```

**Key:** `PK` = primary key; `FK` = foreign key; `[PII]` marks personally identifiable information. Crow's-foot symbols indicate one-to-many or optional relationships.

**Validation note:** Confirm foreign-key names and whether uploaded files link to `REQUEST_ITEMS` or directly to `PRINTING_REQUESTS` using the actual database schema before treating this ERD as final.
