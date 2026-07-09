# Screen Specification

FFixiT Management System (FFixiT-MS)

---

## Document Information

| Item    | Value                 |
| ------- | --------------------- |
| Version | 1.0                   |
| Author  | Muhammad Irfan Syafiq |
| Project | FFixiT-MS             |
| Status  | Active                |

---

# Screen Template

Each page in this document includes a consistent template documenting the screen purpose, structure, navigation, business rules, and implementation details.

- Page Name
- Module
- Purpose
- Accessible Roles
- Route (recommended)
- Breadcrumb
- Page Layout
- Header
- Toolbar
- Action Buttons
- Search
- Filter
- Table
- Cards
- Forms
- Tabs
- Modal Dialogs
- Sidebar Behaviour
- Status Badge
- Empty State
- Loading State
- Validation Messages
- Navigation Flow
- Business Rules
- Related Database Tables
- Related Components

---

# Authentication

## Login

- Module: Authentication
- Purpose: Authenticate users and grant access via RBAC.
- Accessible Roles: All roles.
- Route (recommended): `/login`
- Breadcrumb: Login
- Page Layout: Centered authentication form on light background with brand identity and concise login instructions.
- Header: Page title and subtitle visible above form.
- Toolbar: Not applicable.
- Action Buttons: Primary Sign In button, secondary Forgot Password link.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Login form card.
- Forms: Email, password, remember me checkbox, submit button.
- Tabs: Not applicable.
- Modal Dialogs: Optional password reset flow can use modal or separate page.
- Sidebar Behaviour: No sidebar on login page.
- Status Badge: Not applicable.
- Empty State: Not applicable.
- Loading State: Inline spinner on Sign In button when submitting.
- Validation Messages: Inline field-level errors for email and password, generic authentication failure message.
- Navigation Flow: Login → Dashboard on success; display error on failure.
- Business Rules: Must validate credentials and apply role-based navigation after login.
- Related Database Tables: `users`, `roles`, `role_user` or equivalent pivot table.
- Related Components: FormInput, PrimaryButton, LoadingSpinner, ValidationMessage.

---

# Dashboard

## Dashboard Home

- Module: Dashboard
- Purpose: Provide role-specific operational overview, metrics, and shortcuts.
- Accessible Roles: IT, Kepala Toko, Admin Gudang, Customer Service, Teknisi.
- Route (recommended): `/dashboard`
- Breadcrumb: Dashboard
- Page Layout: Top navbar and sidebar shell, summary cards at top, analytics card and quick actions below.
- Header: Page title, subtitle, contextual status.
- Toolbar: Quick action buttons for common workflows.
- Action Buttons: Primary action for the most important workflow, secondary links to module pages.
- Search: Optional global quick search in top navbar.
- Filter: Optional date or status filter for dashboard widgets.
- Table: Not required, but recent activity may use list cards.
- Cards: StatisticCard, ChartCard, RecentActivityCard, QuickActionCard, NotificationCard.
- Forms: Not applicable.
- Tabs: Optional tabs for role-specific metric categories.
- Modal Dialogs: Rare, only for onboarding hints or new feature notices.
- Sidebar Behaviour: Standard application sidebar with active Dashboard highlight.
- Status Badge: Used inside cards to mark trend or risk status.
- Empty State: Show placeholder state if no data is available for a metric.
- Loading State: Section-level skeleton or spinner until metrics load.
- Validation Messages: Not applicable.
- Navigation Flow: Dashboard → Module List / Detail as user selects shortcuts.
- Business Rules: Each role sees tailored metrics and accessible shortcuts only.
- Related Database Tables: `tickets`, `products`, `sales`, `operational_expenses`, `audit_logs`, `stock_movements`.
- Related Components: StatisticCard, ChartCard, QuickActionCard, NotificationCard, TopNavbar, Sidebar.

---

# Customer Management

## Customer List

- Module: Customer Management
- Purpose: Display all customers and support customer search, filtering, and basic actions.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/customers`
- Breadcrumb: Dashboard / Customers
- Page Layout: Table list with top toolbar, search, filters, and action buttons.
- Header: Page title, subtitle, customer count.
- Toolbar: Add Customer, refresh, export, filter toggle.
- Action Buttons: Create Customer, view details, edit, delete, print summary.
- Search: Prominent search bar above table.
- Filter: Status, segment, date range, last activity.
- Table: Responsive, sortable columns, row number, action column, status column.
- Cards: Optional summary cards for customer count and recent sign-ups.
- Forms: Not on list view aside from search/filter controls.
- Tabs: Optional tabs for customer groups or active/inactive views.
- Modal Dialogs: ConfirmationModal for delete and status changes.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive, VIP, warranty eligible.
- Empty State: Clear instruction to create first customer with primary action.
- Loading State: Skeleton rows or spinner within table area.
- Validation Messages: Not applicable.
- Navigation Flow: Customer List → Customer Detail or Create Customer → back to list.
- Business Rules: Only CS and IT can manage customers; customer deletion may require soft delete or deactivation.
- Related Database Tables: `customers`, `tickets`, `sales`.
- Related Components: DataTable, SearchBar, FilterPanel, Pagination, StatusBadge, ConfirmationModal.

## Customer Create

- Module: Customer Management
- Purpose: Capture new customer information.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/customers/create`
- Breadcrumb: Dashboard / Customers / Add Customer
- Page Layout: Form page with labels above inputs and save/cancel actions.
- Header: Page title and instruction text.
- Toolbar: Not required.
- Action Buttons: Save, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form card.
- Forms: Name, email, phone, address, customer type, notes.
- Tabs: Optional for customer details vs history sections.
- Modal Dialogs: Validation error modal if needed.
- Sidebar Behaviour: Standard.
- Status Badge: Display default status or VIP flag inside form summary.
- Empty State: Not applicable.
- Loading State: Spinner on save button.
- Validation Messages: Inline required and format messages for email/phone.
- Navigation Flow: Create Customer → save → redirect to Customer Detail or list.
- Business Rules: New customer must have valid contact data; duplicate check may be required.
- Related Database Tables: `customers`.
- Related Components: FormInput, FormSelect, FormTextarea, PrimaryButton, SecondaryButton, ValidationMessage.

## Customer Detail

