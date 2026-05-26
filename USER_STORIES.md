# User Stories - Smart Automated Car Wash Management System with Advance Booking & Loyalty Program

## **1. User Story - Customer Account Management**

### US-001: Customer Registration
**As a** customer  
**I want to** register for an account with email and password  
**So that** I can access the car wash booking system

**Acceptance Criteria:**
- Customer can create account with email, password, phone number, and name
- System validates email format and password strength
- Confirmation email is sent to verify email address
- System prevents duplicate email registration

### US-002: Customer Login
**As a** customer  
**I want to** log in to my account  
**So that** I can access my bookings and loyalty information

**Acceptance Criteria:**
- Customer can login with email and password
- System displays "Forgot Password" option
- Session timeout after 30 minutes of inactivity
- Login history is tracked

### US-003: Manage Customer Profile
**As a** customer  
**I want to** update my personal information  
**So that** my profile is always current

**Acceptance Criteria:**
- Customer can update name, phone number, and email
- Customer can add/update profile picture
- System validates phone number format
- Changes are saved immediately

---

## **2. User Story - Vehicle Management**

### US-004: Add Vehicle
**As a** customer  
**I want to** register my vehicle details  
**So that** I can book services for my vehicle

**Acceptance Criteria:**
- Customer can add vehicle with license plate, type (car 4-7 seat, motorcycle), brand, model, and color
- System validates license plate format
- Customer can add multiple vehicles
- Vehicle is saved with unique identifier

### US-005: View Vehicle History
**As a** customer  
**I want to** view service history of each vehicle  
**So that** I can track maintenance and service dates

**Acceptance Criteria:**
- Customer can view past bookings and services for each vehicle
- History shows service date, type, cost, and status
- System displays latest service first
- Customer can filter by date range

### US-006: Remove Vehicle
**As a** customer  
**I want to** delete a vehicle from my account  
**So that** I only have active vehicles listed

**Acceptance Criteria:**
- Customer can remove vehicle from profile
- System confirms deletion with warning
- Vehicle history is preserved
- Booking history remains accessible

---

## **3. User Story - Booking Management**

### US-007: View Available Time Slots
**As a** customer  
**I want to** view available booking slots  
**So that** I can choose a convenient time for my car wash

**Acceptance Criteria:**
- System displays available slots for next 7 days
- Slots are organized by hour
- System shows real-time availability status
- Estimated wait time is displayed
- Different slots for peak hours vs. off-peak hours

### US-008: Book Car Wash Service
**As a** customer  
**I want to** book a car wash service at a selected time slot  
**So that** I can guarantee my car wash appointment

**Acceptance Criteria:**
- Customer must be logged in to make booking
- Customer can select vehicle, service package, and time slot
- System checks:
  - Slot availability
  - Member tier priority rules
  - Daily booking limit per customer
- Booking confirmation is displayed
- Confirmation notification is sent via email/SMS

### US-009: Modify Service Package After Booking
**As a** customer  
**I want to** change my service package after booking  
**So that** I can upgrade or downgrade my service

**Acceptance Criteria:**
- Customer can modify service package before 24 hours of booking
- System calculates price difference or refund
- Customer can pay additional amount or receive refund
- Staff is notified of service change
- Updated invoice is generated

### US-010: Cancel Booking
**As a** customer  
**I want to** cancel my booking  
**So that** I can free up my slot if my plans change

**Acceptance Criteria:**
- Customer can cancel booking up to 2 hours before appointment
- Full refund is applied for cancellations > 2 hours
- 50% refund for cancellations < 2 hours
- Cancellation confirmation is sent
- Booking slot becomes available for others

### US-011: Multiple Vehicle Booking
**As a** customer  
**I want to** book multiple vehicles in one booking  
**So that** I can wash multiple cars in one visit

**Acceptance Criteria:**
- Customer can select multiple vehicles for one booking
- System calculates total price for all vehicles
- Customer can cancel individual vehicles from booking
- Partial refund is calculated if one vehicle is removed
- Invoice itemizes each vehicle separately

### US-012: View Booking History
**As a** customer  
**I want to** view my past and upcoming bookings  
**So that** I can track my car wash appointments

**Acceptance Criteria:**
- Customer can view all bookings with status (Pending, Confirmed, Completed, Cancelled)
- Bookings are sorted by date (newest first)
- Customer can filter by status or vehicle
- Each booking shows date, time, vehicle, service, and cost
- Customer can access booking details and invoice

---

## **4. User Story - Queue Management**

### US-013: Real-time Queue Tracking
**As a** customer  
**I want to** view my position in the queue and estimated wait time  
**So that** I know when my car wash will be completed

