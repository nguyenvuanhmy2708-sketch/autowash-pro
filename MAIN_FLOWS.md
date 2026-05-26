# Main Flows - AutoWash Pro System

## 1. Booking Flow

```mermaid
sequenceDiagram
    actor Customer
    participant WebApp as Web/Mobile App
    participant Backend as System Backend
    participant PaymentGW as Payment Gateway
    participant Notification as Notification Service
    
    Customer->>WebApp: 1. Login to system
    WebApp->>Backend: Verify credentials
    Backend-->>WebApp:  Login successful
    
    Customer->>WebApp: 2. Select vehicle & service package
    WebApp->>Backend: Check availability
    Backend-->>WebApp: Show available slots for next 7 days
    
    Customer->>WebApp: 3. Select time slot
    WebApp->>Backend: Validate slot availability
    Backend-->>WebApp: Confirm slot available
    
    Backend->>Backend: 4. Calculate price<br/>(Service + Discount + Loyalty)
    Backend-->>WebApp: Display total price
    
    Customer->>WebApp: 5. Choose payment method
    alt QR Banking
        WebApp->>Backend: Create payment order
        Backend-->>WebApp: Generate QR code
        Customer->>Customer: Scan & pay via bank app
        PaymentGW->>Backend: Confirm payment
        Backend->>Backend: Update payment status to "Paid"
    else Internal Wallet
        WebApp->>Backend: Deduct from wallet
        Backend->>Backend: Update wallet balance
    end
    
    Backend->>Backend: 6. Create booking
    Backend->>Backend: 7. Calculate loyalty points
    Backend->>Backend: 8. Update system queue
    
    Backend->>Notification: Send confirmation
    Notification-->>Customer: SMS/Email: Booking confirmed
    
    Backend-->>WebApp:  Booking successful
    WebApp-->>Customer: Display booking details & invoice
    
    Note over Customer,Notification: Booking Status: CONFIRMED
```

---

## 2. Walk-in Queue Flow

```mermaid
sequenceDiagram
    actor Customer
    participant Staff
    participant System as System Backend
    participant Dashboard as Staff Dashboard
    participant Notification as Notification Service
    
    Customer->>Staff: 1. Arrive at car wash
    
    alt Registered Customer
        Staff->>System: Search customer by phone/license
        System-->>Staff: Display customer info
    else New Customer
        Staff->>System: Create walk-in account
        System-->>Staff: Generate temporary ID
    end
    
    Staff->>System: 2. Check-in vehicle
    System->>System: Record arrival time
    System-->>Staff: Add to queue
    
    System->>System: 3. Calculate estimated wait time
    System-->>Dashboard: Update real-time queue status
    Dashboard-->>Staff: Display queue position
    
    Staff-->>Customer: "Your position: #3, Wait time: ~45 min"
    
    loop Queue Processing
        Staff->>Dashboard: Check next vehicle to wash
        Dashboard-->>Staff: Display "Vehicle #2"
        
        Staff->>System: Update status â†’ "In Progress"
        System->>Notification: Send notification
        Notification-->>Customer: "Your car wash has started"
        
        Staff->>Staff: Wash vehicle
        
        Staff->>System: Update status -> "Completed"
        System->>Notification: Send notification
        Notification-->>Customer: "Your car wash is complete"
        
        Staff->>System: Mark payment status
    end
    
    Customer->>Staff: 4. Collect vehicle
    Staff->>System: Generate invoice
    System-->>Staff: Display total amount
    
    Customer->>Staff: 5. Make payment
    alt QR Payment
        Customer->>Customer: Scan & pay via bank
        Staff->>System: Confirm payment received
    else Wallet Payment
        Staff->>System: Deduct from wallet
        System->>System: Update wallet balance
    end
    
    System->>System: 6. Add loyalty points
    System->>Notification: Send receipt & loyalty update
    Notification-->>Customer: Receipt + Points earned
    
    Note over Customer,Notification: Status: COMPLETED
```

---

## 3. Loyalty Program Flow

```mermaid
sequenceDiagram
    participant Customer
    participant System as System Backend
    participant Admin
    participant Notification as Notification Service
    
    loop For Each Completed Booking
        System->>System: 1. Check booking status = COMPLETED
        System->>System: 2. Calculate loyalty points<br/>(Base points Ã— tier multiplier)
        System->>System: 3. Add points to customer account
        System->>System: 4. Update total loyalty balance
    end
    
    alt Tier Threshold Reached
        System->>System: Check if points tier threshold
        
        System->>System: Upgrade membership tier
        Note over System: Standard -> Member (500 pts)<br/>Member -> VIP (2000 pts)
        
        System->>System: Apply new multiplier
        System->>System: Grant tier benefits
        
        System->>Notification: Create tier upgrade notification
        Notification-->>Customer: " You've reached Member tier!<br/>Enjoy 1.5x loyalty points!"
    end
    
    Customer->>System: 5. View loyalty dashboard
    System-->>Customer: Display:<br/>- Current points<br/>- Current tier<br/>- Points to next tier<br/>- Transaction history
    
    Customer->>System: 6. Redeem loyalty discount
    System->>System: Validate sufficient points
    Note over System: 100 points = 50,000 VND discount
    
    Customer->>System: 7. Apply discount to booking
    System->>System: Deduct points from balance
    System->>System: Calculate new booking total
    System-->>Customer: Updated price with discount
    
    Customer->>System: 8. Complete booking
    System->>System: Process payment
    System->>System: Record loyalty transaction
    
    System->>Notification: Send confirmation
    Notification-->>Customer: Booking receipt with points status
    
    Note over System: Loyalty Points Cycle Complete
```

