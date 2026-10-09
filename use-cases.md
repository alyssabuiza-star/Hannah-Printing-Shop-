# 3. UML Use Case Diagram — Hannah Printing Shop MVP

**Scope:** Goal-level actions included in the MVP. Online payment and delivery are excluded.

```mermaid
flowchart LR
    Customer[Customer]
    Staff[Shop Staff]
    Admin[Administrator]

    subgraph System["Hannah Printing Shop System"]
      UC1([Upload document file])
      UC2([Submit printing request])
      UC3([Select printing service])
      UC4([View request status])
      UC5([View pickup information])
      UC6([Review submitted request])
      UC7([Update request status])
      UC8([Record payment at pickup])
      UC9([Manage service options])
      UC10([Manage users])
    end

    Customer --- UC1
    Customer --- UC2
    Customer --- UC3
    Customer --- UC4
    Customer --- UC5
    Staff --- UC6
    Staff --- UC7
    Staff --- UC8
    Admin --- UC9
    Admin --- UC10
```

**Key:** Actors are outside the system boundary; ovals are user goals supported by the MVP.