**Acceptance Criteria:**
- Customer can see current queue position on mobile app
- System displays estimated wait time in minutes
- Real-time updates when queue moves
- Notification sent when car wash starts
- Notification sent when car wash is completed

### US-014: Walk-in Check-in
**As a** staff member  
**I want to** check in walk-in customers  
**So that** they are added to the queue system

**Acceptance Criteria:**
- Staff can search customer by name, phone, or license plate
- Staff can create new walk-in booking for unregistered customer
- System adds walk-in to queue with timestamp
- Estimated completion time is calculated
- Queue position is displayed to customer

### US-015: Update Washing Status
**As a** staff member  
**I want to** update the status of car wash in progress  
**So that** customers know their car wash progress

**Acceptance Criteria:**
- Staff can mark car wash as "In Progress", "Completed", or "Issue"
- Status updates are reflected in real-time
- Customer receives notification when status changes
- System tracks time spent on each vehicle
- Completion time is recorded for analytics

---

## **5. User Story - Payment Management**

### US-016: QR Banking Payment
**As a** customer  
**I want to** pay using QR code banking  
**So that** I can make quick and secure payments

**Acceptance Criteria:**
- System displays QR code for payment at checkout
- QR code contains payment amount, recipient, and order ID
- System waits for payment confirmation from bank
- Payment status updates in real-time (Pending â†’ Paid)
- Transaction ID and receipt are generated
- Payment failure is handled with retry option

### US-017: Internal Wallet Management
**As a** customer  
**I want to** load money into my internal wallet  
**So that** I can make quick payments without QR code scanning

**Acceptance Criteria:**
- Customer can load wallet using QR Banking
- Minimum top-up amount is 50,000 VND
- Maximum wallet balance is 50,000,000 VND
- System displays current wallet balance
- Transaction history shows all top-ups and payments
- Wallet balance is deducted when customer completes booking

### US-018: Pay with Internal Wallet
**As a** customer  
**I want to** pay for my car wash using my wallet balance  
**So that** I can make instant payment

**Acceptance Criteria:**
- Customer can select wallet as payment method at checkout
- System verifies sufficient balance
- Payment is deducted immediately from wallet
- Payment receipt is generated
- Wallet balance updates in real-time

### US-019: View Payment History and Invoices
**As a** customer  
**I want to** view all my payment transactions and invoices  
**So that** I can track my spending and have records

**Acceptance Criteria:**
- Customer can view all payment history with date, amount, method, and status
- System displays invoice details (itemized services, discounts, total)
- Customer can download/print invoice as PDF
- Invoices can be filtered by date range
- Payment receipt can be resent via email

### US-020: Refund Processing
**As a** customer  
**I want to** receive refunds when applicable  
**So that** I get my money back for cancelled or failed services

**Acceptance Criteria:**
- System calculates refund amount based on cancellation policy
- Refund is processed to original payment method within 24 hours
- Customer receives refund confirmation notification
- Refund status can be tracked in transaction history
- Refund reason is documented in system

---

## **6. User Story - Loyalty Program**

### US-021: Earn Loyalty Points
**As a** customer  
**I want to** earn loyalty points for each completed booking  
**So that** I can redeem them for rewards or discounts

**Acceptance Criteria:**
- Loyalty points are calculated after booking completion (not immediately)
- Base points = 10 points per 100,000 VND spent
- Points multiplier varies by membership tier (Standard 1x, Member 1.5x, VIP 2x)
- Customer can view earned points in loyalty dashboard
- Points are deducted when used for discount

### US-022: View Loyalty Dashboard
**As a** customer  
**I want to** view my loyalty points, membership tier, and rewards  
**So that** I can understand my benefits and progress

**Acceptance Criteria:**
- Dashboard shows current loyalty points balance
- Current membership tier is displayed with benefits
- Progress to next tier is shown (e.g., "100 points until VIP")
- Transaction history shows all loyalty activities
- Available rewards are listed with point requirements

### US-023: Automatic Tier Upgrade
**As a** customer  
**I want to** automatically advance to higher membership tiers  
**So that** I receive better benefits as I spend more

**Acceptance Criteria:**
- Standard tier: 0 points (default)
- Member tier: 500 points, includes 1.5x loyalty multiplier
- VIP tier: 2,000 points, includes 2x loyalty multiplier, priority booking
- System automatically upgrades when threshold is reached
- Customer receives notification of tier upgrade
- Benefits are applied immediately upon upgrade

### US-024: Use Loyalty Discount
**As a** customer  
**I want to** apply my loyalty points as discount for booking  
**So that** I can use rewards to reduce service cost

**Acceptance Criteria:**
- Customer can enter loyalty discount code at checkout
- 100 points = 50,000 VND discount
- System verifies customer has sufficient points
- Discount is applied to total before final payment
- Points are deducted after payment confirmation
- New loyalty balance is displayed