---

## 4. Peak Hour Slot Allocation Flow

```mermaid
sequenceDiagram
    participant Customer
    participant System as System Backend
    participant Admin
    
    Admin->>System: 1. Define peak hours
    Note over System: E.g., 10 AM-12 PM, 2 PM-4 PM
    System->>System: Store peak hour configuration
    
    Admin->>System: 2. Configure slot allocation
    Note over System: Member: 60% of slots<br/>VIP: 40% of slots
    System->>System: Reserve slots by tier
    
    loop During Peak Hours
        Customer->>System: 3. View available slots
        System->>System: Check customer membership tier
        
        alt VIP Member
            System-->>Customer: Show 40% reserved slots for VIP
            Customer->>System: 4a. Book VIP slot (Priority)
            System->>System: Reserve slot immediately
        else Member
            System-->>Customer: Show 60% available slots for Member
            Customer->>System: 4b. Book Member slot
            System->>System: Check slot availability
            alt Slot Available
                System->>System: Reserve slot
                System-->>Customer:  Booking confirmed
            else Slot Full
                System-->>Customer:  No slots available
                Note over Customer: Suggest off-peak or waitlist
            end
        else Standard/Non-member
            System-->>Customer:  Peak hours not available
            Note over Customer: Upgrade to Member tier
        end
    end
    
    Admin->>System: 5. Monitor slot utilization
    System-->>Admin: Display:<br/>- Slots used by tier<br/>- Demand vs capacity<br/>- Peak hour analytics
```

---

## 5. Payment & Refund Flow

```mermaid
sequenceDiagram
    actor Customer
    participant System as System Backend
    participant Bank as Banking App
    participant Notification as Notification Service
    
    Customer->>System: 1. Select payment method
    
    alt QR Banking Payment
        System->>System: Generate QR code
        System-->>Customer: Display QR
        
        Customer->>Bank: Scan & authorize payment
        Bank->>System: Send payment confirmation
        System->>System: Update status -> "PAID"
        System-->>Notification: Send receipt
    else Internal Wallet Payment
        System->>System: Check wallet balance
        alt Sufficient Balance
            System->>System: Deduct amount from wallet
            System->>System: Update wallet balance
            System->>System: Record transaction
        else Insufficient Balance
            System-->>Customer: Insufficient wallet balance
            Customer->>System: Proceed with QR payment (fallback)
        end
    end
    
    Notification-->>Customer: Payment receipt
    System->>System: 2. Create booking
    System->>System: 3. Reserve time slot
    
    alt Customer Cancels Booking
        Customer->>System: 4. Request cancellation
        System->>System: Check cancellation timing
        
        alt > 2 hours before booking
            System->>System: Full refund (100%)
        else < 2 hours before booking
            System->>System: Partial refund (50%)
        end
        
        System->>System: Calculate refund amount
        System->>System: Create refund transaction
        
        alt Original Payment: QR Banking
            System->>Bank: Process refund
            Bank->>Customer: Refund to bank account (24h)
        else Original Payment: Wallet
            System->>System: Add refund to wallet
            System-->>Customer: Wallet updated (Instant)
        end
        
        System->>Notification: Send refund confirmation
        Notification-->>Customer: Refund details & status
        System->>System: Mark booking â†’ "CANCELLED"
        System->>System: Release time slot
    end
    
    Note over System: Payment & Refund Complete
```

---

## 6. Service Change Flow (On-Site)

```mermaid
sequenceDiagram
    actor Customer
    participant Staff
    participant System as System Backend
    participant Notification as Notification Service
    
    Customer->>Staff: 1. Request service change on-site
    Note over Customer,Staff: (e.g., upgrade from Basic to Premium)
    
    Staff->>System: 2. Retrieve booking
    System-->>Staff: Display current booking details
    
    Staff->>System: 3. Change service package
    System->>System: 4. Calculate price difference
    Note over System: Original: 200,000 VND<br/>New: 350,000 VND<br/>Difference: +150,000 VND
    
    System-->>Staff: Display new total
    Staff-->>Customer: "Additional charge: 150,000 VND"
    
    Customer->>Staff: 5. Confirm & pay
    
    alt QR Payment
        Customer->>Customer: Scan & pay via bank
        Staff->>System: Confirm payment
    else Wallet Payment
        Staff->>System: Deduct from wallet
        System->>System: Verify sufficient balance
    end
    
    System->>System: 6. Update booking
    System->>System: Update invoice
    
    System->>Notification: Notify staff of service change
    Notification-->>Staff: "Service updated: Basic -> Premium"
    
    Staff->>System: 7. Begin car wash
    System->>System: Record service start time
    
    Note over Staff,System: Proceed with new service package
```

---

## Flow Statistics Summary

| Flow | Participants | Key Decision Points | Average Duration |
|------|--------------|-------------------|------------------|
| **Booking** | Customer -> System -> Payment | Slot availability, Payment method | 5-10 minutes |
| **Walk-in** | Staff -> System -> Customer | Customer status, Payment method | 15-60 minutes |
| **Loyalty** | System -> Customer | Tier threshold, Redemption | Ongoing |
| **Peak Hour Allocation** | Admin -> System -> Customer | Membership tier, Time | Real-time |
| **Payment & Refund** | System -> Bank/Wallet | Payment method, Refund policy | 24 hours max |
| **Service Change** | Staff -> System -> Customer | New package, Price difference | 2-5 minutes |

