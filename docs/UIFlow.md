# UI Flow

FFixiT Management System (FFixiT-MS)

---

## Document Information

| Item        | Value                 |
| ----------- | --------------------- |
| Version     | 1.0                   |
| Author      | Muhammad Irfan Syafiq |
| Project     | FFixiT-MS             |
| Last Update | 2026-07-09            |
| Status      | Active                |

---

# Purpose

This document defines the standard navigation flow and user journey for FFixiT-MS. Its purpose is to ensure that every future UI page, screen, and workflow follows a consistent, predictable, and role-aware path from login through task completion and return to the main system.

This document supports:

- consistent navigation across modules
- clear role-based experiences
- predictable transitions between list, detail, create, edit, and confirmation states
- safer movement between pages and workflows
- better implementation planning for future UI and frontend development

---

# Global Navigation

The application should follow one consistent global navigation pattern.

Login
↓
Dashboard
↓
Module Entry
↓
List Page
↓
Detail Page
↓
Create / Edit
↓
Confirmation / Success / Error
↓
Back to List or Return to Dashboard

## Global Navigation Principles

- Every authenticated user starts from Login and reaches Dashboard.
- Navigation must be role-based and permission-aware.
- Every major module must support a list view and a detail view.
- Create and edit actions should return to the relevant list or detail page.
- Destructive actions should be confirmed before execution.
- Users must be able to return safely to the previous level at any point.

---

# Navigation Structure

## IT

Sidebar hierarchy:

- Dashboard
- User Management
- Employee Management
- Role & Permission
- Customer Management
- Service Ticket
- Inventory Management
- Supplier Management
- Direct Sales (POS)
- Operational Expense
- Monitoring & Reports
- Audit Log
- System Configuration

## Kepala Toko

Sidebar hierarchy:

- Dashboard
- Monitoring & Reports
- Operational Expense
- Service Ticket Overview
- Inventory Overview
- Sales Overview

## Admin Gudang

Sidebar hierarchy:

- Dashboard
- Inventory Management
- Supplier Management
- Stock Movement
- Purchase History
- Request Sparepart
- Stock Opname
- Report Overview

## Customer Service

Sidebar hierarchy:

- Dashboard
- Customer Management
- Service Ticket
- Direct Sales (POS)
- Invoice
- Print Receipt
- Monitoring Overview

## Teknisi

Sidebar hierarchy:

- Dashboard
- My Ticket
- Diagnosis
- Progress Service
- Evidence Upload
- Service History

---

# Module Navigation Flow

## Authentication

- Entry Page: Login
- List Page: Not applicable
- Detail Page: Not applicable
- Create: Register or reset password flow if available
- Edit: Password change or profile update
- Delete: Not applicable
- Print: Not applicable
- Back Navigation: Back to Login or return to previous entry point
- Possible Exit Points: Login success, logout, session timeout, invalid credentials

## Dashboard

- Entry Page: Dashboard
- List Page: Dashboard widgets and summaries
- Detail Page: Role-specific summary detail view
- Create: Not primary; may support quick actions
- Edit: Not primary; may support dashboard preferences if introduced later
- Delete: Not applicable
- Print: Optional report export from dashboard
- Back Navigation: Return to previous module from widget or shortcut
- Possible Exit Points: Navigate to module, logout, open quick action

## Customer Management

- Entry Page: Customer List
- List Page: Customer List
- Detail Page: Customer Detail
- Create: Add Customer
- Edit: Edit Customer
- Delete: Delete or deactivate customer record
- Print: Print customer history or service summary if required
- Back Navigation: Back to Customer List from detail or create/edit page
- Possible Exit Points: Return to Dashboard, go to Service Ticket, go to Sales History

## Service Ticket

- Entry Page: Ticket List
- List Page: Ticket List
- Detail Page: Ticket Detail
- Create: Create Ticket
- Edit: Edit Ticket Information or update service metadata
- Delete: Cancel request or delete draft ticket if allowed
- Print: Print Service Receipt or invoice
- Back Navigation: Back to Ticket List from detail or create/edit page
- Possible Exit Points: Return to Dashboard, proceed to Diagnosis, proceed to Invoice, cancel request

## Inventory Management

- Entry Page: Inventory Overview or Stock List
- List Page: Stock List / Product List
- Detail Page: Product Detail or Stock Detail
- Create: Add Product or stock entry
- Edit: Edit Product, stock adjustment, or item metadata
- Delete: Remove inactive or invalid item if permitted
- Print: Print stock report or inventory summary
- Back Navigation: Return to Inventory List from product detail or adjustment form
- Possible Exit Points: Return to Dashboard, go to Supplier, go to Stock Movement, go to Purchase History

## Supplier Management

- Entry Page: Supplier List
- List Page: Supplier List
- Detail Page: Supplier Detail
- Create: Add Supplier
- Edit: Edit Supplier
- Delete: Deactivate supplier if allowed
- Print: Print supplier purchase summary or history
- Back Navigation: Back to Supplier List
- Possible Exit Points: Return to Inventory, go to Purchase History

## Direct Sales (POS)

- Entry Page: Sales Transaction Page
- List Page: Sales History
- Detail Page: Invoice Detail
- Create: Create Sales Invoice
- Edit: Edit pending invoice or transaction details
- Delete: Void or cancel invoice if permitted
- Print: Print Invoice
- Back Navigation: Back to Sales History or Dashboard
- Possible Exit Points: Return to Dashboard, proceed to payment, print invoice