### US-025: Priority Booking for VIP Members
**As a** VIP member  
**I want to** have priority access to peak-hour time slots  
**So that** I can book during high-demand times

**Acceptance Criteria:**
- VIP members can access 40% of peak-hour slots
- Regular members can access remaining 60% of peak-hour slots
- VIP slots are reserved and released 2 hours before regular slot release
- System prevents overbooking of VIP slots
- Non-VIP customers receive error message if VIP slot is full

---

## **7. User Story - Promotion Management**

### US-026: Create and Manage Promotions
**As an** admin  
**I want to** create and manage promotional campaigns  
**So that** I can attract and retain customers

**Acceptance Criteria:**
- Admin can create promotion with discount percentage or fixed amount
- Promotion can be limited by:
  - Date range (start/end date)
  - Customer tier (Standard/Member/VIP only)
  - Maximum number of uses
  - Service package type
- Promotion code is auto-generated
- System prevents duplicate promotion codes
- Promotions can be enabled/disabled

### US-027: Apply Promotion Code
**As a** customer  
**I want to** apply a promotion code to my booking  
**So that** I can get a discount

**Acceptance Criteria:**
- Customer can enter promotion code at checkout
- System validates:
  - Code exists and is active
  - Customer meets eligibility criteria (tier, date, etc.)
  - Maximum uses not exceeded
- Discount is calculated and applied to total
- Code validity period is checked
- Error message displayed if code is invalid

---

## **8. User Story - Operations Dashboard (Staff)**

### US-028: Real-time Operations Dashboard
**As a** staff member  
**I want to** view real-time operations dashboard  
**So that** I can monitor queue and manage workflow

**Acceptance Criteria:**
- Dashboard shows current queue status (how many vehicles waiting)
- Active bookings in progress are displayed
- Next 5 upcoming bookings are listed
- Estimated completion times are shown
- Staff can mark vehicles as completed
- System updates dashboard in real-time (refresh every 10 seconds)

### US-029: Confirm QR Payment
**As a** staff member  
**I want to** verify and confirm QR banking payments  
**So that** I can ensure payment was received

**Acceptance Criteria:**
- Staff can view pending payments on dashboard
- Staff can see payment QR code and amount
- System confirms payment status from bank integration
- Staff marks payment as confirmed
- Booking status updates to "Confirmed" after payment confirmation
- Error notification if payment fails

### US-030: Update Service Package On-Site
**As a** staff member  
**I want to** change a customer's service package on-site  
**So that** I can accommodate customer requests during service

**Acceptance Criteria:**
- Staff can select booking from queue
- Staff can upgrade/downgrade service package
- System calculates price difference
- Customer is charged/refunded the difference
- Payment is processed before service begins
- Updated invoice is generated

---

## **9. User Story - Analytics and Reporting (Admin)**

### US-031: Revenue Dashboard and Reports
**As an** admin  
**I want to** view revenue and business analytics  
**So that** I can make data-driven business decisions

**Acceptance Criteria:**
- Dashboard shows:
  - Total revenue (today, this week, this month)
  - Number of bookings (completed, pending, cancelled)
  - Average service duration
  - Peak hour analysis
  - Revenue by service package type
- Data can be filtered by date range
- Reports can be exported as CSV/PDF
- Charts and graphs for visualization

### US-032: Customer Analytics
**As an** admin  
**I want to** analyze customer behavior and loyalty patterns  
**So that** I can improve loyalty program and marketing

**Acceptance Criteria:**
- Reports show:
  - New customers (last 7 days, 30 days)
  - Repeat customers and booking frequency
  - Customer retention rate
  - Average spending per customer
  - Loyalty tier distribution
- Data can be segmented by tier and vehicle type
- Identify inactive customers (no booking in 30 days)
- Export customer list for marketing campaigns

### US-033: Refund and Payment Analytics
**As an** admin  
**I want to** track refund trends and payment issues  
**So that** I can identify operational problems

**Acceptance Criteria:**
- Dashboard shows:
  - Total refunds and refund reasons breakdown
  - Failed payment transactions
  - Payment method distribution
  - Average transaction amount
  - Chargeback rate
- Reports can be filtered by date range and payment method
- Alerts for unusual refund patterns
- Export detailed transaction logs

---

## **10. User Story - Notification System**

### US-034: Booking Confirmation Notification
**As a** customer  
**I want to** receive confirmation of my booking  
**So that** I have proof of my appointment

**Acceptance Criteria:**
- Notification sent immediately after successful booking
- Contains: booking ID, date, time, vehicle, service, total cost
- Sent via SMS and email
- Notification includes cancellation policy
- Customer can view/resend notification anytime