- Module: Customer Management
- Purpose: Show customer profile, service history, and sales history.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/customers/{id}`
- Breadcrumb: Dashboard / Customers / Customer Detail
- Page Layout: Detail header with actions, tabs for profile/history, summary cards.
- Header: Customer name, status, primary action.
- Toolbar: Edit Customer, Create Ticket, Print, Back to List.
- Action Buttons: Edit, Create Ticket, Print Receipt.
- Search: Optional search within history tabs.
- Filter: Status or date filter within history lists.
- Table: Service History and Sales History tables.
- Cards: InfoCard for contact summary and ticket metrics.
- Forms: Not primary; may use read-only detail fields.
- Tabs: Profile, Service History, Sales History, Warranty.
- Modal Dialogs: ConfirmationModal for customer deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: Customer type and warranty flags.
- Empty State: Show message if no history exists and provide action to create ticket.
- Loading State: Content skeleton while loading customer details.
- Validation Messages: Not applicable.
- Navigation Flow: Detail → Edit or Create Ticket → return to detail.
- Business Rules: Only CS or IT may initiate ticket from customer detail.
- Related Database Tables: `customers`, `tickets`, `sales`, `ticket_warranties`.
- Related Components: PageHeader, Tabs, InfoCard, DataTable, PrimaryButton, StatusBadge.

## Customer Edit

- Module: Customer Management
- Purpose: Update existing customer data.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/customers/{id}/edit`
- Breadcrumb: Dashboard / Customers / Customer Detail / Edit
- Page Layout: Standard form page.
- Header: Page title, subtitle with customer name.
- Toolbar: Save, cancel.
- Action Buttons: Update, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form card.
- Forms: Editable customer fields.
- Tabs: Optional profile vs settings tabs.
- Modal Dialogs: Confirmation on cancel if changes present.
- Sidebar Behaviour: Standard.
- Status Badge: Show current status on header.
- Empty State: Not applicable.
- Loading State: Save button spinner and page-level skeleton if needed.
- Validation Messages: Inline field validation and required field indicators.
- Navigation Flow: Edit → save → Customer Detail; cancel → Customer Detail.
- Business Rules: Updates must preserve ticket/customer history.
- Related Database Tables: `customers`.
- Related Components: FormInput, FormSelect, PrimaryButton, SecondaryButton, ValidationMessage.

---

# Service Ticket

## Ticket List

- Module: Service Ticket
- Purpose: Display all service tickets and support ticket management.
- Accessible Roles: Customer Service, Teknisi, IT.
- Route (recommended): `/tickets`
- Breadcrumb: Dashboard / Tickets
- Page Layout: List page with top toolbar, search, filter panel, and responsive table.
- Header: Page title, ticket summary count.
- Toolbar: Create Ticket, refresh, filter toggle, export.
- Action Buttons: Create Ticket, view, assign, cancel request.
- Search: Prominent search field for ticket ID, customer, device, status.
- Filter: Status, technician, date range, priority, warranty.
- Table: Ticket number, customer, device, status badge, technician, updated date, actions.
- Cards: Optional summary cards for waiting, in progress, completed counts.
- Forms: Search/filter controls only.
- Tabs: Optional tabs for ticket categories (All, Waiting, In Progress, Completed).
- Modal Dialogs: ConfirmationModal for cancel, assign, status change.
- Sidebar Behaviour: Standard.
- Status Badge: Waiting Technician, Diagnosis, In Progress, Waiting Customer Approval, Completed, Cancelled.
- Empty State: Use clear messaging and Create Ticket action when no tickets exist.
- Loading State: Table skeleton rows or spinner.
- Validation Messages: Not applicable.
- Navigation Flow: Ticket List → Ticket Detail, Create Ticket.
- Business Rules: Ticket list respects role-based access and assignment.
- Related Database Tables: `tickets`, `ticket_progresses`, `ticket_photos`, `ticket_parts`, `ticket_cancellations`, `users`, `employees`.
- Related Components: DataTable, SearchBar, FilterPanel, StatusBadge, Pagination, ConfirmationModal.

## Ticket Create

- Module: Service Ticket
- Purpose: Capture a new service ticket from a customer visit.
- Accessible Roles: Customer Service.
- Route (recommended): `/tickets/create`
- Breadcrumb: Dashboard / Tickets / Create Ticket
- Page Layout: Multi-section form with customer selection, device details, problem details, and initial estimates.
- Header: Page title and instructions.
- Toolbar: Save, cancel.
- Action Buttons: Create Ticket, Cancel.
- Search: Customer search / quick lookup within form.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Customer summary card, device details card.
- Forms: Customer select/search, device, complaint, initial notes, estimate, attachments.
- Tabs: Optional Customer / Device / Summary tabbed form.
- Modal Dialogs: ConfirmationModal for cancel.
- Sidebar Behaviour: Standard.
- Status Badge: Default ticket status set to Waiting Technician after creation.
- Empty State: Not applicable.
- Loading State: Save button spinner.
- Validation Messages: Inline required field messages for customer, device, complaint.
- Navigation Flow: Create Ticket → save → Ticket Detail or Ticket List.
- Business Rules: CS must capture customer and device details, and print receipt on creation.
- Related Database Tables: `tickets`, `customers`, `employees`, `ticket_photos`.
- Related Components: FormInput, FormTextarea, FormSelect, PrimaryButton, SecondaryButton, ValidationMessage.

## Ticket Detail

- Module: Service Ticket
- Purpose: Display ticket details, progress, assignment, and action controls.
- Accessible Roles: Customer Service, Teknisi, IT.
- Route (recommended): `/tickets/{id}`
- Breadcrumb: Dashboard / Tickets / Ticket Detail
- Page Layout: Header with summary, detail sections, tabs for progress and attachments.
- Header: Ticket number, status badge, assigned technician, last update.
- Toolbar: Edit Ticket, Print Receipt, Request Cancellation, Add Progress.
- Action Buttons: Send to Technician, Start Service, Finish Service, Print.
- Search: Optional search within progress or part lists.
- Filter: Optional status filter in progress timeline.
- Table: Ticket parts and activity history tables.
- Cards: Summary cards for customer, device, service progress, warranty.
- Forms: Inline action forms for progress updates and approvals.
- Tabs: Overview, Progress History, Evidence, Warranty, Notes.
- Modal Dialogs: ConfirmationModal for status transitions, delete evidence, cancel request.
- Sidebar Behaviour: Standard.
- Status Badge: Current ticket state and priority.
- Empty State: Show placeholder in history or evidence tabs when no records exist.
- Loading State: Content skeleton and loading panel.
- Validation Messages: Inline messages for progress inputs and approval decisions.
- Navigation Flow: Ticket Detail → Edit Ticket / Create Progress / Print / back to Ticket List.
- Business Rules: Assignments and status changes must follow business flow; technician cannot cancel ticket; IT approves cancellations.
- Related Database Tables: `tickets`, `ticket_progresses`, `ticket_photos`, `ticket_parts`, `ticket_cancellations`, `ticket_warranties`, `customers`, `employees`.
- Related Components: PageHeader, Tabs, Timeline, InfoCard, StatusBadge, ConfirmationModal, LoadingSpinner.

## Ticket Edit

