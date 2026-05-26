graph LR

    Customer["Customer"]
    Staff["Staff"]
    Admin["Admin"]
    Bank["Banking App"]
    Notify["Notification Service"]

    System["Smart Automated Car Wash<br/>Management System"]

    %% Customer Interactions
    Customer -->|Register / Login| System
    Customer -->|Book Service| System
    Customer -->|Manage Vehicles| System
    Customer -->|Track Queue Status| System
    Customer -->|View Invoices & History| System
    Customer -->|Loyalty & Rewards| System
    Customer -->|Payment Request| System

    %% Staff Interactions
    Staff -->|Check-in Customers| System
    Staff -->|Manage Queue| System
    Staff -->|Update Washing Status| System
    Staff -->|Confirm QR Payments| System
    Staff -->|Manage Service Changes| System
    Staff -->|View Operations Dashboard| System

    %% Admin Interactions
    Admin -->|Configure System Settings| System
    Admin -->|Manage Promotions| System
    Admin -->|Manage Loyalty Program| System
    Admin -->|Manage Membership Tier| System
    Admin -->|View Reports & Analytics| System

    %% Banking App Interactions
    System -->|QR Payment Request| Bank
    Bank -->|Payment Confirmation / Failure| System
    Bank -->|Refund Processing| System

    %% Notification Service Interactions
    System -->|Send Notifications| Notify
    Notify -->|Booking Confirmation| Customer
    Notify -->|Queue Updates| Customer
    Notify -->|Service Completion Alert| Customer
    Notify -->|Loyalty Upgrade Alert| Customer

    %% Styles
    style System fill:#4A90E2,stroke:#2E5C8A,stroke-width:4px,color:#fff

    style Customer fill:#50E3C2,stroke:#2E8C74,stroke-width:2px
    style Staff fill:#F5A623,stroke:#C87A1A,stroke-width:2px
    style Admin fill:#9013FE,stroke:#6A0DAD,stroke-width:2px
    style Bank fill:#E74C3C,stroke:#C0392B,stroke-width:2px
    style Notify fill:#27AE60,stroke:#1E8449,stroke-width:2px
