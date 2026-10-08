# Swift Ship Tracker - Salesforce Project
Data Model and Security Model for Salesforce Project

## Phase 1: Designing Data Model and Security Model

### Project Overview
Swift Ship Tracker is a parcel delivery tracking system built on Salesforce.

### Data Model Includes:

#### 1. Parcel__c (Custom Object) - Main Object
Fields:
- Parcel_ID__c (Text, Unique)
- Status__c (Picklist: Ordered, Shipped, In-Transit, Delivered)
- Weight__c (Number)
- Estimated_Delivery_Date__c (Date)

#### 2. Delivery__c (Custom Object) - Tracking
Fields:
- Current_Location__c (Text)
- Delivery_Status__c (Picklist)
- Actual_Delivery_Date__c (Date)
- Lookup to Parcel__c

#### 3. Sender__c (Custom Object)
Fields:
- Name, Address__c, Phone__c, Email__c
- Relationship: One Sender has Many Parcels (Lookup)

#### 4. Receiver__c (Custom Object)
Fields:
- Name, Address__c, Phone__c, Email__c

### Relationship Diagram
Sender__c (1) ---> (Many) Parcel__c (1) ---> (1) Delivery__c
Receiver__c (1) ---> (Many) Parcel__c

### Security Model
- OWD: Private for Parcel__c and Delivery__c, Public Read for Sender__c
- Profiles:
    - System Admin: Full CRUD on all objects
    - Delivery Agent: Read/Write on Delivery__c, Read on Parcel__c
    - Customer User: Read only on own Parcel__c
- Sharing Rules: Share Parcel with related Sender
- Permission Sets: Delivery_Update_Access for agents

### Created By: Gopika
### Internship: Salesforce Developer - SkillWallet