- Module: Service Ticket
- Purpose: Update ticket details or service metadata.
- Accessible Roles: Customer Service, IT (limited edits), Technician (progress-only edits).
- Route (recommended): `/tickets/{id}/edit`
- Breadcrumb: Dashboard / Tickets / Ticket Detail / Edit
- Page Layout: Structured form with sections for customer, device, service, and additional notes.
- Header: Page title and edit guidance.
- Toolbar: Save changes, cancel.
- Action Buttons: Update, Cancel.
- Search: Optional customer lookup.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form section cards.
- Forms: Editable ticket fields with conditional sections.
- Tabs: Optional General / Service / Notes tabs.
- Modal Dialogs: Confirm cancel if unsaved changes.
- Sidebar Behaviour: Standard.
- Status Badge: Display ticket state prominently.
- Empty State: Not applicable.
- Loading State: Save button feedback.
- Validation Messages: Required field validation and business rule warnings.
- Navigation Flow: Edit Ticket → save → Ticket Detail; cancel → Ticket Detail.
- Business Rules: Technician can update progress but not change core customer/device data; CS can update ticket metadata; IT can make system-level edits.
- Related Database Tables: `tickets`, `ticket_parts`, `employees`.
- Related Components: FormInput, FormTextarea, FormSelect, PrimaryButton, ValidationMessage.

## Ticket Diagnosis / Progress Service

- Module: Service Ticket
- Purpose: Capture technician diagnosis, progress updates, and service status transitions.
- Accessible Roles: Teknisi.
- Route (recommended): `/tickets/{id}/diagnosis`, `/tickets/{id}/progress`
- Breadcrumb: Dashboard / Tickets / Ticket Detail / Diagnosis
- Page Layout: Detail summary with diagnosis form, evidence upload, and progress timeline.
- Header: Ticket title and current status.
- Toolbar: Update progress, start service, complete service.
- Action Buttons: Save Progress, Upload Evidence, Request Sparepart.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Optional progress entry list.
- Cards: Diagnosis facts and service summary.
- Forms: Symptoms, findings, parts required, estimated completion, approval note.
- Tabs: Progress, Evidence, Parts.
- Modal Dialogs: Status transition confirmation.
- Sidebar Behaviour: Standard.
- Status Badge: Diagnosis and in-progress state.
- Empty State: Show instruction when no progress exists.
- Loading State: Spinner on action buttons.
- Validation Messages: Required fields for diagnosis and service notes.
- Navigation Flow: Diagnosis → save → Ticket Detail; finish service → Ticket Detail.
- Business Rules: Technician cannot begin service before customer approval; progress entries must be recorded with timestamps.
- Related Database Tables: `ticket_progresses`, `ticket_photos`, `ticket_parts`, `tickets`.
- Related Components: Timeline, FormTextarea, File Upload, PrimaryButton.

## Ticket Cancellation Request

- Module: Service Ticket
- Purpose: Capture and submit ticket cancellation requests.
- Accessible Roles: Customer Service, IT (approval).
- Route (recommended): `/tickets/{id}/cancel-request`
- Breadcrumb: Dashboard / Tickets / Ticket Detail / Cancel Request
- Page Layout: Form page with required rationale and supporting evidence.
- Header: Page title and guidance.
- Toolbar: Submit request, cancel.
- Action Buttons: Submit, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Ticket summary card.
- Forms: Reason, evidence attachments, customer communication notes.
- Tabs: Not applicable.
- Modal Dialogs: Confirmation before submitting request.
- Sidebar Behaviour: Standard.
- Status Badge: Request pending approval.
- Empty State: Not applicable.
- Loading State: Submit button spinner.
- Validation Messages: Required reason and evidence conditions.
- Navigation Flow: Submit request → Ticket Detail or request status screen.
- Business Rules: Technician cannot cancel; IT must approve cancellation.
- Related Database Tables: `ticket_cancellations`, `tickets`, `ticket_photos`.
- Related Components: FormTextarea, File Upload, PrimaryButton, ConfirmationModal.

## Ticket Print Receipt

- Module: Service Ticket
- Purpose: Provide a printable receipt or service summary at ticket creation or completion.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/tickets/{id}/print`
- Breadcrumb: Dashboard / Tickets / Ticket Detail / Print
- Page Layout: Print-ready header, ticket details, customer summary, price breakdown.
- Header: Print title and ticket summary.
- Toolbar: Print action, back.
- Action Buttons: Print, Close.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Parts and service cost breakdown table.
- Cards: Summary card with totals.
- Forms: Not applicable.
- Tabs: Not applicable.
- Modal Dialogs: Not applicable.
- Sidebar Behaviour: Sidebar may hide in print preview.
- Status Badge: Ticket status and payment status.
- Empty State: Not applicable.
- Loading State: Print generation indicator.
- Validation Messages: Not applicable.
- Navigation Flow: Print → back to Ticket Detail.
- Business Rules: The receipt should reflect approved service and any payment conditions.
- Related Database Tables: `tickets`, `ticket_parts`, `customers`, `sales`.
- Related Components: Badge, DataTable, PrimaryButton.

---

# Inventory Management

## Inventory Overview

- Module: Inventory Management
- Purpose: Provide a quick view of stock health, low-stock alerts, and inventory metrics.
- Accessible Roles: Admin Gudang, IT, Kepala Toko.
- Route (recommended): `/inventory`
- Breadcrumb: Dashboard / Inventory
- Page Layout: Summary cards, stock charts, low-stock warnings, and doorway cards for inventory operations.
- Header: Page title and overview subtitle.
- Toolbar: Refresh, add stock, view stock movement.
- Action Buttons: Add Product, Stock Adjustment, Stock Opname.
- Search: Optional global search for inventory items.
- Filter: Optional status or category filters for overview cards.
- Table: Not required on overview, but may include summary list.
- Cards: Stock Badge, Low Stock Warning, Purchase Summary Card, Stock Movement Card.
- Forms: Not applicable.
- Tabs: Optional for stock health, movement, and purchase summaries.
- Modal Dialogs: Confirmation for low stock reorder suggestions.
- Sidebar Behaviour: Standard.
- Status Badge: Stock availability state.
- Empty State: Show message when no inventory exists and highlight add product action.
- Loading State: Card skeletons and spinner.
- Validation Messages: Not applicable.
- Navigation Flow: Overview → Stock List, Supplier, Stock Movement.
- Business Rules: The overview should reflect current stock levels and operational alerts.
- Related Database Tables: `products`, `stock_movements`, `suppliers`, `purchase_transactions`.
- Related Components: StatisticCard, StockBadge, LowStockWarning, StockMovementCard, PurchaseSummaryCard.

## Product List / Stock List

- Module: Inventory Management
- Purpose: List inventory items with stock quantities, statuses, and actions.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/products`
- Breadcrumb: Dashboard / Inventory / Products
- Page Layout: Search and filter toolbar above responsive table.
- Header: Page title and inventory count.
- Toolbar: Add Product, refresh, export, filter.
- Action Buttons: Add Product, View, Edit, Stock Movement.
- Search: Prominent search for product name, SKU, supplier.
- Filter: Category, stock level, supplier, status.
- Table: Row number, product name, SKU, stock badge, status, updated date, actions.
- Cards: Optional top metrics for total products, low stock, reorder count.
- Forms: Search/filter controls.
- Tabs: Optional product categories.
- Modal Dialogs: ConfirmationModal for delete or deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: In stock, low stock, out of stock.
- Empty State: Prompt to add first product.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Products → Product Detail, Product Create.
- Business Rules: Stock badges should update based on current quantity thresholds.
- Related Database Tables: `products`, `categories`, `suppliers`, `stock_movements`.
- Related Components: DataTable, SearchBar, FilterPanel, StatusBadge, Pagination.