## Operational Expense

- Entry Page: Expense List
- List Page: Expense List
- Detail Page: Expense Detail
- Create: Add Expense
- Edit: Edit Expense
- Delete: Delete or void expense entry
- Print: Print expense report
- Back Navigation: Back to Expense List
- Possible Exit Points: Return to Dashboard, return to Monitoring & Reports

## Monitoring & Reports

- Entry Page: Monitoring Dashboard
- List Page: Report List or filtered monitoring pages
- Detail Page: Detailed report or metric page
- Create: Not primary
- Edit: Not primary; may allow report filter adjustment
- Delete: Not primary
- Print: Print report or export data summary
- Back Navigation: Back to Dashboard or previous report section
- Possible Exit Points: Return to Dashboard, navigate to module-specific detail

## User Management

- Entry Page: User List
- List Page: User List
- Detail Page: User Detail
- Create: Add User
- Edit: Edit User or Role Assignment
- Delete: Deactivate or remove account
- Print: Not applicable
- Back Navigation: Back to User List
- Possible Exit Points: Return to Dashboard, go to Role & Permission

## Audit Log

- Entry Page: Audit Log List
- List Page: Audit Log List
- Detail Page: Audit Log Detail
- Create: Not applicable
- Edit: Not applicable
- Delete: Not applicable
- Print: Optional export or printable report
- Back Navigation: Back to Audit Log List
- Possible Exit Points: Return to Dashboard or monitoring page

---

# User Journey

## Customer Service

Login
↓
Dashboard
↓
Customer List
↓
Create Customer
↓
Customer Detail
↓
Create Ticket
↓
Print Receipt
↓
Dashboard

## Teknisi

Login
↓
Dashboard
↓
My Ticket List
↓
Ticket Detail
↓
Diagnosis
↓
Progress Service
↓
Evidence Upload
↓
Finish Service
↓
Dashboard

## Admin Gudang

Login
↓
Dashboard
↓
Inventory List
↓
Stock Detail
↓
Stock Adjustment or Stock Opname
↓
Request Sparepart
↓
Inventory List
↓
Dashboard

## Kepala Toko

Login
↓
Dashboard
↓
Monitoring & Reports
↓
Ticket Monitoring
↓
Inventory Monitoring
↓
Operational Expense
↓
Dashboard

## IT

Login
↓
Dashboard
↓
User Management
↓
User Detail or Role Assignment
↓
Audit Log
↓
Monitoring & Reports
↓
Dashboard

---

# Breadcrumb Standard

Breadcrumbs should help users understand their current position and return to higher-level pages quickly.

## General Breadcrumb Pattern

Home / Module / List / Detail

## Examples

- Home / Service Ticket / Ticket List / Ticket Detail
- Home / Inventory / Stock List / Product Detail
- Home / Customer / Customer List / Customer Detail
- Home / Reports / Monitoring / Ticket Monitoring

## Breadcrumb Rules

- Breadcrumbs must appear on all non-root list and detail pages.
- The first breadcrumb should always point to the Dashboard.
- The current page should be the last breadcrumb item.
- Breadcrumbs should remain visible when entering create or edit forms.
- Breadcrumbs should support safe back navigation without relying on the browser only.

---

# Page Transition Rules

## After Save

- Show success feedback.
- Redirect to the relevant detail page if the record was created.
- Redirect to the detail page or list page after edit depending on context.
- Preserve the user’s next logical action if the workflow continues.

## After Cancel

- Return to the previous page or list page.
- Do not commit any changes.
- Show no destructive effect.

## After Delete

- Show confirmation first.
- After confirmation, return to the list page.
- Show a success or failure message.
- If deletion is not permitted, block the action and explain the reason.

## After Approve

- Move the ticket or request to the next valid workflow state.
- Return to the relevant detail page or next action screen.
- Show confirmation of approval.

## After Reject

- Return to the previous workflow state or request form.
- Show a reason message if applicable.
- Keep the user in the same module context.

## After Finish Service

- Move the ticket to completed or ready-for-invoice state.
- Show completion confirmation.
- Redirect to the ticket detail or invoice preparation step.

## After Print

- Open print view or download action.
- Return to the originating page after completion.
- Do not interrupt the main workflow unnecessarily.

## After Logout

- Return to Login.
- Clear active session context.
- Remove role-specific navigation state.

---

# Deep Navigation Rules

The system should support a maximum depth of four levels in primary navigation.

Recommended depth:

1. Dashboard
2. Module Entry
3. List Page
4. Detail / Create / Edit / Confirmation

## Navigation Safety Rules

- Every deep page must include a clear back action.
- Users should always be able to return to the previous list view.
- Confirmation screens must provide both confirm and cancel actions.
- Detail pages should include a return path to the list page.
- Create and edit pages should always include a cancel route.
- No critical workflow should require the user to rely on browser back alone.

## Return Strategy

- Use explicit back buttons or breadcrumb links where possible.
- Use consistent navigation labels such as Back to List, Cancel, Return to Dashboard.
- Preserve context where the user is continuing a workflow.

---

# Summary

This document becomes the official navigation standard for all future UI and frontend implementation in FFixiT-MS. It defines how users move through the system, how role-based menus should be structured, how module flows should behave, and how users should always be able to return safely within the application.
