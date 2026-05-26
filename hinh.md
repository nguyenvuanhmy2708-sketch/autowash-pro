
 ```mermaid
graph TB

    %% =========================
    %% TOP ACTORS
    %% =========================

    Customer["Customer"]
    Staff["Staff"]
    Admin["Admin"]

    %% =========================
    %% SYSTEM
    %% =========================

    subgraph "AutoWash Pro System"
        System["Smart Automated Car Wash<br/>Management System"]
    end

    %% =========================
    %% BOTTOM EXTERNAL SERVICE
    %% =========================

    Bank["Banking App"]

    %% =========================
    %% LAYOUT CONTROL
    %% =========================

    Customer --- Staff
    Staff --- Admin

    %% =========================
    %% CUSTOMER INTERACTIONS
    %% =========================

    Customer -->|Register, Login, Book, View Queue| System
    Customer -->|Pay for Services| System
    Customer -->|Earn Loyalty Points| System

    %% =========================
    %% STAFF INTERACTIONS
    %% =========================

    Staff -->|Check-in Customers| System
    Staff -->|Update Wash Status| System
    Staff -->|Confirm Payments| System
    Staff -->|View Dashboard| System

    %% =========================
    %% ADMIN INTERACTIONS
    %% =========================

    Admin -->|Configure System| System
    Admin -->|Manage Promotions| System
    Admin -->|View Analytics| System

    %% =========================
    %% BANKING INTERACTIONS
    %% =========================

    System -->|Process QR Payments| Bank
    Bank -->|Payment Confirmation| System

    %% =========================
    %% STYLES
    %% =========================

    style System fill:#4A90E2,stroke:#2E5C8A,stroke-width:4px,color:#fff

    style Customer fill:#50E3C2,stroke:#2E8C74,stroke-width:2px
    style Staff fill:#F5A623,stroke:#C87A1A,stroke-width:2px
    style Admin fill:#9013FE,stroke:#6A0DAD,stroke-width:2px
    style Bank fill:#E74C3C,stroke:#C0392B,stroke-width:2px
```
