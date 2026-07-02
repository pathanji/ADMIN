# INDIXA Database Schema

## Firestore Collections Structure

### 1. Users Collection

```json
/users/{userId}
{
  "name": "string",
  "phone": "string",
  "email": "string",
  "profilePhoto": "string (URL)",
  "role": "endUser | vendor | admin",
  "status": "active | blocked | suspended",
  "verified": "boolean",
  "createdAt": "timestamp",
  "updatedAt": "timestamp",
  "lastLogin": "timestamp",
  "location": {
    "latitude": "number",
    "longitude": "number",
    "city": "string",
    "state": "string",
    "country": "string"
  },
  "preferences": {
    "language": "en | hi | mr | gu | ta",
    "theme": "light | dark",
    "notifications": "boolean",
    "privacyLevel": "public | private"
  },
  "wallet": {
    "balance": "number",
    "currency": "INR"
  },
  "savedAddresses": [
    {
      "label": "Home | Work | Other",
      "address": "string",
      "latitude": "number",
      "longitude": "number",
      "isDefault": "boolean"
    }
  ]
}
```

### 2. Partners Collection

```json
/partners/{partnerId}
{
  "userId": "string (reference to user)",
  "type": "taxi_driver | auto_driver | bike_rider | delivery | restaurant | grocery | pharmacy | seller | hotel | service_provider",
  "name": "string",
  "phone": "string",
  "email": "string",
  "profilePhoto": "string (URL)",
  "businessName": "string (optional)",
  "status": "pending | approved | rejected | suspended | active",
  "kycStatus": {
    "status": "pending | verified | rejected",
    "submittedAt": "timestamp",
    "verifiedAt": "timestamp",
    "rejectionReason": "string (optional)"
  },
  "documents": [
    {
      "type": "aadhaar | pan | driving_license | rc | insurance | gst | fssai",
      "documentNumber": "string",
      "url": "string (firestore storage URL)",
      "uploadedAt": "timestamp",
      "verified": "boolean"
    }
  ],
  "bankDetails": {
    "accountHolder": "string",
    "accountNumber": "string",
    "ifsc": "string",
    "bankName": "string",
    "verified": "boolean"
  },
  "location": {
    "latitude": "number",
    "longitude": "number",
    "city": "string",
    "state": "string",
    "serviceArea": "string"
  },
  "onlineStatus": "boolean",
  "availability": {
    "status": "available | busy | offline",
    "lastStatusChange": "timestamp"
  },
  "vehicle": {
    "type": "car | auto | bike | tempo",
    "registrationNumber": "string",
    "model": "string",
    "capacity": "number"
  },
  "rating": {
    "average": "number (1-5)",
    "totalReviews": "number",
    "ratings": [
      {
        "userId": "string",
        "rating": "number",
        "review": "string",
        "createdAt": "timestamp"
      }
    ]
  },
  "earnings": {
    "today": "number",
    "week": "number",
    "month": "number",
    "total": "number"
  },
  "wallet": {
    "balance": "number",
    "pendingAmount": "number",
    "currency": "INR"
  },
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 3. Orders Collection

```json
/orders/{orderId}
{
  "userId": "string",
  "partnerId": "string",
  "serviceId": "string",
  "serviceType": "string",
  "status": "pending | accepted | in_progress | completed | cancelled | refunded",
  "items": [
    {
      "id": "string",
      "name": "string",
      "quantity": "number",
      "price": "number",
      "total": "number"
    }
  ],
  "pickup": {
    "address": "string",
    "latitude": "number",
    "longitude": "number",
    "instructions": "string",
    "arrivalTime": "timestamp",
    "completionTime": "timestamp"
  },
  "dropoff": {
    "address": "string",
    "latitude": "number",
    "longitude": "number",
    "instructions": "string",
    "arrivalTime": "timestamp",
    "completionTime": "timestamp"
  },
  "pricing": {
    "basePrice": "number",
    "distance": "number",
    "distanceCharge": "number",
    "time": "number",
    "timeCharge": "number",
    "surgeCharge": "number",
    "discount": "number",
    "tax": "number",
    "total": "number",
    "currency": "INR"
  },
  "coupon": {
    "code": "string",
    "discount": "number",
    "type": "percentage | fixed"
  },
  "payment": {
    "method": "upi | card | wallet | net_banking | cash",
    "status": "pending | success | failed",
    "paymentId": "string",
    "transactionId": "string",
    "completedAt": "timestamp"
  },
  "tracking": {
    "isLive": "boolean",
    "currentLocation": {
      "latitude": "number",
      "longitude": "number",
      "timestamp": "timestamp"
    },
    "eta": "number (minutes)",
    "otp": "string",
    "otpVerified": "boolean",
    "otpVerifiedAt": "timestamp"
  },
  "rating": {
    "score": "number (1-5)",
    "review": "string",
    "ratedAt": "timestamp",
    "ratedBy": "user | partner"
  },
  "createdAt": "timestamp",
  "acceptedAt": "timestamp",
  "completedAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 4. Admins Collection

```json
/admins/{adminId}
{
  "userId": "string",
  "name": "string",
  "email": "string",
  "phone": "string",
  "role": "super_admin | admin | manager | finance | support | operations | marketing | analytics | readonly",
  "status": "active | inactive | suspended",
  "permissions": [
    "user.view | user.edit | user.delete | user.block",
    "partner.view | partner.edit | partner.approve | partner.reject",
    "order.view | order.edit | order.cancel",
    "payment.view | payment.process | payment.refund",
    "promotion.create | promotion.edit | promotion.delete",
    "analytics.view | analytics.export",
    "admin.create | admin.edit | admin.delete"
  ],
  "twoFactorEnabled": "boolean",
  "lastLogin": "timestamp",
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 5. Locations Collection (Hierarchical)

```json
/locations/{countryId}/states/{stateId}/districts/{districtId}/cities/{cityId}/areas/{areaId}/zones/{zoneId}/localities/{localityId}

{
  "name": "string",
  "code": "string",
  "type": "country | state | district | city | area | zone | locality",
  "coordinates": {
    "latitude": "number",
    "longitude": "number"
  },
  "enabledServices": ["service_1", "service_2", ...],
  "disabledServices": ["service_1", "service_2", ...],
  "createdAt": "timestamp"
}
```

### 6. Services Collection

```json
/services/{serviceId}
{
  "name": "string",
  "type": "mobility | food | retail | healthcare | home_services | travel | finance | utility | education | freelance | entertainment",
  "category": "string",
  "description": "string",
  "icon": "string (URL)",
  "image": "string (URL)",
  "rating": "number (1-5)",
  "commission": {
    "percentage": "number",
    "fixed": "number",
    "type": "percentage | fixed | hybrid"
  },
  "availableLocations": ["locationId_1", "locationId_2", ...],
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 7. Orders Collection for Food/Retail

```json
/orders/{orderId}
{
  "userId": "string",
  "vendorId": "string",
  "deliveryPartnerId": "string",
  "serviceType": "food | grocery | pharmacy | marketplace",
  "status": "pending | accepted | preparing | ready | dispatched | in_transit | delivered | cancelled",
  "items": [
    {
      "itemId": "string",
      "name": "string",
      "quantity": "number",
      "price": "number",
      "specialInstructions": "string"
    }
  ],
  "deliveryAddress": {
    "address": "string",
    "latitude": "number",
    "longitude": "number",
    "contactPerson": "string",
    "contactPhone": "string"
  },
  "pricing": {
    "subtotal": "number",
    "deliveryFee": "number",
    "tax": "number",
    "discount": "number",
    "total": "number"
  },
  "estimatedDelivery": "timestamp",
  "createdAt": "timestamp",
  "acceptedAt": "timestamp",
  "deliveredAt": "timestamp"
}
```

### 8. Promotions Collection

```json
/promotions/{promotionId}
{
  "code": "string",
  "type": "coupon | promo_code | cashback | referral | seasonal",
  "discount": "number",
  "discountType": "percentage | fixed",
  "description": "string",
  "validFrom": "timestamp",
  "validTill": "timestamp",
  "usageLimit": "number",
  "usedCount": "number",
  "usagePerUser": "number",
  "minOrderAmount": "number",
  "maxDiscount": "number",
  "applicableServices": ["service_1", "service_2", ...],
  "applicableLocations": ["location_1", "location_2", ...],
  "active": "boolean",
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 9. Wallet Collection

```json
/wallet/{userId}
{
  "userId": "string",
  "balance": "number",
  "pendingAmount": "number",
  "currency": "INR",
  "transactions": [
    {
      "id": "string",
      "type": "credit | debit",
      "amount": "number",
      "description": "string",
      "orderId": "string",
      "reason": "order | refund | cashback | reward | admin_adjustment",
      "createdAt": "timestamp"
    }
  ],
  "createdAt": "timestamp",
  "updatedAt": "timestamp"
}
```

### 10. Notifications Collection

```json
/notifications/{userId}/{notificationId}
{
  "userId": "string",
  "title": "string",
  "message": "string",
  "type": "order | payment | offer | system | alert | promotion",
  "relatedOrderId": "string",
  "relatedPartnerId": "string",
  "read": "boolean",
  "readAt": "timestamp",
  "createdAt": "timestamp",
  "expiresAt": "timestamp"
}
```

### 11. Analytics Collection

```json
/analytics/daily/{date}
{
  "date": "string (YYYY-MM-DD)",
  "revenue": {
    "total": "number",
    "byService": { "service_1": "number", "service_2": "number", ... }
  },
  "orders": {
    "total": "number",
    "completed": "number",
    "cancelled": "number",
    "averageValue": "number"
  },
  "users": {
    "newUsers": "number",
    "activeUsers": "number",
    "returningUsers": "number"
  },
  "partners": {
    "newPartners": "number",
    "activePartners": "number",
    "onlinePartners": "number"
  },
  "createdAt": "timestamp"
}
```

## Firestore Indexes

Composite indexes required:
```
1. /orders: userId, createdAt DESC
2. /orders: partnerId, status, createdAt DESC
3. /partners: type, location, onlineStatus
4. /notifications: userId, createdAt DESC, read
5. /analytics/daily: date DESC
```
