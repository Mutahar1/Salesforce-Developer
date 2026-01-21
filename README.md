# 🏡 Real Estate Property Management Platform

[![Salesforce Platform](https://img.shields.io/badge/Salesforce-Platform-blue?logo=salesforce)](https://www.salesforce.com/)  
[![LWC Version](https://img.shields.io/badge/LWC-3.9.1-blue?logo=salesforce)](https://developer.salesforce.com/docs/component-library/documentation/en/lwc)  
[![Apex Version](https://img.shields.io/badge/Apex-232.0-blue?logo=salesforce)](https://developer.salesforce.com/releases/release-notes)  
[![SOQL](https://img.shields.io/badge/SOQL-Standard-yellowgreen)](https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/soql_sosl/)  
[![Experience Cloud](https://img.shields.io/badge/Experience_Cloud-Release_232.0-blueviolet)](https://experiencecloud.salesforce.com/)  
[![JavaScript ES6+](https://img.shields.io/badge/JavaScript-ES6%2B-yellow?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)  
[![Stripe API v2023-08-16](https://img.shields.io/badge/Stripe-API%20v2023--08--16-%230677e6)](https://stripe.com/docs/api)  
[![Google OAuth 2.0](https://img.shields.io/badge/Google_OAuth-2.0-red?logo=google)](https://developers.google.com/identity/protocols/oauth2)  
[![LinkedIn OAuth](https://img.shields.io/badge/LinkedIn_OAuth-2.0-blue?logo=linkedin)](https://docs.microsoft.com/en-us/linkedin/shared/authentication/)  
[![DropBox API](https://img.shields.io/badge/DropBox-API-blueviolet?logo=dropbox)](https://www.dropbox.com/developers/documentation)  
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 📋 Table of Contents

- [Project Overview](#project-overview)  
- [Architecture](#architecture)  
- [Application Flow](#application-flow)  
- [Key Features](#key-features)  
- [Technology Stack](#technology-stack)  
- [Custom Objects](#custom-objects)  
- [LWC Components](#lwc-components)  
- [Apex Controllers](#apex-controllers)  
- [Screenshots](#screenshots)  
- [Setup & Configuration](#setup--configuration)  

---

## Project Overview

This platform is an all-in-one Real Estate Property Management System built on the Salesforce Platform. It features a sleek, modern Experience Cloud buyer portal and covers everything from property listings and lifecycle management to integrated e-commerce capabilities.

### Business Value

- **For Property Managers:** Centralized portfolio management with automated workflows.  
- **For Buyers:** Self-service portal for browsing, scheduling, and offers.  
- **For Agents:** Simplified lead and commission management.  
- **For Leadership:** Real-time analytics and reporting for informed decisions.

---

## Architecture

System Architecture Diagram
┌─────────────────────────────────────────────────────────────────────────────┐
│                          SALESFORCE PLATFORM                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                               │
│  ┌───────────────────────────────────────────────────────────────────────┐  │
│  │                     EXPERIENCE CLOUD SITE                              │  │
│  │                    (Buyer Self-Service Portal)                         │  │
│  └───────────────────────────────────────────────────────────────────────┘  │
│                                    │                                          │
│                                    │                                          │
│  ┌────────────────────────────────┴───────────────────────────────────┐     │
│  │               LIGHTNING WEB COMPONENTS LAYER (31 Components)        │     │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │  • Property Browsing   • Shopping Cart      • My Dashboard          │    │
│  │  • Property Details    • Checkout           • My Appointments       │    │
│  │  • Image Carousel      • Wishlist           • My Inquiries          │    │
│  │  • Property Filters    • Offer Modal        • My Offers             │    │
│  │  • Property Calculator • Schedule Modal     • My Properties         │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                    │                                          │
│                                    │                                          │
│  ┌────────────────────────────────┴───────────────────────────────────┐     │
│  │                   APEX BUSINESS LOGIC LAYER                         │     │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │  Controllers:                    Services:                          │    │
│  │  • PropertyController            • Authentication (Google, LinkedIn)│    │
│  │  • CartController                • Permission Assignment            │    │
│  │  • WishlistController            • Order Processing                │    │
│  │  • BuyerDashboardController      • Payment Integration             │    │
│  │  • MyOffersController            • Email Notifications             │    │
│  │  • CheckoutController                                               │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                    │                                          │
│                                    │                                          │
│  ┌────────────────────────────────┴───────────────────────────────────┐     │
│  │                     DATA MODEL LAYER (50+ Objects)                  │     │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │  Core Entities:                  Related Entities:                  │    │
│  │  • Property__c                   • PropertyInquiry__c              │    │
│  │  • Property_Listing__c           • Appointment__c                  │    │
│  │  • Offer__c                      • Wishlist__c                     │    │
│  │  • Agent__c                      • Cart__c                         │    │
│  │  • LocationSite__c               • Commission__c                   │    │
│  │  • Property_Image__c             • Invoice__c                      │    │
│  │  • Property_Feature__c           • PropertyDocument__c             │    │
│  │  • Property_Amenities__c         • Loan_Application__c             │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                    │                                          │
│                                    │                                          │
│  ┌────────────────────────────────┴───────────────────────────────────┐     │
│  │                   AUTOMATION & INTEGRATION                          │     │
│  ├─────────────────────────────────────────────────────────────────────┤    │
│  │  • Process Builder & Flows       • REST API Integration            │    │
│  │  • Approval Processes             • OAuth Authentication           │    │
│  │  • Validation Rules               • Payment Gateway (Stripe)       │    │
│  │  • Email Alerts & Templates       • Document Storage (DropBox)     │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                               │
└─────────────────────────────────────────────────────────────────────────────┘

                                    │
                    ┌───────────────┴───────────────┐
                    │                               │
            ┌───────▼────────┐            ┌────────▼────────┐
            │  External APIs  │            │  Third-Party    │
            │  • Stripe       │            │  Services       │
            │  • Google OAuth │            │  • DropBox      │
            │  • LinkedIn     │            │  • Email        │
            └─────────────────┘            └─────────────────┘

## Application Flow

┌─────────────┐
│   Buyer     │
│  (Guest)    │
└──────┬──────┘
       │
       │ 1. Browse Properties
       ▼
┌─────────────────────────┐
│  Property Listing Page  │
│  • Search & Filter      │
│  • Property Cards       │
│  • Add to Cart/Wishlist │
└──────┬──────────────────┘
       │
       │ 2. View Details
       ▼
┌─────────────────────────┐
│ Property Details Page   │
│  • Images & Features    │
│  • Calculator           │
│  • Submit Inquiry       │
│  • Schedule Viewing     │
│  • Make Offer ───────┐  │
└──────┬────────────────┘  │
       │                   │
       │                   │ Login Check
       │                   │
       ▼                   ▼
┌─────────────────┐  ┌──────────────┐
│  Add to Cart    │  │ Login Page   │
└──────┬──────────┘  └──────┬───────┘
       │                     │
       │ 3. Checkout         │ 4. Authenticated
       ▼                     ▼
┌─────────────────┐  ┌──────────────────────┐
│ Checkout Page   │  │  Buyer Dashboard     │
│  • Review Items │  │  • My Appointments   │
│  • Payment      │  │  • My Inquiries      │
│  • Place Order  │  │  • My Offers         │
└──────┬──────────┘  │  • My Properties     │
       │             │  • Order History     │
       │             └──────────────────────┘
       ▼
┌─────────────────┐
│  Order Success  │
│  • Confirmation │
│  • Invoice      │
└─────────────────┘
---

The platform integrates with external APIs like Stripe for payments, Google and LinkedIn for OAuth authentication, and Dropbox for document storage.

---

1. **Buyer (Guest):**  
   Browse properties using filters, add favorites or to cart without logging in.

2. **Property Listing & Details:**  
   Explore property info, image carousels, calculators, and submit inquiries or offers.

3. **Login:**  
   Required for making offers, scheduling viewings, and checkout.

4. **Buyer Dashboard:**  
   Access appointments, inquiries, offers, properties, and order history.

5. **Checkout & Orders:**  
   Review cart, make payments (via Stripe), and receive confirmations/invoices.

---

## Key Features

### 1. Property Management  
- Advanced filtering by price, location, amenities, and more  
- Image galleries and mortgage calculators  
- Document management with brochures and floor plans  

### 2. E-Commerce  
- Persistent shopping cart and wishlist  
- Secure payment processing via Stripe  
- Order history and invoice management  

### 3. Offer Management  
- Comprehensive offer submission and status tracking  
- Counter-offer handling and messaging with sellers  

### 4. Appointment Scheduling  
- Book in-person or virtual tours with email confirmations  
- Manage and track upcoming appointments  

### 5. Inquiry System  
- Submit and track property inquiries  
- Agent notifications and response history  

### 6. Buyer Dashboard  
- Profile management and personal preferences  
- Overview of owned properties, offers, inquiries, and appointments  

### 7. Authentication & Authorization  
- Social logins with Google and LinkedIn OAuth  
- Role-based access with permission sets  
- Guest browsing with limited functionality  

### 8. Agent & Commission Tracking  
- Manage agent specializations and commissions  
- Lead tracking and performance metrics  

### 9. Document Management  
- Store property documents securely via Dropbox  
- Version control and access permissions  

---

## Technology Stack

**Frontend:**  
- Lightning Web Components (LWC) 3.9.1  
- Lightning Design System (SLDS)  
- JavaScript ES6+  
- CSS3 & HTML5  

**Backend:**  
- Apex 232.0  
- Salesforce Database & SOQL  
- Experience Cloud  
- Process Builder & Flows  
- Approval Processes & Validation Rules  

**Integrations:**  
- Stripe API (v2023-08-16)  
- Google OAuth 2.0  
- LinkedIn OAuth 2.0  
- Dropbox API  

---

## Custom Objects

| Object Name                 | API Name                      | Description                       |
|----------------------------|-------------------------------|---------------------------------|
| Property                   | Property__c                   | Main property records            |
| Property Listing           | Property_Listing__c           | Active listings with pricing     |
| Property Image             | Property_Image__c             | Photos and media                 |
| Property Feature           | Property_Feature__c           | Specific features                |
| Property Amenities         | Property_Amenities__c         | Amenities junction object        |
| Property Document          | PropertyDocument__c           | Related documents                |
| Location Site             | LocationSite__c               | Property locations              |
| Amenities                 | Amenities__c                  | Master amenities list            |
| Offer                     | Offer__c                     | Property offers & counter-offers |
| Cart                      | Cart__c                      | Shopping cart                    |
| Invoice                   | Invoice__c                   | Order invoices                  |
| Commission                | Commission__c                | Agent commissions               |
| Property Inquiry          | PropertyInquiry__c           | Customer inquiries              |
| Appointment               | Appointment__c               | Property viewings               |
| Wishlist                  | Wishlist__c                  | Saved properties                |
| Loan Application          | Loan_Application__c          | Financing applications          |
| Agent                     | Agent__c                     | Real estate agents              |
| Territory                 | Territory__c                 | Sales territories              |

---

## LWC Components

| Component Name         | Purpose                          | Features                          |
|-----------------------|---------------------------------|----------------------------------|
| propertyContainer      | Main listing container           | Search, filter, pagination       |
| propertyCard           | Individual property card         | Quick view, action buttons       |
| propertyFilters        | Advanced filter panel            | Multi-criteria filtering         |
| propertyDetailsPage    | Full property view               | Detailed info & actions          |
| imageCarousel         | Image slider                    | Swipeable with thumbnails        |
| propertyCalculator     | Mortgage calculator              | Payment estimation               |
| wishlistDisplay        | Wishlist viewer                  | Multiple lists, sharing          |
| cartDisplay            | Shopping cart                   | Add/remove items, totals         |
| buyerDashboard         | User dashboard                   | Stats, quick actions             |
| makeOfferModal         | Offer submission modal           | Detailed offer form              |

---

## Apex Controllers

| Controller                 | Purpose                          | Methods    |
|----------------------------|---------------------------------|------------|
| PropertyController         | Property operations & offers    | 15+        |
| CartController             | Cart management & checkout      | 8          |
| WishlistController         | Wishlist CRUD                   | 6          |
| BuyerDashboardController   | Aggregated dashboard data       | 10         |
| CheckoutController         | Order processing                | 6          |
| GoogleAuthHandler          | Google OAuth                   | 2          |
| LinkedInAuthHandler        | LinkedIn OAuth                 | 2          |

---

## Screenshots

### Property Listing Page  
┌────────────────────────────────────────────────────────┐
│  [Search Bar]  [Filters]                    [Cart: 3] │
├────────────────────────────────────────────────────────┤
│                                                         │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐            │
│  │  Image   │  │  Image   │  │  Image   │            │
│  │          │  │          │  │          │            │
│  ├──────────┤  ├──────────┤  ├──────────┤            │
│  │ $500K    │  │ $750K    │  │ $1.2M    │            │
│  │ 3BR 2BA  │  │ 4BR 3BA  │  │ 5BR 4BA  │            │
│  │ [Cart]   │  │ [Cart]   │  │ [Cart]   │            │
│  └──────────┘  └──────────┘  └──────────┘            │
│                                                         │
└────────────────────────────────────────────────────────┘

### Property Details Page  
- Image carousel with swipe controls  
- Mortgage calculator and contact actions  
┌────────────────────────────────────────────────────────┐
│  [< Back]                            [Cart] [Wishlist] │
├────────────────────────────────────────────────────────┤
│  [======== Image Carousel ========]                    │
│  [  < Prev ]  [ 1 2 3 4 5 ]  [ Next > ]               │
├────────────────────────────────────────────────────────┤
│  Modern Family Home - $850,000                         │
│  123 Main St, San Francisco, CA                        │
│                                                         │
│  4 Beds  |  3 Baths  |  2,500 sqft  |  Built: 2020   │
├────────────────────────────────────────────────────────┤
│  [Make Offer] [Schedule Viewing] [Contact Agent]      │
│                                                         │
│  Mortgage Calculator                                    │
│  ┌────────────────────────────────────────┐           │
│  │ Monthly Payment: $4,200                │           │
│  └────────────────────────────────────────┘           │
└────────────────────────────────────────────────────────┘

### My Offers Dashboard
- Track all submitted offers with statuses  
- View messages, counter-offers, and deadlines  
┌────────────────────────────────────────────────────────┐
│  My Offers                                              │
├────────────────────────────────────────────────────────┤
│  [5 Total] [1 Draft] [2 Pending] [1 Accepted]         │
│                                                         │
│  Filter: [All ▼]                                       │
├────────────────────────────────────────────────────────┤
│  ┌────────────────────────────────────────────────┐   │
│  │ [Image] Property Name                  [Draft] │   │
│  │         123 Main St, SF                        │   │
│  │                                                 │   │
│  │  Your Offer: $850,000                          │   │
│  │  Counter Offer: $875,000                       │   │
│  │                                                 │   │
│  │  📧 MESSAGE FROM SELLER:                       │   │
│  │  "Thank you for your offer. We are willing..." │   │
│  │                                                 │   │
│  │  Offer Date: Jan 15, 2025                      │   │
│  │  Expires: Jan 22, 2025                         │   │
│  │                                                 │   │
│  │  Contingencies: [Financing] [Inspection]       │   │
│  │                                                 │   │
│  │  [View Property]                               │   │
│  └────────────────────────────────────────────────┘   │
└────────────────────────────────────────────────────────┘


---

## ⚙️ Setup & Configuration

### Step 1: Create Experience Cloud Site  
- Navigate to Setup → Digital Experiences → All Sites → New  
- Choose "Build Your Own (LWR)" template  
- Name it "Property Buyer Portal"  

### Step 2: Add Components to Pages  
- Home Page: homePageHero, propertyContainer  
- Property Details: propertyDetailsPage  
- Dashboard: buyerDashboard (with tabs)  
- Checkout Page: checkout  

### Step 3: Configure Navigation  
- Home, Properties, My Dashboard, Cart, Login/Register  

### Step 4: Set Up Guest User Profile  
- Grant read access to core property objects  
- Allow create access on Cart and Wishlist for anonymous users  

### Step 5: Configure Authentication  
- Enable self-registration  
- Set up Google and LinkedIn OAuth providers  
- Configure permission set auto-assignment  

### Step 6: Load Sample Data (optional)  
- Import sample properties and test data  

### Step 7: Activate and Test  
- Publish your Experience Cloud site  
- Test guest browsing, cart, and login flows  
- Verify OAuth login and integrations  

---


