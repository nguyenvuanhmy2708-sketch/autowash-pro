```mermaid
graph LB
    subgraph "External Actors"
        Customer["Customer"]
        Staff[" Staff"]
        Admin["Admin"]
        Bank["Banking App"]
        Notify[" Notification Service"]
    end
    
    subgraph "AutoWash Pro System"
        System["Smart Automated Car Wash<br/>Management System"]
    end
    
    %% Customer interactions
    Customer -->|Register, Login, Book, View Queue| System
    Customer -->|Pay for Services| System
    Customer -->|Earn Loyalty Points| System
    
    %% Staff interactions
    Staff -->|Check-in Customers| System
    Staff -->|Update Wash Status| System
    Staff -->|Confirm Payments| System
    Staff -->|View Dashboard| System
    
    %% Admin interactions
    Admin -->|Configure System| System
    Admin -->|Manage Promotions| System
    Admin -->|View Analytics| System
    
    %% External services
    System -->|Process QR Payments| Bank
    Bank -->|Payment Confirmation| System
    
    System -->|Send Notifications| Notify
    Notify -->|SMS/Email/Push| Customer
    
    style System fill:#4A90E2,stroke:#2E5C8A,stroke-width:3px,color:#fff
    style Customer fill:#50E3C2,stroke:#2E8C74,stroke-width:2px
    style Staff fill:#F5A623,stroke:#C87A1A,stroke-width:2px
    style Admin fill:#9013FE,stroke:#6A0DAD,stroke-width:2px
    style Bank fill:#E74C3C,stroke:#C0392B,stroke-width:2px
    style Notify fill:#27AE60,stroke:#1E8449,stroke-width:2px

    style Customer fill:#50E3C2,stroke:#2E8C74,stroke-width:2px
    style Staff fill:#F5A623,stroke:#C87A1A,stroke-width:2px
    style Admin fill:#9013FE,stroke:#6A0DAD,stroke-width:2px
    style Bank fill:#E74C3C,stroke:#C0392B,stroke-width:2px
    style Notify fill:#27AE60,stroke:#1E8449,stroke-width:2px
