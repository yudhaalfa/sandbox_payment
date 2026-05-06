# Payment Gateway Prototype - Horizon UI Chakra TS

A high-performance web-based Payment Gateway system designed to manage transaction flows between **Merchants**, **Admins**, and **Customers** using React, TypeScript, and Zustand.

---

## 🛠 Tech Stack
*   **Frontend Framework:** React 19 with TypeScript
*   **UI Library:** Chakra UI (v2.6.1)
*   **State Management:** Zustand (v5.0.12) with Persist Middleware
*   **Routing:** React Router DOM (v6.25.1)
*   **Styling:** Emotion & Framer Motion

---

## 🚀 Technical Development Lifecycle

The development of this application followed a structured iterative process to ensure data integrity and a smooth user experience:

1.  **UI Slicing & Layouting:** 
    Converted Horizon UI designs into functional components using Chakra UI. Established three core layout structures: `AuthLayout` (Login/Register), `AdminLayout` (Main Dashboard), and a clean Public Route for payment links.
    
2.  **Global State Configuration (Zustand):** 
    Initialized `useGlobalData.ts` and `useAuthStore.ts` using the `persist` middleware. This simulates a real-time database by storing transaction logs and user credentials directly in the browser's Local Storage.

3.  **Implementation of Role-Based Access Control (RBAC):** 
    Defined absolute roles: `'ADMIN'` and `'MERCHANT'`. Implemented strict route protection in `Main.tsx` using `<Navigate>` to ensure users are redirected if they attempt to access unauthorized dashboards.

4.  **Merchant Billing Logic:** 
    Developed the `createInvoice` function to handle merchant inputs, generating unique invoice IDs (e.g., `INV-XXXXXXXX`) and dynamic payment URLs.

5.  **Public Payment Gateway Route:** 
    Created a dynamic `/pay/:id` route using `useParams`. This allows the application to fetch specific invoice data from the global state and render it for unauthenticated customers.

6.  **Data Architecture Unification (Single Source of Truth):** 
    Resolved "Split-Brain" data issues by migrating all merchant-specific logic into `useGlobalData`. This ensures that Admin, Merchant, and Public views always reflect identical, real-time data.

7.  **3-Step Transaction State Machine:** 
    Refined the payment lifecycle into three logical stages:
    *   `PENDING`: Invoice generated, awaiting customer action.
    *   `WAITING`: Customer has initiated payment; transaction moved to Admin queue for verification.
    *   `PAID` / `FAILED`: Final resolution executed by the Admin.

8.  **UX & Accessibility Optimizations:** 
    *   Enhanced the Sign-In flow by wrapping inputs in a `<form>` element to support "Enter to Submit" functionality.
    *   Integrated the browser’s *Clipboard API* for a "One-Click Copy Link" feature on the merchant table.

---

## 💻 Getting Started

Follow these steps to run the project on your local machine:

### 1. Prerequisites
Ensure you have **Node.js** and **npm** installed.

### 2. Install Dependencies
Clone the repository and run the following command in your terminal:
```bash
npm install