## Product Create

- Module: Inventory Management
- Purpose: Add a new inventory product.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/products/create`
- Breadcrumb: Dashboard / Inventory / Products / Add Product
- Page Layout: Form page with product and supplier details.
- Header: Page title and instructions.
- Toolbar: Save, cancel.
- Action Buttons: Save Product, Cancel.
- Search: Supplier lookup within form.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Product details card and purchasing card.
- Forms: Name, SKU, category, supplier, base price, stock quantity, reorder level.
- Tabs: Optional General / Stock / Supplier tabs.
- Modal Dialogs: Cancel confirmation.
- Sidebar Behaviour: Standard.
- Status Badge: Product status selection if active/inactive.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Required fields and numeric validation for prices and quantities.
- Navigation Flow: Create Product → save → Product Detail or list.
- Business Rules: New products may require supplier assignment and reorder threshold.
- Related Database Tables: `products`, `categories`, `suppliers`.
- Related Components: FormInput, FormSelect, PrimaryButton, ValidationMessage.

## Product Detail

- Module: Inventory Management
- Purpose: Display product details, stock movement, and related purchase history.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/products/{id}`
- Breadcrumb: Dashboard / Inventory / Products / Product Detail
- Page Layout: Summary header, stock details sections, movement list, purchase summary.
- Header: Product name, SKU, category, status badge.
- Toolbar: Edit Product, Stock Adjustment, Add Stock, Print.
- Action Buttons: Edit, Add Stock, Stock Movement.
- Search: Optional search in movement table.
- Filter: Date range or movement type filter.
- Table: Stock movement and purchase history tables.
- Cards: Current stock card, supplier card, reorder level card.
- Forms: Not applicable.
- Tabs: Overview, Stock Movement, Purchase History.
- Modal Dialogs: Confirmation for stock adjustments.
- Sidebar Behaviour: Standard.
- Status Badge: Stock state and product status.
- Empty State: Show placeholder if no movement history.
- Loading State: Content skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Product Detail → Edit Product, Stock Adjustment.
- Business Rules: Stock movement must calculate current quantity and reflect supplier receipts.
- Related Database Tables: `products`, `stock_movements`, `purchase_transactions`, `suppliers`.
- Related Components: InfoCard, DataTable, StatusBadge, Tabs.

## Stock Entry / Barang Masuk

- Module: Inventory Management
- Purpose: Record incoming stock receipts and update inventory levels.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/stock-in`
- Breadcrumb: Dashboard / Inventory / Stock Entry
- Page Layout: Form page with product selection, supplier, quantity, and notes.
- Header: Page title and instruction.
- Toolbar: Save, cancel.
- Action Buttons: Record Stock, Cancel.
- Search: Product lookup.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Summary card of item selected.
- Forms: Product, supplier, quantity, received date, notes.
- Tabs: Not applicable.
- Modal Dialogs: Confirmation on submit.
- Sidebar Behaviour: Standard.
- Status Badge: Not applicable.
- Empty State: Not applicable.
- Loading State: Submit spinner.
- Validation Messages: Required quantity and supplier.
- Navigation Flow: Record Stock → Inventory Overview or Product Detail.
- Business Rules: Stock receipts increment product quantity and record movement.
- Related Database Tables: `stock_movements`, `products`, `suppliers`.
- Related Components: FormSelect, PrimaryButton, ValidationMessage.

## Stock Adjustment

- Module: Inventory Management
- Purpose: Adjust stock counts for corrections or stocktaking.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/stock-adjustment`
- Breadcrumb: Dashboard / Inventory / Stock Adjustment
- Page Layout: Form with current stock, adjustment quantity, reason.
- Header: Page title and instruction.
- Toolbar: Save, cancel.
- Action Buttons: Adjust Stock, Cancel.
- Search: Product lookup.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Current stock summary.
- Forms: Product, current stock, new quantity, reason.
- Tabs: Not applicable.
- Modal Dialogs: Confirmation before update.
- Sidebar Behaviour: Standard.
- Status Badge: Not applicable.
- Empty State: Not applicable.
- Loading State: Submit spinner.
- Validation Messages: Required reason and valid quantity values.
- Navigation Flow: Adjust Stock → Product Detail or Inventory Overview.
- Business Rules: Adjustments must record reason and update stock movements.
- Related Database Tables: `stock_movements`, `products`.
- Related Components: FormInput, FormTextarea, PrimaryButton.

## Stock Opname

