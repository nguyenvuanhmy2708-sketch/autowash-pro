# AutoWash Pro - Smart Automated Car Wash Management System

## 📚 Documentation Index

This repository contains the complete specification and design documentation for the AutoWash Pro system.

### Core Documentation Files

#### 1. **USER_STORIES.md** - User Stories & Features
   - 42 comprehensive user stories organized by functional category
   - Acceptance criteria for each story
   - Priority levels and phase breakdown
   - **Categories**: Account Management, Vehicle Management, Booking, Queue, Payment, Loyalty, Promotions, Operations, Analytics, Configuration, Feedback

#### 2. **CONTEXT_DIAGRAM.md** - System Context
   - High-level system architecture
   - External actors and their roles
   - System boundaries and scope
   - Data flow overview
   - **Actors**: Customer, Staff, Admin, Banking App

#### 3. **MAIN_FLOWS.md** - Process Flows & Sequence Diagrams
   - **Booking Flow**: Customer registration → booking → payment → confirmation
   - **Walk-in Queue Flow**: Check-in → queuing → service → payment
   - **Loyalty Program Flow**: Points calculation → tier upgrade → redemption
   - **Peak Hour Slot Allocation**: Tier-based slot management
   - **Payment & Refund Flow**: Payment processing and refund policies
   - **Service Change Flow**: On-site service modifications

---

## 🎯 System Overview

**AutoWash Pro** is a comprehensive digital solution for managing modern car wash operations with features including:

✅ **Online Booking System** - Customers can book services in advance with available slot visibility   
✅ **Loyalty Program** - Automatic tier-based rewards (Standard → Member → VIP)  
✅ **Smart Payment System** - QR Banking + Internal Wallet integration  
✅ **Peak Hour Management** - Intelligent slot allocation by membership tier  
✅ **Operations Dashboard** - Real-time staff dashboard for queue and service management  
✅ **Business Analytics** - Revenue, customer, and refund analytics for decision-making  
✅ **Rating & Feedback** - Service quality tracking and improvement insights  

---

## 👥 Key Stakeholders

| Role | Responsibilities | System Access |
|------|------------------|---------------|
| **Customer** | Book services, make payments, track loyalty | Mobile/Web App |
| **Staff** | Check-in customers, update service status, confirm payments | Staff Dashboard |
| **Admin** | System configuration, promotions, analytics | Admin Portal |
| **Banking API** | Process QR code payments, send confirmations | API Integration |
| **Notification Service** | Send SMS/Email/Push notifications | Message Queue |

---

## 🔄 Main Business Processes

### 1️⃣ **Booking Process**
   - Customer selects vehicle → service package → time slot
   - System validates slot availability and membership tier rules
   - Payment processed (QR Banking or Wallet)
   - Loyalty points calculated
   - Confirmation sent via notification service

### 2️⃣ **Queue Management**
   - Walk-in customers checked in by staff
   - Real-time queue position updates
   - Estimated completion time calculated
   - Status notifications sent throughout the process

### 3️⃣ **Loyalty Rewards**
   - Points earned on service completion (Base: 10 pts per 100K VND)
   - Tier multipliers applied (Standard 1x, Member 1.5x, VIP 2x)
   - Automatic tier upgrades at thresholds (Member: 500pts, VIP: 2000pts)
   - Priority booking access for VIP members

### 4️⃣ **Payment Handling**
   - Flexible payment options: QR Banking or Internal Wallet
   - Automatic refunds based on cancellation timing
   - Transaction audit trail maintained
   - Payment analytics for business intelligence

---

## 📊 Feature Statistics

| Category | Count | Examples |
|----------|-------|----------|
| **User Stories** | 42 | Booking, Payment, Loyalty, Analytics |
| **GitHub Issues** | 42 | Tracked in GitHub Issues board |
| **Main Flows** | 6 | Booking, Walk-in, Loyalty, Peak Hours, Payment, Service Change |
| **External Actors** | 5 | Customer, Staff, Admin, Bank, Notification |
| **Supported Vehicles** | 2 | Cars (4-7 seat), Motorcycles |
| **Membership Tiers** | 3 | Standard, Member, VIP |
| **Service Packages** | 4+ | Basic, Standard, Premium, Deluxe |

---

## 🚀 Implementation Phases

### **Phase 1 (MVP - Core Features)** - Weeks 1-4
- Account management & authentication
- Vehicle management
- Basic booking system
- Payment integration (QR Banking)
- Notification system

### **Phase 2 (Queue & Operations)** - Weeks 5-8
- Real-time queue management
- Staff operations dashboard
- Service status tracking
- Queue notifications

### **Phase 3 (Loyalty & Promotions)** - Weeks 9-12
- Loyalty points system
- Tier management
- Promotion management
- Loyalty notifications

### **Phase 4 (Advanced Features)** - Weeks 13-16
- Multiple vehicle booking
- Business analytics
- Advanced admin configuration
- Rating & feedback system
- Refund analytics

---

## 📋 How to Use This Documentation

1. **Start with User Stories** (USER_STORIES.md)
   - Understand all features and requirements
   - Review acceptance criteria for development guidance
   - Check phase breakdown for release planning

2. **Review Context Diagram** (CONTEXT_DIAGRAM.md)
   - Understand system architecture
   - Identify external integrations
   - Define system boundaries

3. **Study Main Flows** (MAIN_FLOWS.md)
   - Follow detailed sequence diagrams
   - Understand decision points and logic
   - Identify edge cases and error handling

---

## 🔗 Quick Links

- **GitHub Issues**: https://github.com/nguyenvuanhmy2708-sketch/autowash-pro/issues
- **Repository**: https://github.com/nguyenvuanhmy2708-sketch/autowash-pro
- **User Stories File**: USER_STORIES.md
- **Context Diagram**: CONTEXT_DIAGRAM.md
- **Main Flows & Sequences**: MAIN_FLOWS.md

---

## 📝 Document Version Info

- **Created**: May 26, 2026
- **Status**: Ready for Development
- **Total User Stories**: 42
- **Total GitHub Issues**: 42
- **Main Flows Documented**: 6
- **External Integrations**: 2 (Banking, Notifications)

---

## 🎓 Architecture Notes

### Technology Considerations
- **Frontend**: React/Vue.js with real-time queue updates (WebSocket/Socket.io)
- **Backend**: Node.js/Python with REST API
- **Database**: PostgreSQL for relational data + Redis for caching/queue
- **Payment**: QR Code integration via banking API
- **Notifications**: SMS/Email service + Push notifications (Firebase/OneSignal)
- **Analytics**: Real-time dashboards (Grafana/Kibana)

### Security Considerations
- JWT-based authentication
- Role-based access control (RBAC)
- Payment PCI-DSS compliance
- Data encryption at rest and in transit
- Audit logging for all critical operations

---

**Last Updated**: May 26, 2026  
**Document Status**: Complete & Ready for Development
