# 🚀 INDIXA - Hyperlocal Super App

**Complete production-ready Indian Super App platform** connecting Users, Partners, and Admins through a single Firebase backend.

## 📱 Project Overview

INDIXA is a comprehensive hyperlocal super app that provides 50+ services from **village to country level**:

### Services Offered
- 🚗 **Mobility**: Cab, Auto, Bike, Bus, Flight, Tempo
- 🍔 **Food**: Restaurants, Food Delivery, Cloud Kitchen
- 🛒 **Retail**: Grocery, Vegetables, Clothing, Hardware, Electronics, Marketplace
- 💊 **Healthcare**: Pharmacy, Medicine, Doctors, Labs
- 💍 **Luxury**: Jewelry, Watches, Accessories
- 🏠 **Services**: Electrician, Plumber, Carpenter, Painter, Beauty, Laundry
- 🏨 **Travel**: Hotels, Holiday Packages, Homestay
- 💰 **Finance**: Wallet, Bills, Insurance
- 📱 **Utilities**: Mobile Recharge, DTH, Bills
- 🎓 **Education**: Tuitions, Coaching, Courses
- And **30+ more services**...

## 🏗️ Project Structure

```
indixa-superapp/
├── admin-panel/          # React.js Admin Dashboard
├── user-app/            # Flutter User Application
├── partner-app/         # Flutter Partner Application
├── backend/             # Firebase Config & Cloud Functions
├── docs/                # Documentation
└── README.md            # This file
```

## 🔐 Technology Stack

### Frontend
- **User App**: Flutter (Android/iOS)
- **Partner App**: Flutter (Android/iOS)
- **Admin Panel**: React.js + Ant Design

### Backend
- **Database**: Firebase Firestore
- **Authentication**: Firebase Auth
- **Serverless**: Firebase Cloud Functions
- **Storage**: Firebase Storage
- **Messaging**: Firebase Cloud Messaging (FCM)
- **Analytics**: Firebase Analytics

### Integrations
- 💳 **Razorpay**: Payment Gateway
- 🗺️ **MapMyIndia**: Maps & Navigation
- 🤖 **Gemini AI**: AI Assistant
- 📧 **Twilio/SendGrid**: SMS & Email

## 🎯 Key Features

✅ **Geographical Hierarchy**
- Country → States → Districts → Cities → Areas → Zones → Localities
- Complete control over service availability per location

✅ **Role-Based Access Control (RBAC)**
- Super Admin, Admin, Manager, Finance, Support, Operations, Marketing
- Partners see only their relevant services
- Users see only available services in their area

✅ **Multi-Service Platform**
- 50+ services integrated seamlessly
- Real-time order tracking
- Dynamic pricing and surge pricing
- Intelligent matching algorithm

✅ **Admin Control Panel**
- User management (block, unblock, verify)
- Partner management (approve, reject, suspend)
- KYC verification
- Real-time analytics and reports
- Promotion & offer management
- Payment settlement
- System monitoring

✅ **Partner App**
- Role-specific modules
- Online/Offline toggle
- Real-time booking requests
- Earnings tracking
- Settlement management
- Rating & reviews

✅ **User App**
- Universal search (voice, text, AI)
- Service browsing
- Real-time tracking
- Multiple payment methods
- Wallet management
- Order history
- AI assistant

✅ **Security**
- Firebase Security Rules (RBAC)
- JWT token validation
- Secure storage
- Device integrity checks
- OWASP best practices

✅ **Performance**
- Offline caching
- Image optimization
- API retry mechanism
- Low battery usage
- Smooth animations

✅ **Google Play Ready**
- Privacy Policy
- Terms & Conditions
- Data Safety
- Runtime Permissions
- Background Location Compliance
- Crash-free build

## 📊 Firebase Backend Structure

```
Firestore Collections:

/users/{userId}                    - User profiles
/partners/{partnerId}              - Partner profiles
/admins/{adminId}                  - Admin accounts
/locations/{hierarchy}             - Geographical data
/services/{serviceId}              - Service definitions
/orders/{orderId}                  - Order management
/payments/{paymentId}              - Payment records
/wallet/{userId}                   - Wallet data
/promotions/{promotionId}          - Offers & coupons
/notifications/{userId}/{notifId}  - Notifications
/analytics/                        - Analytics data
```

## 🚀 Getting Started

### Prerequisites
- Flutter SDK (3.0+)
- Node.js (16+)
- npm/yarn
- Firebase CLI
- Android Studio / Xcode

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/pathanji/indixa-superapp.git
   cd indixa-superapp
   ```

2. **Setup Firebase**
   ```bash
   cd backend
   npm install
   firebase init
   firebase deploy
   ```

3. **Setup Admin Panel**
   ```bash
   cd admin-panel
   npm install
   npm start
   ```

4. **Setup User App**
   ```bash
   cd user-app
   flutter pub get
   flutter run
   ```

5. **Setup Partner App**
   ```bash
   cd partner-app
   flutter pub get
   flutter run
   ```

## 📚 Documentation

Detailed documentation available in `/docs` folder:
- Architecture Overview
- Database Schema
- API Reference
- Security Rules
- Deployment Guide
- Contributing Guidelines

## 🤝 Contributing

Contributions are welcome! Please follow the guidelines in CONTRIBUTING.md

## 📄 License

Proprietary - All rights reserved

## 📞 Support

For support, email: support@indixa.app

---

**Made with ❤️ for Indian Super App Revolution**