- Module: Inventory Management
- Purpose: Conduct periodic stock taking and reconcile actual quantities.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/inventory/stock-opname`
- Breadcrumb: Dashboard / Inventory / Stock Opname
- Page Layout: Table of products with expected vs counted quantities and reconciliation actions.
- Header: Page title and instructions.
- Toolbar: Start Count, Save Adjustments, export.
- Action Buttons: Save Count, Cancel.
- Search: Search product names or SKU.
- Filter: Category, location.
- Table: Product list with expected quantity, actual count, difference.
- Cards: Summary cards for adjustments needed and total variance.
- Forms: Inline count fields in table.
- Tabs: Not applicable.
- Modal Dialogs: Confirm final reconciliation.
- Sidebar Behaviour: Standard.
- Status Badge: Low variance, overstock, shortage.
- Empty State: No products found placeholder.
- Loading State: Table skeleton.
- Validation Messages: Required count values.
- Navigation Flow: Stock Opname → Save → Inventory Overview.
- Business Rules: Stock opname adjustments update inventory records and require reconciliation comments.
- Related Database Tables: `products`, `stock_movements`.
- Related Components: DataTable, FormInput, PrimaryButton, StatusBadge.

## Request Sparepart

- Module: Inventory Management
- Purpose: Submit sparepart requests for unavailable items.
- Accessible Roles: Admin Gudang, Teknisi.
- Route (recommended): `/inventory/request-sparepart`
- Breadcrumb: Dashboard / Inventory / Request Sparepart
- Page Layout: Request form with product selection, quantity, requester details, and approval status.
- Header: Page title and instructions.
- Toolbar: Submit request, cancel.
- Action Buttons: Request Sparepart, Cancel.
- Search: Product filter.
- Filter: Request status filter.
- Table: Optional current request list.
- Cards: Request summary.
- Forms: Product, quantity, requester, reason.
- Tabs: Active requests / history.
- Modal Dialogs: Confirmation on submit.
- Sidebar Behaviour: Standard.
- Status Badge: Requested, approved, fulfilled.
- Empty State: Encourage first request.
- Loading State: Spinner on submit.
- Validation Messages: Required fields and quantity validation.
- Navigation Flow: Request Sparepart → detail or list.
- Business Rules: Requests are fulfilled by inventory team and recorded in stock movements.
- Related Database Tables: `products`, `stock_movements`, `users`, `suppliers`.
- Related Components: FormSelect, Button, StatusBadge, DataTable.

---

# Supplier Management

## Supplier List

- Module: Supplier Management
- Purpose: Manage supplier records and allow quick access to supplier details.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/suppliers`
- Breadcrumb: Dashboard / Suppliers
- Page Layout: List view with search, filters, and supplier table.
- Header: Page title and supplier count.
- Toolbar: Add Supplier, refresh, filter.
- Action Buttons: Add Supplier, view, edit, delete.
- Search: Name, contact, category.
- Filter: Region, status, active/inactive.
- Table: Supplier name, contact, product categories, status, actions.
- Cards: Optional supplier metrics.
- Forms: Search and filter controls.
- Tabs: Optional active/inactive suppliers.
- Modal Dialogs: ConfirmationModal for deletion.
- Sidebar Behaviour: Standard.
- Status Badge: Active, inactive.
- Empty State: Prompt to add first supplier.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Supplier List → Supplier Detail / Create Supplier.
- Business Rules: Supplier data should be consistent with purchase records.
- Related Database Tables: `suppliers`, `purchase_transactions`.
- Related Components: DataTable, SearchBar, FilterPanel, ConfirmationModal.

## Supplier Create

- Module: Supplier Management
- Purpose: Add new supplier details.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/suppliers/create`
- Breadcrumb: Dashboard / Suppliers / Add Supplier
- Page Layout: Form page with supplier contact and business details.
- Header: Page title and field instructions.
- Toolbar: Save, cancel.
- Action Buttons: Save Supplier, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Summary card.
- Forms: Name, phone, email, address, category, notes.
- Tabs: Not applicable.
- Modal Dialogs: Cancel confirmation.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive toggle.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Required contact details and valid email.
- Navigation Flow: Create Supplier → save → Supplier Detail or list.
- Business Rules: Supplier record should be created before purchase transactions.
- Related Database Tables: `suppliers`, `purchase_transaction_items`.
- Related Components: FormInput, PrimaryButton, ValidationMessage.

## Supplier Detail

- Module: Supplier Management
- Purpose: Show supplier profile and purchase history.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/suppliers/{id}`
- Breadcrumb: Dashboard / Suppliers / Supplier Detail
- Page Layout: Header with supplier summary, purchase history table, and tabs.
- Header: Supplier name, contact info, primary action.
- Toolbar: Edit, add purchase, print.
- Action Buttons: Edit Supplier, Add Purchase.
- Search: Purchase history search.
- Filter: Date range and purchase status.
- Table: Purchase history list.
- Cards: Summary card for supplier status and totals.
- Forms: Not applicable.
- Tabs: Overview, Purchase History.
- Modal Dialogs: Confirm deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive.
- Empty State: Placeholder when no purchase history exists.
- Loading State: Page-level skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Supplier Detail → Edit → save → Supplier Detail.
- Business Rules: Supplier details may be referenced by inventory and purchase flows.
- Related Database Tables: `suppliers`, `purchase_transactions`, `purchase_transaction_items`.
- Related Components: InfoCard, DataTable, StatusBadge.

## Supplier Edit

- Module: Supplier Management
- Purpose: Update supplier information.
- Accessible Roles: Admin Gudang, IT.
- Route (recommended): `/suppliers/{id}/edit`
- Breadcrumb: Dashboard / Suppliers / Supplier Detail / Edit
- Page Layout: Form page with pre-filled supplier fields.
- Header: Page title and current supplier name.
- Toolbar: Save, cancel.
- Action Buttons: Update, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form card.
- Forms: Editable supplier fields.
- Tabs: Not applicable.
- Modal Dialogs: Cancel confirmation.
- Sidebar Behaviour: Standard.
- Status Badge: Display active status.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Inline validation for required data.
- Navigation Flow: Edit → save → Supplier Detail; cancel → Supplier Detail.
- Business Rules: Edits must preserve purchase history integrity.
- Related Database Tables: `suppliers`.
- Related Components: FormInput, PrimaryButton, ValidationMessage.

---

# Direct Sales (POS)

## Sales Transaction

- Module: Direct Sales (POS)
- Purpose: Create a new point-of-sale invoice for direct product sales.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/sales/create`
- Breadcrumb: Dashboard / Direct Sales / Create Invoice
- Page Layout: Split form with product selection, cart summary, payment details, and totals.
- Header: Page title and cashier context.
- Toolbar: Save invoice, reset cart.
- Action Buttons: Submit Sale, Cancel.
- Search: Product search input.
- Filter: Optional category filter for product selection.
- Table: Cart items table, invoice line items.
- Cards: Payment summary, customer summary, totals card.
- Forms: Product selection, quantity, discount, payment method, customer info.
- Tabs: Optional Product / Payment / Summary tabs.
- Modal Dialogs: confirmation before final sale or cancel.
- Sidebar Behaviour: Standard.
- Status Badge: Payment status in summary.
- Empty State: Prompt to add products to cart.
- Loading State: Spinner during invoice submission.
- Validation Messages: Required payment fields and item quantity.
- Navigation Flow: Create Invoice → save → Invoice Detail or Sales History.
- Business Rules: Invoice must record stock outflow and payment details; direct sales bypass ticket flow.
- Related Database Tables: `sales`, `sale_items`, `products`, `customers`, `stock_movements`.
- Related Components: DataTable, FormInput, PrimaryButton, StatusBadge.

## Sales History

- Module: Direct Sales (POS)
- Purpose: List completed direct sales invoices.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/sales`
- Breadcrumb: Dashboard / Direct Sales / Sales History
- Page Layout: Search and filter toolbar above invoice table.
- Header: Page title and totals summary.
- Toolbar: Print, export, refresh.
- Action Buttons: View Invoice, Print.
- Search: Invoice number, customer name, product.
- Filter: Date range, payment status.
- Table: Invoice number, customer, total, payment status, date, actions.
- Cards: Total sales summary card.
- Forms: Search/filter controls.
- Tabs: Optional All / Paid / Pending.
- Modal Dialogs: Print confirmation or success.
- Sidebar Behaviour: Standard.
- Status Badge: Paid, pending, void.
- Empty State: Call to action to create a new sale.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Sales History → Invoice Detail.
- Business Rules: Sales list should reflect completed direct sales only.
- Related Database Tables: `sales`, `sale_items`, `customers`.
- Related Components: DataTable, SearchBar, StatusBadge, Pagination.

