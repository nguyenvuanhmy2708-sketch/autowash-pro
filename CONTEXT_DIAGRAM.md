# Context Diagram - AutoWash Pro System

## System Context Overview

```mermaid
graph TB
    subgraph "External Actors"
        Customer["ðŸ‘¤ Customer"]
        Staff["ðŸ‘· Staff"]
        Admin["âš™ï¸ Admin"]
        Bank["ðŸ¦ Banking App"]
        Notify["ðŸ“¢ Notification Service"]
    end
    
    subgraph "AutoWash Pro System"
        System["ðŸš— Smart Automated Car Wash<br/>Management System"]
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
```

---

## Key Actors and Their Responsibilities

### 1. **Customer**
- Registers and logs in
- Manages vehicle information
- Books car wash services
- Selects service packages and time slots
- Makes payments via QR Banking or internal wallet
- Tracks queue status in real-time
- Views booking history and invoices
- Accumulates and redeems loyalty points
- Rates services and provides feedback

### 2. **Staff**
- Checks in walk-in customers
- Manages the real-time queue
- Updates car wash status
- Confirms QR Banking payments
- Manages service changes on-site
- Accesses operations dashboard
- Tracks vehicle progress

### 3. **Admin**
- Configures system parameters (peak hours, slots, pricing)
- Manages loyalty program settings
- Creates and manages promotional campaigns
- Views and analyzes business metrics
- Tracks refunds and payment issues
- Manages customer tier system

### 4. **Banking App**
- Processes QR Banking payments
- Sends payment confirmation/failure status
- Handles refunds and chargebacks

### 5. **Notification Service**
- Sends booking confirmations
- Sends queue status updates
- Sends service completion notifications
- Sends loyalty tier upgrade notifications
- Sends promotional alerts

---

## System Boundaries

### **In Scope:**
 Customer registration and authentication  
 Vehicle management  
 Advance booking with slot management  
 Real-time queue management  
 Payment processing (QR Banking & Internal Wallet)  
 Loyalty program and membership tiers  
 Promotion management  
 Operations dashboard for staff  
 Business analytics and reporting  
 Notification system  
 Service quality rating system  

### **Out of Scope:**
 Physical car wash equipment control  
 Multi-location support (single location only)  
 Direct banking integration (only QR code)  
 Inventory management for supplies  
 Employee payroll or HR management  

---

## Data Flow Summary

### Information Flows:
1. **Booking Flow** â†’ Customer â†’ System â†’ Staff â†’ Notification Service
2. **Payment Flow** â†’ Customer â†’ System â†’ Banking App â†’ System â†’ Confirmation
3. **Loyalty Flow** â†’ System â†’ Customer (Points) + Admin (Tier Management)
4. **Analytics Flow** â†’ System â†’ Admin (Reports & Dashboard)
5. **Queue Flow** â†’ Staff â†’ System â†’ Customer (Real-time Updates)