### US-035: Queue Status Notifications
**As a** customer  
**I want to** receive notifications about my queue status  
**So that** I know when my car wash will start and be completed

**Acceptance Criteria:**
- Notification when car wash service starts
- Notification when car wash is completed
- Notification 15 minutes before booking time (reminder)
- Customer can opt-out of notifications
- Push notification if app is installed

### US-036: Cancellation Confirmation Notification
**As a** customer  
**I want to** receive confirmation when I cancel my booking  
**So that** I have record of cancellation and refund

**Acceptance Criteria:**
- Notification sent immediately after cancellation
- Contains: booking ID, cancellation date/time, refund amount
- Refund processing timeframe is stated
- Customer can view cancellation details anytime

### US-037: Tier Upgrade Notification
**As a** customer  
**I want to** be notified when I advance to a higher membership tier  
**So that** I understand my new benefits

**Acceptance Criteria:**
- Notification sent automatically when tier threshold is reached
- Contains: new tier name, benefits, and bonus points (if applicable)
- Sent via email and push notification
- Customer can view tier benefits on dashboard

---

## **11. User Story - System Configuration (Admin)**

### US-038: Configure Peak Hour Rules
**As an** admin  
**I want to** configure peak hour time slots and capacity rules  
**So that** I can manage customer flow during busy times

**Acceptance Criteria:**
- Admin can define peak hours (e.g., 10 AM - 12 PM, 2 PM - 4 PM)
- Admin can set slot allocation:
  - 60% for Member tier
  - 40% for VIP tier
- Admin can set maximum bookings per day per customer
- Admin can set queue capacity threshold
- Rules take effect immediately

### US-039: Configure Service Packages
**As an** admin  
**I want to** create and manage service packages  
**So that** I can offer different service options

**Acceptance Criteria:**
- Admin can create package with name, description, price, and duration
- Service packages include: Basic, Standard, Premium, Deluxe
- Admin can set package availability by vehicle type
- Admin can modify package price and duration
- Admin can enable/disable packages
- Package changes apply to new bookings only

### US-040: Configure Loyalty Program
**As an** admin  
**I want to** configure loyalty program parameters  
**So that** I can adjust loyalty rules as needed

**Acceptance Criteria:**
- Admin can set:
  - Tier thresholds (Member: 500 pts, VIP: 2,000 pts)
  - Loyalty multipliers per tier (Standard 1x, Member 1.5x, VIP 2x)
  - Points calculation rate (base: 10 pts per 100K VND)
  - Tier expiration policy (if applicable)
- Changes take effect for new transactions
- Admin can manually adjust customer loyalty points if needed
- Audit log tracks all configuration changes

---

## **12. User Story - Rating and Feedback**

### US-041: Rate Service Quality
**As a** customer  
**I want to** rate my car wash service experience  
**So that** I can provide feedback and help improve service quality

**Acceptance Criteria:**
- Customer can rate service 1-5 stars after booking completion
- Customer can write text comment (optional, max 500 chars)
- Customer can rate specific aspects: cleanliness, staff friendliness, time efficiency
- Rating can be submitted within 7 days of service completion
- Ratings are anonymous (staff cannot see customer name)
- Customer can edit rating within 24 hours of submission

### US-042: View Service Feedback
**As an** admin  
**I want to** view customer feedback and ratings  
**So that** I can identify service improvement areas

**Acceptance Criteria:**
- Admin can view all ratings and comments
- Dashboard shows:
  - Average rating (overall, by package, by date range)
  - Comments sorted by date (newest first)
  - Low ratings (< 3 stars) highlighted
- Admin can filter by rating range or date
- Trend analysis shows rating changes over time
- Export feedback reports for analysis

---

## **Priority and Dependencies**

### Phase 1 (MVP - Core Features)
- US-001 to US-003 (Customer Account)
- US-004 to US-006 (Vehicle Management)
- US-007 to US-010 (Basic Booking)
- US-016 to US-018 (Payment)
- US-034 (Booking Confirmation)

### Phase 2 (Queue & Operations)
- US-013 to US-015 (Queue Management)
- US-028 to US-030 (Staff Dashboard)
- US-035 to US-036 (Notifications)

### Phase 3 (Loyalty & Promotions)
- US-021 to US-025 (Loyalty Program)
- US-026 to US-027 (Promotions)
- US-037 (Tier Upgrade Notifications)

### Phase 4 (Advanced Features)
- US-011 (Multiple Vehicle Booking)
- US-031 to US-033 (Analytics)
- US-038 to US-040 (Admin Configuration)
- US-041 to US-042 (Ratings & Feedback)
- US-019, US-020 (Payment History & Refunds)

---

**Document Version:** 1.0  
**Last Updated:** 2024  
**Status:** Ready for Development