## Invoice Detail

- Module: Direct Sales (POS)
- Purpose: Show invoice details for printing, payment verification, and record review.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/sales/{id}`
- Breadcrumb: Dashboard / Direct Sales / Sales History / Invoice Detail
- Page Layout: Invoice header, itemized table, payment summary, customer details.
- Header: Invoice number, status badge, date.
- Toolbar: Print Invoice, Back to Sales History.
- Action Buttons: Print, Close.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Line items, quantity, price, totals.
- Cards: Payment summary, customer summary.
- Forms: Not applicable.
- Tabs: Optional Invoice / Payments sections.
- Modal Dialogs: Print preview.
- Sidebar Behaviour: Standard.
- Status Badge: Invoice status.
- Empty State: Not applicable.
- Loading State: Page skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Invoice Detail → Sales History.
- Business Rules: Invoice should accurately reflect product stock movement and payment status.
- Related Database Tables: `sales`, `sale_items`, `products`, `customers`.
- Related Components: DataTable, Badge.

## Invoice Print

- Module: Direct Sales (POS)
- Purpose: Provide a printer-friendly invoice layout.
- Accessible Roles: Customer Service, IT.
- Route (recommended): `/sales/{id}/print`
- Breadcrumb: Dashboard / Direct Sales / Invoice Detail / Print
- Page Layout: Print-ready format with invoice header and totals.
- Header: Invoice title and reference.
- Toolbar: Print action, back.
- Action Buttons: Print.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Itemized invoice table.
- Cards: Summary totals card.
- Forms: Not applicable.
- Tabs: Not applicable.
- Modal Dialogs: Not applicable.
- Sidebar Behaviour: Sidebar hidden in print layout.
- Status Badge: Invoice status if relevant.
- Empty State: Not applicable.
- Loading State: Print generation indicator if required.
- Validation Messages: Not applicable.
- Navigation Flow: Print → back to Invoice Detail.
- Business Rules: Print layout must be clean and compatible with physical invoices.
- Related Database Tables: `sales`, `sale_items`, `products`.
- Related Components: Badge, DataTable.

---

# Operational Expense

## Expense List

- Module: Operational Expense
- Purpose: List operational expenses and support expense management.
- Accessible Roles: Kepala Toko, IT.
- Route (recommended): `/expenses`
- Breadcrumb: Dashboard / Operational Expense
- Page Layout: Search/filter toolbar above expense table.
- Header: Page title and total expense summary.
- Toolbar: Add Expense, refresh, export.
- Action Buttons: Add Expense, view, edit, delete.
- Search: Expense name, vendor, category.
- Filter: Date range, category, amount range.
- Table: Expense name, amount, category, date, status, actions.
- Cards: Expense totals and category breakdown.
- Forms: Search/filter controls.
- Tabs: Optional by category.
- Modal Dialogs: ConfirmationModal for delete.
- Sidebar Behaviour: Standard.
- Status Badge: Pending, approved, paid.
- Empty State: Prompt to add first expense.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Expense List → Expense Detail / Add Expense.
- Business Rules: Expense records should be categorized and date-stamped.
- Related Database Tables: `operational_expenses`, `expense_categories`.
- Related Components: DataTable, FilterPanel, StatusBadge, ConfirmationModal.

## Expense Create

- Module: Operational Expense
- Purpose: Record a new operational expense.
- Accessible Roles: Kepala Toko, IT.
- Route (recommended): `/expenses/create`
- Breadcrumb: Dashboard / Operational Expense / Add Expense
- Page Layout: Standard expense entry form.
- Header: Page title and instructions.
- Toolbar: Save, cancel.
- Action Buttons: Save Expense, Cancel.
- Search: Optional vendor lookup.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Summary of totals.
- Forms: Date, category, amount, vendor, notes.
- Tabs: Not applicable.
- Modal Dialogs: Confirm cancellation.
- Sidebar Behaviour: Standard.
- Status Badge: Expense type indicator.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Required amount and category.
- Navigation Flow: Add Expense → save → Expense Detail or list.
- Business Rules: Expenses must be assigned to categories and contain valid amounts.
- Related Database Tables: `operational_expenses`, `expense_categories`.
- Related Components: FormInput, FormSelect, PrimaryButton, ValidationMessage.

## Expense Detail

- Module: Operational Expense
- Purpose: Display expense details and supporting information.
- Accessible Roles: Kepala Toko, IT.
- Route (recommended): `/expenses/{id}`
- Breadcrumb: Dashboard / Operational Expense / Expense Detail
- Page Layout: Detail summary with expense fields and history.
- Header: Expense title, amount, date.
- Toolbar: Edit, delete.
- Action Buttons: Edit Expense, Back to List.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Summary card with expense breakdown.
- Forms: Read-only information.
- Tabs: Optional Notes / History.
- Modal Dialogs: Confirmation for delete.
- Sidebar Behaviour: Standard.
- Status Badge: Approved or pending.
- Empty State: Not applicable.
- Loading State: Content skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Expense Detail → Edit → save → Expense Detail.
- Business Rules: Expense detail should link to report summaries.
- Related Database Tables: `operational_expenses`, `expense_categories`.
- Related Components: InfoCard, PrimaryButton.

## Expense Edit

- Module: Operational Expense
- Purpose: Update an existing expense record.
- Accessible Roles: Kepala Toko, IT.
- Route (recommended): `/expenses/{id}/edit`
- Breadcrumb: Dashboard / Operational Expense / Expense Detail / Edit
- Page Layout: Form with pre-filled expense fields.
- Header: Page title and subtitle.
- Toolbar: Save, cancel.
- Action Buttons: Update, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form card.
- Forms: Editable expense fields.
- Tabs: Not applicable.
- Modal Dialogs: Confirm cancel if changes unsaved.
- Sidebar Behaviour: Standard.
- Status Badge: Expense category as label.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Inline validation for amounts and required fields.
- Navigation Flow: Edit Expense → save → Expense Detail; cancel → Expense Detail.
- Business Rules: Editing must preserve expense history and category classification.
- Related Database Tables: `operational_expenses`.
- Related Components: FormInput, PrimaryButton, ValidationMessage.

---

# Monitoring & Reports

## Monitoring Dashboard

- Module: Monitoring & Reports
- Purpose: Provide real-time operational and KPI monitoring.
- Accessible Roles: IT, Kepala Toko, Admin Gudang.
- Route (recommended): `/monitoring`
- Breadcrumb: Dashboard / Monitoring
- Page Layout: Dashboard cards, charts, status panels, key alerts.
- Header: Page title and summary.
- Toolbar: Refresh data, filter date range.
- Action Buttons: View Details, Export.
- Search: Not applicable.
- Filter: Date range, module type.
- Table: Optional summary list of alert conditions.
- Cards: StatisticCard, NotificationCard, ChartCard.
- Forms: Filter panel only.
- Tabs: Optional Ticket Monitoring, Inventory Monitoring, KPI Monitoring.
- Modal Dialogs: Not applicable.
- Sidebar Behaviour: Standard.
- Status Badge: Alert severity and trend.
- Empty State: Show fallback when monitoring data is unavailable.
- Loading State: Dashboard skeletons.
- Validation Messages: Not applicable.
- Navigation Flow: Monitoring Dashboard → module-specific reports.
- Business Rules: Monitoring must display live status and recent alerts.
- Related Database Tables: `tickets`, `products`, `stock_movements`, `operational_expenses`, `sales`.
- Related Components: StatisticCard, ChartCard, NotificationCard.

## Reports List

- Module: Monitoring & Reports
- Purpose: List available report types and export options.
- Accessible Roles: IT, Kepala Toko.
- Route (recommended): `/reports`
- Breadcrumb: Dashboard / Reports
- Page Layout: Cards or list of report categories with filters.
- Header: Page title and report purpose.
- Toolbar: Export, refresh.
- Action Buttons: Open report, download.
- Search: Report name search.
- Filter: Report category, date range.
- Table: Optional list of recent reports.
- Cards: Report summary cards.
- Forms: Search/filter controls.
- Tabs: Optional by report category.
- Modal Dialogs: Export confirmation.
- Sidebar Behaviour: Standard.
- Status Badge: Report status or freshness.
- Empty State: Prompt to run a report.
- Loading State: Cards skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Reports → Report Detail.
- Business Rules: Reports should align with monitoring KPIs.
- Related Database Tables: `tickets`, `sales`, `products`, `operational_expenses`.
- Related Components: Cards, FilterPanel, Pagination.

## Report Detail

- Module: Monitoring & Reports
- Purpose: Show detailed report data and export controls.
- Accessible Roles: IT, Kepala Toko.
- Route (recommended): `/reports/{id}`
- Breadcrumb: Dashboard / Reports / Report Detail
- Page Layout: Report header, filters, charts, summary table.
- Header: Report title and timeframe.
- Toolbar: Export, back.
- Action Buttons: Download PDF, Export CSV.
- Search: Optional within report table.
- Filter: Date range and segment.
- Table: Report data table.
- Cards: Summary metrics.
- Forms: Filter controls.
- Tabs: Optional metrics tabs.
- Modal Dialogs: Confirm export.
- Sidebar Behaviour: Standard.
- Status Badge: Report update state.
- Empty State: Placeholder when no result.
- Loading State: Table and chart skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Report Detail → Reports.
- Business Rules: Report results should reflect selected filters and date range.
- Related Database Tables: `tickets`, `sales`, `products`, `operational_expenses`.
- Related Components: ChartCard, DataTable, Card, FilterPanel.

---

# User Management

## User List

- Module: User Management
- Purpose: Display all system users and provide account management controls.
- Accessible Roles: IT.
- Route (recommended): `/users`
- Breadcrumb: Dashboard / User Management
- Page Layout: Search and filter toolbar above user table.
- Header: Page title and total users count.
- Toolbar: Add User, refresh, filter.
- Action Buttons: Add User, view, edit, deactivate.
- Search: Name, email, role.
- Filter: Role, status, department.
- Table: User name, role, status, last login, actions.
- Cards: Optional user metrics.
- Forms: Search/filter controls.
- Tabs: Active / Inactive tabs.
- Modal Dialogs: ConfirmationModal for deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: Active, inactive.
- Empty State: Prompt to add first user.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: User List → User Detail / Create User.
- Business Rules: Only IT can manage users and roles.
- Related Database Tables: `users`, `roles`, `role_user`, `employees`.
- Related Components: DataTable, SearchBar, StatusBadge, ConfirmationModal.

## User Create

- Module: User Management
- Purpose: Create a new system user and assign role permissions.
- Accessible Roles: IT.
- Route (recommended): `/users/create`
- Breadcrumb: Dashboard / User Management / Add User
- Page Layout: Form page with user profile and role assignment.
- Header: Page title and instructions.
- Toolbar: Save, cancel.
- Action Buttons: Create User, Cancel.
- Search: Role lookup if needed.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Summary card of account settings.
- Forms: Name, email, password, role, employee association, status.
- Tabs: Account Info / Permissions.
- Modal Dialogs: Confirm cancel.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive account.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Required fields, password strength, unique email.
- Navigation Flow: Create User → save → User Detail or list.
- Business Rules: User creation must assign a role and enforce unique email.
- Related Database Tables: `users`, `roles`, `role_user`, `employees`.
- Related Components: FormInput, FormSelect, PrimaryButton, ValidationMessage.

## User Detail

- Module: User Management
- Purpose: Display user account details, role assignments, and activity status.
- Accessible Roles: IT.
- Route (recommended): `/users/{id}`
- Breadcrumb: Dashboard / User Management / User Detail
- Page Layout: Header with account summary, permissions panel, activity timeline.
- Header: User name, role, status badge.
- Toolbar: Edit User, reset password, deactivate.
- Action Buttons: Edit, Deactivate.
- Search: Optional activity search.
- Filter: Not applicable.
- Table: Optional activity or login history.
- Cards: Account summary, role permissions.
- Forms: Read-only fields.
- Tabs: Profile, Permissions, Activity.
- Modal Dialogs: Confirmation for deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive.
- Empty State: Placeholder when no activity.
- Loading State: Skeleton sections.
- Validation Messages: Not applicable.
- Navigation Flow: User Detail → Edit User.
- Business Rules: User details should reflect current role assignments and status.
- Related Database Tables: `users`, `roles`, `role_user`, `audit_logs`.
- Related Components: InfoCard, StatusBadge, Tabs.

## User Edit

- Module: User Management
- Purpose: Update a user account and role permissions.
- Accessible Roles: IT.
- Route (recommended): `/users/{id}/edit`
- Breadcrumb: Dashboard / User Management / User Detail / Edit
- Page Layout: Form page with editable account fields.
- Header: Page title and role context.
- Toolbar: Save, cancel.
- Action Buttons: Update, Cancel.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Not applicable.
- Cards: Form card.
- Forms: Editable fields for name, email, role, status.
- Tabs: Account / Permissions.
- Modal Dialogs: Confirm cancel if unsaved changes.
- Sidebar Behaviour: Standard.
- Status Badge: Current account status.
- Empty State: Not applicable.
- Loading State: Save spinner.
- Validation Messages: Inline validation for required/unique fields.
- Navigation Flow: Edit User → save → User Detail; cancel → User Detail.
- Business Rules: Changes must preserve audit trail and login access.
- Related Database Tables: `users`, `roles`, `role_user`.
- Related Components: FormInput, FormSelect, PrimaryButton, ValidationMessage.

## Role & Permission Management

- Module: User Management
- Purpose: Define roles and their permissions in the system.
- Accessible Roles: IT.
- Route (recommended): `/roles`
- Breadcrumb: Dashboard / User Management / Roles & Permissions
- Page Layout: Role list, permission matrix, role detail panel.
- Header: Page title and summary.
- Toolbar: Add Role, refresh.
- Action Buttons: Create Role, edit permissions.
- Search: Role name search.
- Filter: Permission category filter.
- Table: Role name, description, assigned users.
- Cards: Permission summary.
- Forms: Not applicable except in create/edit flows.
- Tabs: Roles / Permissions.
- Modal Dialogs: Confirm permission changes.
- Sidebar Behaviour: Standard.
- Status Badge: Role active/inactive.
- Empty State: Prompt to create first role if none exist.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Roles → Role Detail / Create Role.
- Business Rules: Role changes must update access immediately and preserve audit data.
- Related Database Tables: `roles`, `permissions`, `role_user`.
- Related Components: DataTable, FilterPanel, StatusBadge.

## Employee Management

- Module: User Management
- Purpose: Manage employee profiles that may be linked to system users.
- Accessible Roles: IT.
- Route (recommended): `/employees`
- Breadcrumb: Dashboard / User Management / Employees
- Page Layout: List of employees with search and filter.
- Header: Page title and employee count.
- Toolbar: Add Employee, refresh.
- Action Buttons: Add, view, edit.
- Search: Name, ID, department.
- Filter: Department, role.
- Table: Employee name, role, department, status, actions.
- Cards: Optional staff counts.
- Forms: Search/filter controls.
- Tabs: Active / Inactive.
- Modal Dialogs: Confirm deactivation.
- Sidebar Behaviour: Standard.
- Status Badge: Active/inactive.
- Empty State: Prompt to add employees.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Employees → Employee Detail / Create Employee.
- Business Rules: Employee records may be linked to user accounts and roles.
- Related Database Tables: `employees`, `users`, `roles`.
- Related Components: DataTable, SearchBar, StatusBadge.

---

# Audit Log

## Audit Log List

- Module: Audit Log
- Purpose: Display system audit events and support compliance review.
- Accessible Roles: IT.
- Route (recommended): `/audit-logs`
- Breadcrumb: Dashboard / Audit Log
- Page Layout: Search and filter toolbar above audit table.
- Header: Page title and event count.
- Toolbar: Export, refresh.
- Action Buttons: View, export.
- Search: Event type, user, object.
- Filter: Date range, user, module.
- Table: Timestamp, user, action, object, details, actions.
- Cards: Optional summary of event counts.
- Forms: Search/filter controls.
- Tabs: Optional by module or severity.
- Modal Dialogs: Not applicable.
- Sidebar Behaviour: Standard.
- Status Badge: Event severity.
- Empty State: Prompt if no events found.
- Loading State: Table skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Audit Log List → Audit Entry Detail.
- Business Rules: Audit log is immutable and should not allow edits.
- Related Database Tables: `audit_logs`, `users`, `roles`.
- Related Components: DataTable, SearchBar, FilterPanel.

## Audit Entry Detail

- Module: Audit Log
- Purpose: Show a single audit event with full details.
- Accessible Roles: IT.
- Route (recommended): `/audit-logs/{id}`
- Breadcrumb: Dashboard / Audit Log / Audit Entry Detail
- Page Layout: Detail summary card with event metadata and payload.
- Header: Event title, timestamp, user.
- Toolbar: Back to list.
- Action Buttons: Back.
- Search: Not applicable.
- Filter: Not applicable.
- Table: Optional metadata table.
- Cards: Audit event summary card.
- Forms: Read-only details.
- Tabs: Event details / metadata.
- Modal Dialogs: Not applicable.
- Sidebar Behaviour: Standard.
- Status Badge: Event type or severity.
- Empty State: Not applicable.
- Loading State: Content skeleton.
- Validation Messages: Not applicable.
- Navigation Flow: Audit Entry Detail → Audit Log List.
- Business Rules: Event detail should be read-only and complete.
- Related Database Tables: `audit_logs`, `users`.
- Related Components: InfoCard, StatusBadge.

---

# Global Screen Behaviors

## Breadcrumb Standard

- All non-root pages must display breadcrumb navigation.
- Breadcrumbs start at Dashboard and reflect page hierarchy.
- Current page appears as the final breadcrumb item.
- Breadcrumb links provide safe back navigation.

## Sidebar Behaviour

- Sidebar appears on all authenticated pages.
- Sidebar collapses on tablet and becomes drawer-based on mobile.
- Active module highlights the current page.
- Role-based sidebar items are visible only when permitted.

## Header and Toolbar

- Each page uses a Page Header with title and a concise subtitle.
- Toolbars group primary actions, filters, and global controls.
- Primary actions appear on the right side of the header toolbar.

## Empty State

- Every list page must define an empty state with a clear message and primary action.
- Use a standard empty-state card for zero results.

## Loading State

- Every page with asynchronous data should include a loading state.
- Use page skeletons or spinners to show progress.

## Validation Messages

- Validation messages appear inline near inputs.
- Use concise, actionable copy.
- Preserve form data when validation fails.

## Navigation Flow

- Save redirects to the relevant detail or list page.
- Cancel returns to the previous page without committing changes.
- Delete requires confirmation and returns to the list page.
- Print opens a printable view and returns to origin.
- Approval and rejection follow business rules and remain within module context.

---

# Summary

This Screen Specification defines every major page across FFixiT-MS modules, including authentication, dashboard, customer, service ticket, inventory, supplier, POS, expenses, monitoring, user management, and audit log. It provides frontend developers with clear page structure, navigation, business rules, data relationships, and reusable component expectations for consistent implementation.
