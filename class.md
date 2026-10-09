# 6. UML Class Diagram — Hannah Printing Shop Domain Model

**Scope:** Core domain classes, typed attributes, associations, multiplicities, and status enumerations.

```mermaid
classDiagram
    class User {
      +int userId
      +string name
      +string email
      +UserRole role
    }
    class PrintingRequest {
      +int requestId
      +datetime submittedAt
      +RequestStatus status
      +string pickupInfo
    }
    class RequestItem {
      +int itemId
      +int copies
      +string printOptions
      +string notes
    }
    class UploadedFile {
      +int fileId
      +string fileName
      +string storagePath
      +string mimeType
    }
    class PrintingService {
      +int serviceId
      +string name
      +string description
      +decimal basePrice
    }
    class PaymentRecord {
      +int paymentId
      +decimal amount
      +datetime paidAt
      +string method
    }
    class UserRole {
      <<enumeration>>
      CUSTOMER
      STAFF
      ADMIN
    }
    class RequestStatus {
      <<enumeration>>
      SUBMITTED
      UNDER_REVIEW
      ACCEPTED
      REJECTED
      QUEUED
      PROCESSING
      COMPLETED
      PICKED_UP
    }

    User "1" --> "0..*" PrintingRequest : submits
    PrintingRequest "1" *-- "1..*" RequestItem : contains
    RequestItem "0..*" --> "1" PrintingService : selects
    RequestItem "1" --> "0..*" UploadedFile : has files
    PrintingRequest "1" --> "0..1" PaymentRecord : has payment record
    User --> UserRole : role
    PrintingRequest --> RequestStatus : status
```

**Key:** `1`, `0..1`, `0..*`, and `1..*` show association multiplicity. Enumerations define valid role and request-status values.

**Validation note:** This is a draft domain model. Confirm that each association, field, and multiplicity matches your actual MVP and database implementation.
