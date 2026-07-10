# Laravel Architecture

FFixiT Management System (FFixiT-MS)

---

## Document Information

| Item        | Value                                                  |
| ----------- | ------------------------------------------------------- |
| Version     | 1.0                                                      |
| Author      | AI Lead Laravel Architect (FFixiT-MS Project)            |
| Project     | FFixiT-MS                                                |
| Status      | Draft — Ready for Review                                 |

This document translates the FFixiT-MS documentation set (`README.md`, `BusinessFlow.md`, `Roles.md`, `Modules.md`, `Roadmap.md`, `ERD.md`, `AIInstructions.md`, `CodingStandards.md`, `UIGuidelines.md`, `DesignSystem.md`, `ComponentLibrary.md`, `UIFlow.md`, `ScreenSpecification.md`) into a concrete Laravel 12 architecture. It does not introduce new business rules, roles, modules, or database entities — every decision below traces back to an existing document, or to a Sprint 0 decision already approved by the project owner (2026-07-10), which this document treats as binding precedent.

This document is **architecture only** — no PHP, Blade, or migration code is included. It is the reference every future sprint's implementation must follow.

---

## Binding Decisions Carried Over From Sprint 0

These decisions were explicitly approved during Sprint 0 (Project Foundation) and are treated as fixed architectural constraints for the rest of the project, overriding what might otherwise be a "default" Laravel choice:

1. **No `roles` table, no `role_id` foreign key.** Roles are fixed (5 roles, per `Roles.md`) and implemented as a PHP backed enum (`App\Enums\UserRole`), stored as a single `role` string column on `users`.
2. **No third-party RBAC package** (e.g. Spatie Permission). Role checks are done with a small custom middleware comparing `UserRole`.
3. **No Repository Pattern.** The layering is strictly **Controller → Service → Model** (Eloquent). Controllers stay thin; Services hold business logic; Models stay focused on relationships/casts/scopes.
4. **No SPA behavior, no client-side component framework.** FFixiT-MS is server-rendered Laravel Blade with Bootstrap 5 and vanilla JavaScript progressive enhancement only, per `AIInstructions.md` Technology Stack. There is no Loading Skeleton or other SPA-style component.
5. **Sidebar always renders the full menu** for a role (per `DesignSystem.md` Section 8), even for modules not yet implemented — those items render disabled with a "Coming Soon" indicator instead of being omitted.
6. **No self-service Registration.** Per `ScreenSpecification.md` Module 1, accounts are created exclusively by IT through User Management (v0.2). There is no public `/register` route.

Any change to these six points requires the same explicit approval process as a documentation change, per `AIInstructions.md` ("If Something Is Missing").

---

## 1. Project Folder Structure

FFixiT-MS follows the standard Laravel 12 application skeleton. The structure below lists only the applica­tion-level (non-framework) folders and where each module's files live, since `CodingStandards.md` explicitly forbids restructuring the framework's default folders ("Ikuti struktur standar Laravel. Jangan mengubah struktur folder framework.").

```
ffixit-ms/
├── app/
│   ├── Enums/
│   │   └── UserRole.php                  (fixed 5-role enum — see RBAC Strategy)
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Auth/                     (Login, Forgot/Reset Password)
│   │   │   ├── Customer/                 (v0.4)
│   │   │   ├── Ticket/                   (v0.5 — one controller per sub-flow, see Route Organization)
│   │   │   ├── Inventory/                (v0.6 — Product, Category, StockIn, StockOpname, StockAdjustment)
│   │   │   ├── Supplier/                 (v0.6)
│   │   │   ├── Sales/                    (v0.7 — POS)
│   │   │   ├── Expense/                  (v0.8)
│   │   │   ├── Monitoring/               (v0.9 — read-only report controllers)
│   │   │   ├── UserManagement/           (v0.2 — User, Employee, Role&Permission)
│   │   │   ├── AuditLog/                 (v1.0)
│   │   │   └── DashboardController.php   (v0.3 — one controller, role-aware view data)
│   │   ├── Middleware/
│   │   │   └── EnsureUserHasRole.php
│   │   ├── Requests/
│   │   │   ├── Auth/
│   │   │   ├── Customer/
│   │   │   ├── Ticket/
│   │   │   ├── Inventory/
│   │   │   ├── Supplier/
│   │   │   ├── Sales/
│   │   │   ├── Expense/
│   │   │   └── UserManagement/
│   │   └── Resources/                    (JSON resources — used only if/when an internal API is needed, e.g. type-ahead search endpoints; see UIGuidelines/ComponentLibrary Searchable Select)
│   ├── Models/
│   │   (one Eloquent model per ERD entity — see MVC Architecture)
│   ├── Services/
│   │   (one Service class per business-logic-bearing module — see Service Layer Strategy)
│   ├── Policies/
│   │   (optional, only if a model-level authorization nuance doesn't fit the role middleware — see RBAC Strategy)
│   ├── View/
│   │   └── Components/
│   │       └── Sidebar.php               (class-based; all other Blade components are anonymous)
│   └── Providers/
│       └── AppServiceProvider.php
├── bootstrap/
│   └── app.php                           (middleware alias registration, exception rendering)
├── config/
│   └── (standard Laravel config; no custom config file is needed for roles since they live in the enum)
├── database/
│   ├── migrations/                       (see Database Migration Order)
│   ├── seeders/                          (see Seeder Order)
│   └── factories/                        (one factory per model, used by seeders and tests)
├── resources/
│   ├── sass/
│   │   └── app.scss                      (Bootstrap 5 + design tokens from DesignSystem.md)
│   ├── js/
│   │   └── app.js                        (vanilla JS progressive enhancement only)
│   └── views/
│       ├── components/
│       │   ├── layouts/                  (app.blade.php, guest.blade.php)
│       │   ├── (generic reusable atoms: button, alert, badge, modal, page-header, empty-state, ...)
│       │   ├── sidebar.blade.php / navbar.blade.php / footer.blade.php
│       │   └── (per-module component subfolders added as each module ships — see Blade Structure)
│       ├── auth/
│       ├── dashboard.blade.php
│       ├── customers/                    (v0.4)
│       ├── tickets/                      (v0.5)
│       ├── inventory/                    (v0.6)
│       ├── suppliers/                    (v0.6)
│       ├── sales/                        (v0.7)
│       ├── expenses/                     (v0.8)
│       ├── monitoring/                   (v0.9)
│       ├── users/, employees/, roles/    (v0.2)
│       ├── audit-logs/                   (v1.0)
│       └── errors/
│           ├── 403.blade.php
│           └── 404.blade.php
├── routes/
│   ├── web.php                           (root file — only Route::redirect + requires below)
│   ├── auth.php
│   └── modules/                          (one file per module, required from web.php — see Route Organization)
├── storage/
│   └── app/
│       └── public/                       (see Storage Structure)
├── tests/
│   ├── Feature/
│   └── Unit/
└── docs/                                 (existing documentation — untouched by this document)
```

**Rule:** a module's Controller, Request, Service, Model(s), Blade folder, and route file are always named after the same singular/plural pair defined in `CodingStandards.md` (e.g. `TicketController`, `Ticket` model, `tickets` table, `tickets.*` route names, `resources/views/tickets/`). This one-to-one naming makes it trivial to find every file belonging to a module.

---

## 2. MVC Architecture

FFixiT-MS strictly follows Laravel's MVC, extended with a Service layer (see Section 7). No Repository layer, no Domain/DTO layer, no CQRS — `AIInstructions.md` explicitly asks for Laravel Convention over custom architecture, and `CodingStandards.md`'s stated Goal is code "mudah dipahami bahkan oleh developer baru," which a deep custom architecture would work against.

### 2.1 Layer Responsibilities

| Layer | Responsibility | Must NOT contain |
|---|---|---|
| **Route** | Maps an HTTP verb + URI to a Controller action, with middleware applied. | Business logic, validation logic. |
| **Controller** | Receives the request (already validated by a Form Request), calls exactly one Service method, and returns a View or Redirect. | Query building, business rules, direct Eloquent writes beyond trivial reads for a View. |
| **Form Request** | Validates and authorizes input, per `AIInstructions.md` Backend Rules ("Gunakan Form Request Validation jika diperlukan"). | Business logic beyond validation/authorization. |
| **Service** | Owns business logic: orchestrates one or more Model operations, enforces `BusinessFlow.md` rules, wraps multi-step writes in a DB transaction, and is the only place status transitions (e.g. Ticket status) happen. | HTTP concerns (Request/Response objects), View rendering. |
| **Model (Eloquent)** | Table mapping, relationships (`ERD.md`), casts/enums, accessors/scopes, and model-level constants. | Cross-entity business rules, HTTP or Service concerns. |
| **View (Blade)** | Presentation only, per `ScreenSpecification.md` and `DesignSystem.md`. | Query logic (a View may loop over data already fully prepared by the Controller/Service — it must not call the Service or Model to fetch additional data itself). |

### 2.2 Data Flow (typical write action, e.g. "Finish Service")

```
Route (tickets.finish.store)
  → Middleware: auth, role:teknisi
  → FinishServiceRequest (validates work_result, service_fee, parts_used, evidence_after)
  → TicketController::finishService()
      → TicketService::finishService(Ticket $ticket, array $data)
          → wraps in DB::transaction()
          → updates Ticket status (Finished → Waiting Invoice), per BusinessFlow.md Step 7
          → creates TicketPhoto records (evidence_after)
          → creates StockMovement records (type: Service) for parts consumed
          → decrements Product stock via InventoryService (see Service Layer Strategy — cross-module calls)
  → redirect()->route('tickets.show', $ticket) with Success Alert
```

Controllers never call two Services' *domain* methods to fake a transaction boundary — if an action spans modules (e.g. Finish Service also touches Inventory), the *owning* Service (`TicketService`) calls the *other* Service's method (`InventoryService::deductStockForTicket()`), and the transaction is opened once, at the top (owning Service).

### 2.3 Models (per `ERD.md`, singular per `CodingStandards.md`)

`User`, `Customer`, `Employee`, `Ticket`, `TicketProgress`, `TicketPhoto`, `TicketPart`, `TicketCancellation`, `TicketWarranty`, `Supplier`, `Category`, `Product`, `StockMovement`, `PurchaseTransaction`, `PurchaseTransactionItem`, `Sale`, `SaleItem`, `OperationalExpense`, `ExpenseCategory`, `AuditLog`.

No `Role` model exists (see Binding Decisions §1).

---

## 3. Route Organization

### 3.1 Principles

- **Resource routes** wherever a module maps cleanly to CRUD, per `CodingStandards.md` Route Naming (`customers.index`, `customers.create`, `customers.store`, `customers.edit`, `customers.update`, `customers.destroy`).
- **Extra member/collection routes** for non-CRUD actions (e.g. Ticket status transitions), named as a nested resource-style suffix: `tickets.diagnosis.edit`, `tickets.diagnosis.store`, `tickets.finish.edit`, `tickets.finish.store`, matching the route names already used as the recommendation in `ScreenSpecification.md`.
- **One route file per module** under `routes/modules/`, required from `routes/web.php`, so a route file's diff in a Pull Request is scoped to exactly one module (supports the "One Module at a Time" principle in `Roadmap.md`).
- **Every route is named.** No anonymous closures in production route files.
- **Every non-auth route is wrapped in `auth` + `role:` middleware**, matching the Accessible Roles column of `ScreenSpecification.md` for that screen.

### 3.2 File Map

| File | Contains |
|---|---|
| `routes/web.php` | `Route::redirect('/', '/dashboard')`, the `dashboard` route, and `require` statements for `auth.php` and every file in `modules/`. |
| `routes/auth.php` | Login, Forgot Password, Reset Password, Logout (Sprint 0 — already implemented). |
| `routes/modules/customers.php` | Customer List/Form/Detail (v0.4). |
| `routes/modules/tickets.php` | Ticket List/Create/Detail + all sub-flows: diagnosis, approval, progress, evidence, sparepart-requests, finish, cancellation, warranty-claim, invoice, print (v0.5). |
| `routes/modules/inventory.php` | Product, Category, Stock In, Stock Opname, Stock Adjustment, Stock Movement History (v0.6). |
| `routes/modules/suppliers.php` | Supplier List/Form/Detail (v0.6). |
| `routes/modules/sales.php` | POS Transaction, Sales History, Sales Invoice Detail, Print Invoice (v0.7). |
| `routes/modules/expenses.php` | Expense List/Form, Expense Category (v0.8). |
| `routes/modules/monitoring.php` | Monitoring Overview + 5 read-only report pages (v0.9). |
| `routes/modules/user-management.php` | User, Employee, Role & Permission (v0.2). |
| `routes/modules/audit-log.php` | Audit Log List/Detail (v1.0). |

### 3.3 Route Group Skeleton (descriptive, not code)

Each module file wraps its routes in a group with:
- URI prefix matching the module (e.g. `tickets/...`),
- `auth` middleware,
- `role:<roles allowed per ScreenSpecification.md>` middleware, applied per sub-group when a sub-action's allowed roles differ from the module's general list (e.g. within `tickets.php`, the Cancellation review routes are further restricted to `role:it` even though the module overall allows `customer_service,it`),
- route name prefix matching the resource name (e.g. `name('tickets.')`).

### 3.4 Route Existence vs. Sidebar

Per Binding Decision §5, the Sidebar (Sprint 0) already lists every route name it *will* use once a module ships. When a module's route file is added in its sprint, only two things change in `app/View/Components/Sidebar.php`: the corresponding item's `enabled` flag flips to `true` and its `route` key is filled in — the menu structure itself does not change.

---

## 4. Blade Structure

### 4.1 Directory Convention

- `resources/views/components/` — reusable, generic, cross-module atoms (Button, Alert, Badge, Modal, Page Header, Empty State, and from v0.5 onward: Status Badge, Progress History, Evidence Gallery, Timeline, etc. as they're introduced in `ComponentLibrary.md`). Components used by more than one module belong here.
- `resources/views/components/layouts/` — `app.blade.php` (authenticated shell: Sidebar + Navbar + Content + Footer) and `guest.blade.php` (auth pages). Every module page extends one of these two via the `<x-layouts.app>` / `<x-layouts.guest>` component tag — never a raw `@extends`.
- `resources/views/{module}/` — one folder per module (matching the plural table/route name), containing that module's pages: `index.blade.php` (list), `create.blade.php` / `edit.blade.php` (or a shared `form.blade.php` partial included by both), `show.blade.php` (detail). Sub-flow pages (e.g. Ticket's Diagnosis, Progress, Finish Service) live in a module subfolder, e.g. `resources/views/tickets/diagnosis.blade.php`.
- `resources/views/{module}/partials/` — Blade partials specific to one module only (e.g. a Ticket Status Timeline partial used only across Ticket Detail's tabs). If a partial turns out to be needed by a second module, it is promoted to `resources/views/components/`.

### 4.2 Component Classification

Per `ComponentLibrary.md`, components fall into two kinds, and Sprint 0 already established the pattern for both:

| Kind | Where | Example |
|---|---|---|
| **Anonymous component** (no PHP class, pure Blade + `@props`) | `resources/views/components/*.blade.php` | Button, Alert, Badge, Modal, Empty State, Page Header |
| **Class-based component** (needs PHP logic to prepare data) | `app/View/Components/*.php` + matching Blade view | Sidebar (role-based menu building) |

A component only gets a backing PHP class when it needs computed data beyond what `@props` + simple Blade conditionals can express (mirroring why Sidebar needed one and Button did not). Examples expected to need a class in later sprints: `TicketStatusTimeline` (needs to compute which steps are complete/current/upcoming), `EvidenceGallery` (needs to group photos by Before/After).

### 4.3 Forms

Per `ScreenSpecification.md`'s repeated Create/Edit pairing, every module with both a Create and an Edit screen shares one Blade form partial (`{module}/_form.blade.php`) included by both `create.blade.php` and `edit.blade.php`, differing only in the form's `action`/`method` and whether fields are pre-filled — this avoids the duplicate-markup problem `CodingStandards.md` warns against ("Tidak duplikasi").

### 4.4 Print Views

Print-optimized views (`ScreenSpecification.md` 4.13, 7.4) live in `resources/views/{module}/print/` and extend a dedicated `<x-layouts.print>` layout (added in v0.5) that omits Sidebar/Navbar/Footer entirely, per the Page Layout spec for those screens.

---

## 5. Middleware Strategy

FFixiT-MS uses a small, explicit middleware set — no middleware groups beyond Laravel's own `web` group, per Binding Decision §2 (no RBAC package) and `AIInstructions.md` ("Menambahkan library pihak ketiga tanpa alasan yang jelas" is disallowed).

| Middleware | Registered as | Purpose |
|---|---|---|
| `auth` (Laravel default) | `auth` | Blocks unauthenticated access; redirects to `login`. |
| `guest` (Laravel default) | `guest` | Blocks authenticated users from auth pages (Login, Forgot/Reset Password). |
| `EnsureUserHasRole` (Sprint 0) | `role:<role1>,<role2>,...` | Compares `$request->user()->role` against the roles listed in the route definition; also blocks deactivated accounts (`is_active = false`), per `ScreenSpecification.md` 10.1. |

### 5.1 Application Order

Every protected module route is wrapped, in this order: `auth` → `role:...`. `auth` must run first so `EnsureUserHasRole` can safely assume a user is present.

### 5.2 Why No Policies for Role Checks

Route-level `role:` middleware is sufficient for every case in `Modules.md`'s Access Matrix, because FFixiT-MS's authorization is entirely role-based with no per-record ownership rules (e.g. a Teknisi does not need "own this specific ticket" authorization beyond "is a Teknisi and the ticket is unassigned or assigned to them" — a check simple enough for the Controller/Service to perform inline, per `ScreenSpecification.md` 4.1's Business Rules). Laravel Policies remain available (see folder structure) for the rare case a future module needs finer-grained, per-record authorization — none is currently documented.

### 5.3 Exception Rendering

`bootstrap/app.php` relies on Laravel's default status-code-to-view resolution for `403` and `404` (Sprint 0 already ships `resources/views/errors/403.blade.php` and `404.blade.php`, per `ScreenSpecification.md` 1.3–1.4). No custom `Handler`/`withExceptions` rendering logic is needed beyond registering the `role` middleware alias.

---

## 6. Authentication Strategy

### 6.1 Stack

Laravel's built-in session-based guard (`web`), scaffolded via **Laravel Breeze (Blade stack)** and then trimmed to match `ScreenSpecification.md` Module 1 exactly (Sprint 0 already removed Registration, Email Verification, and Password Confirmation — none are documented screens).

### 6.2 What Exists

| Feature | Status | Spec Reference |
|---|---|---|
| Login | Implemented (Sprint 0) | 1.1 |
| Logout | Implemented (Sprint 0) | 1.5 |
| Forgot / Reset Password | Implemented (Sprint 0) | 1.2 |
| Remember Me | Implemented (Sprint 0, `remember` checkbox) | 1.1 |
| Registration | **Not implemented — by design** | Accounts are created by IT (v0.2 User Management) |
| Email Verification | **Not implemented** | Not a documented screen |
| Two-Factor Auth | **Not implemented** | Not a documented screen; would require new approval |

### 6.3 Session Configuration

`SESSION_DRIVER=database` (per Sprint 0 `.env.example`), so active sessions are queryable/revokable — useful groundwork for a future "force logout" IT action, though no such screen is currently documented (flagged as a possible future item only, not implemented).

### 6.4 Account Activation Gate

`EnsureUserHasRole` (see Section 5) doubles as the activation gate: every authenticated route implicitly requires `is_active = true`, since every protected route already carries `role:` middleware. `AuthenticatedSessionController` additionally blocks login itself for deactivated accounts (defense in depth — the message is shown at the earliest possible point, per `ScreenSpecification.md` 1.1's validation messages, not just on the next request).

---

## 7. RBAC Strategy

### 7.1 Source of Truth

`App\Enums\UserRole` (backed `string` enum) is the **only** place the 5 roles are enumerated in code:

`IT`, `KEPALA_TOKO`, `ADMIN_GUDANG`, `CUSTOMER_SERVICE`, `TEKNISI` — matching `Roles.md` exactly, in both name and responsibility. The enum also carries presentation metadata (`label()`, `shortLabel()`, `badgeVariant()`) so no other file hardcodes a role's display string or badge color.

### 7.2 Enforcement Points

RBAC in FFixiT-MS is enforced at three layers, deliberately overlapping (defense in depth), per `Modules.md`'s Access Matrix and each screen's Accessible Roles in `ScreenSpecification.md`:

1. **Route middleware** (`role:...`) — blocks the request before any Controller code runs. This is the primary, authoritative gate.
2. **Blade conditionals** (`@if (auth()->user()->hasRole(UserRole::IT))` or `hasAnyRole([...])`) — hides buttons/actions a role cannot use, per `ScreenSpecification.md`'s repeated rule "buttons the current role is not authorized to use are hidden, not disabled" (see Global Conventions). This is a UX concern, not a security boundary by itself.
3. **Service-layer guard clauses** — for actions where the *route* is shared across roles but the *allowed transition* differs by role (e.g. Ticket Cancellation: CS can *request*, only IT can *approve* — both hit `tickets.cancellation.*` routes, but `TicketService` checks the acting user's role before performing an approval).

Layer 1 is mandatory on every route. Layers 2 and 3 are added as each module is implemented; a module PR that only implements Layer 1 is incomplete.

### 7.3 View-Level Role Badge Convention

Any screen listing a role (User List, Audit Log) renders it via `<x-badge :variant="$user->role->badgeVariant()">{{ $user->role->label() }}</x-badge>` — never a raw string — so a future role-label wording change happens in exactly one place (the enum).

### 7.4 What Is Explicitly Out of Scope

Per Binding Decision §2 and `AIInstructions.md` ("Menambah role baru" is disallowed): no admin UI to create/edit roles, no permission-toggle matrix stored in the database. The Role & Permission screen (`ScreenSpecification.md` 10.6) is a **read-only reference view** of the fixed `Modules.md` Access Matrix — it does not write to any table.

---

## 8. Service Layer Strategy

### 8.1 One Service per Module (minimum)

Per `CodingStandards.md` ("Use Service Classes when business logic becomes complex. Keep Controllers thin."), every module with more than trivial CRUD gets a dedicated Service:

| Service | Owns |
|---|---|
| `DashboardService` | Sprint 0 shell; from v0.3 onward, assembles each role's widget data by calling into other modules' Services (read-only). |
| `CustomerService` | Customer CRUD + delete-guard (blocks delete if Ticket/Sales history exists, per `ScreenSpecification.md` 3.1 Business Rules). |
| `TicketService` | The full Service Flow state machine (`BusinessFlow.md` Section A): creation, diagnosis, approval recording, progress, finish, invoicing, status transitions. This is the largest and most critical Service in the system. |
| `TicketCancellationService` | Cancellation request + IT approval/denial sub-flow (kept separate from `TicketService` because its authorization shape — CS requests, IT decides — is distinct enough to warrant isolation, while still being called *by* `TicketService` for the resulting status change). |
| `TicketWarrantyService` | Warranty claim creation (new linked ticket), per `BusinessFlow.md` Garansi rule. |
| `InventoryService` | Product/Category CRUD, Stock In, Stock Opname, Stock Adjustment, and the single place `StockMovement` rows are ever written (see 8.3). |
| `SparepartRequestService` | Request creation (from `TicketService`) and fulfillment (from Admin Gudang), per `ScreenSpecification.md` 4.8 / 5.9. |
| `SupplierService` | Supplier CRUD. |
| `SalesService` | POS transaction creation, void/refund, per `BusinessFlow.md` Direct Sales Flow. |
| `ExpenseService` | Expense + Expense Category CRUD. |
| `MonitoringService` | Read-only aggregation queries for the 5 report pages (v0.9) — no writes. |
| `UserManagementService` | User CRUD, Reset Password, Activate/Deactivate. |
| `EmployeeService` | Employee CRUD. |
| `AuditLogService` | Write-side: a single `record()` method called by other Services (see 8.4). Read-side: filtering/search for the Audit Log List/Detail screens. |

### 8.2 Service Method Shape

Every Service method that writes data:
- Accepts either a Model instance (for updates) or plain validated array data (from the Form Request), never the raw `Request` object — this keeps Services testable without HTTP.
- Wraps multi-step writes in `DB::transaction()`.
- Returns the affected Model (or a small result object) — never a Response/Redirect.
- Throws a domain exception (not an HTTP abort) for a business-rule violation the Controller then translates into a user-facing message — e.g. `TicketService::startService()` throws if the customer has not yet approved, per `BusinessFlow.md` Step 5's rule; the Controller catches it and re-renders with the exact validation message specified in `ScreenSpecification.md`.

### 8.3 Cross-Module Rule: Stock Movements

Per `BusinessFlow.md` Inventory Flow ("Setiap perubahan stock menghasilkan Stock Movement"), **only `InventoryService` is allowed to write a `StockMovement` row or mutate `products.stock`.** `TicketService` (parts used) and `SalesService` (items sold) both call `InventoryService::deductStock(...)`/`restoreStock(...)` rather than touching the `products` table directly. This single-writer rule is the most important cross-module contract in the system and must not be bypassed even for a "simple" adjustment — it is what keeps the Stock Movement History (`ScreenSpecification.md` 5.8) a complete, trustworthy ledger.

### 8.4 Cross-Module Rule: Audit Log

Per `BusinessFlow.md` Audit Flow, every Create/Update/Delete/Cancel/Reassign/Stock Adjustment/Login/Logout action is recorded. Rather than each Service duplicating "write an audit row," every write-side Service calls a single `AuditLogService::record(User $actor, string $action, Model $subject, array $changes = [])` at the end of its transaction. `AuditLogService` is the only Service permitted to write to `audit_logs` — enforcing the immutability rule from `ScreenSpecification.md` 11.1 (no Controller, View, or other Service ever issues an `UPDATE`/`DELETE` against that table).

### 8.5 Read-Heavy Pages (Monitoring, Dashboard)

`MonitoringService` and `DashboardService` are read-only by contract — they never call a write method on another Service. This keeps the reporting layer safely decoupled from the transactional layer: a bug in a report query can never corrupt operational data.

---

## 9. File Upload Strategy

FFixiT-MS has three documented upload surfaces, all using Laravel's standard `Illuminate\Http\UploadedFile` + `Storage` facade — no third-party media library, per `AIInstructions.md`'s "no unjustified third-party library" rule:

| Upload | Spec Reference | Constraints (from ScreenSpecification.md) |
|---|---|---|
| Ticket Evidence (Before/After photos) | 4.4, 4.7, 4.9 | Multiple images, JPG/PNG/WEBP only, required at least 1 per stage. |
| Ticket Cancellation Evidence | 4.10 | Multiple files (images, audio/video, or documents), required at least 1. |
| Expense Receipt Attachment | 8.2 | Single image or PDF, optional. |

### 9.1 Validation

Every upload field is validated in its Form Request with Laravel's `file`/`image`/`mimes` rules matching the table above, plus a `max:` rule for file size. The exact size ceiling is not specified in any current document — flagged as an **Open Item** (see Section 15 note below and `ScreenSpecification.md`'s own Appendix): implementation should default to a conservative `max:5120` (5 MB) per file until the project owner confirms a value.

### 9.2 Storage Location

All uploads are stored on the `public` disk (`storage/app/public/...`), served via the standard `php artisan storage:link` symlink — no cloud disk is configured in this phase, consistent with the project's current single-store, on-premise deployment implied by `README.md`. If FFixiT-MS is later deployed to infrastructure without persistent local disk, switching the disk to `s3` is a one-line config change since all upload code goes through the `Storage` facade rather than raw filesystem calls.

### 9.3 Naming & Organization

Uploaded files are stored under a path namespaced by module and owning record, never by original filename alone (to avoid collisions and to keep an owning record's files grouped): see Storage Structure (Section 10) for the exact path convention.

### 9.4 Processing

No image resizing/thumbnailing library is introduced in this phase — evidence photos are stored as uploaded. If gallery thumbnails become a performance concern, that is a candidate for the Recommended Packages list (Section 16) in a later sprint, not a Sprint 0/architecture-time decision.

---

## 10. Storage Structure

```
storage/app/public/
├── tickets/
│   └── {ticket_id}/
│       ├── evidence/
│       │   ├── before/            (Diagnosis stage uploads)
│       │   └── after/             (Finish Service stage uploads)
│       └── cancellations/
│           └── {cancellation_id}/ (supporting evidence files)
├── expenses/
│   └── {expense_id}/
│       └── receipt/               (single file per expense)
└── exports/                        (v0.9 Monitoring & Reports "Export Report" output — transient, not user-facing storage)
```

- Path segments use the record's numeric ID, never a user-supplied name, to keep paths predictable and collision-free.
- Nothing is stored directly under `storage/app/public/` root — every file belongs to a module subfolder, mirroring the Blade/Route/Model module boundaries described earlier in this document.
- `storage/app/private/` (default `local` disk) is reserved for any future non-public file (none currently documented) — evidence and receipts are intentionally on the `public` disk because CS/Teknisi/Kepala Toko view them directly in the browser (Evidence Gallery, Detail pages) without needing a signed-URL download route.

---

## 11. Database Migration Order

Migrations must run in dependency order — a table with a foreign key cannot migrate before the table it references. This order also mirrors, and is derived from, the module sequence in `Roadmap.md` (Foundation → Auth/User → Customer → Ticket → Inventory → Sales → Expense), so each sprint's migrations are a contiguous block.

| # | Migration | Depends On | Roadmap Milestone |
|---|---|---|---|
| 1 | `users` (+ `password_reset_tokens`, `sessions`) | — | v0.1 (done, Sprint 0) |
| 2 | `employees` | — | v0.2 |
| 3 | `customers` | — | v0.4 |
| 4 | `expense_categories` | — | v0.8 (migrated early since it has no dependencies; see note below) |
| 5 | `categories` | — | v0.6 |
| 6 | `suppliers` | — | v0.6 |
| 7 | `products` | `categories` | v0.6 |
| 8 | `tickets` | `customers`, `employees` (technician, nullable until assigned) | v0.5 |
| 9 | `ticket_progresses` | `tickets`, `employees` | v0.5 |
| 10 | `ticket_photos` | `tickets` | v0.5 |
| 11 | `ticket_parts` | `tickets`, `products` | v0.5 |
| 12 | `ticket_warranties` | `tickets` | v0.5 |
| 13 | `ticket_cancellations` | `tickets`, `users` (requested_by, decided_by) | v0.5 |
| 14 | `purchase_transactions` | `suppliers` | v0.6 |
| 15 | `purchase_transaction_items` | `purchase_transactions`, `products` | v0.6 |
| 16 | `stock_movements` | `products`, plus nullable polymorphic reference to source (`purchase_transactions` / `tickets` / `sales`) | v0.6 |
| 17 | `sales` | `customers` (nullable — walk-in), `users` (cashier) | v0.7 |
| 18 | `sale_items` | `sales`, `products` | v0.7 |
| 19 | `operational_expenses` | `expense_categories`, `users` | v0.8 |
| 20 | `audit_logs` | `users`, plus polymorphic reference to the affected record | v1.0 (see note below) |

**Notes:**

- **`expense_categories` is migrated early (step 4)** even though Operational Expense is v0.8, because it has zero dependencies and costs nothing to have available sooner; the *table* being migrated early does not mean the *module* is implemented early — no Controller/Service/View for Expense exists until v0.8. This is purely a migration-ordering convenience, not a scope change.
- **`audit_logs` is migrated at v1.0 per the literal Roadmap position**, but since `AuditLogService::record()` (Section 8.4) is called by every other Service from v0.2 onward, the `audit_logs` table must actually exist much earlier. **This is an Open Item requiring confirmation**: either (a) move the `audit_logs` migration to immediately after `users` (step 2) so audit recording can start from v0.2 as `BusinessFlow.md`'s Audit Flow implies ("mencatat aktivitas penting" — login/logout already happens in v0.2), or (b) confirm that Audit Log recording itself is intentionally deferred to v1.0 along with its UI. Recommendation: option (a). This does not change `ERD.md` (the table already exists there) or `Roadmap.md` (the *screen* still ships at v1.0) — it only moves *when the table is migrated*, which is an implementation-order detail, not a documentation change, but is flagged here per `AIInstructions.md`'s "ask before deciding" rule since it affects delivery sequencing.
- **Sparepart Request** (`ScreenSpecification.md` 4.8/5.9) has no dedicated table in `ERD.md`. Per that document's own Appendix, this is flagged as an Open Item: the recommended approach is to extend `ticket_parts` with a `status` column (`requested` / `fulfilled`) and a nullable `requested_at`/`fulfilled_at` pair, rather than introducing a new table, since `AIInstructions.md` forbids new tables without approval. This should be confirmed before the v0.5/v0.6 migrations are written.

---

## 12. Seeder Order

Seeders follow the same dependency order as migrations, split into two categories:

### 12.1 Foundation Seeders (run in every environment, including production first-deploy)

| # | Seeder | Purpose |
|---|---|---|
| 1 | `UserSeeder` | One account per role for initial IT access (Sprint 0 already seeds test accounts for local/dev only — production seeding should create exactly one real IT account, not the five test accounts, per an environment check, e.g. `app()->environment('local')`). |
| 2 | `ExpenseCategorySeeder` | Standard categories implied by `BusinessFlow.md`/`Roadmap.md` (Electricity, Water, Internet, Rent, Operational Equipment) — reference data, not demo data. |
| 3 | `CategorySeeder` | A starter set of product categories (e.g. Sparepart, Accessories, Peripherals) — reference data, to be confirmed with the project owner before the v0.6 sprint, since `Modules.md`/`ERD.md` do not enumerate specific category names. |

### 12.2 Demo/Development Seeders (local & staging only, never production)

| # | Seeder | Purpose |
|---|---|---|
| 4 | `EmployeeSeeder` | Sample employees, one per role, for exercising Ticket assignment. |
| 5 | `CustomerSeeder` | Sample walk-in customers. |
| 6 | `SupplierSeeder` | Sample suppliers. |
| 7 | `ProductSeeder` | Sample products across seeded categories, with realistic stock levels (including some intentionally below minimum stock, to exercise the Low Stock Warning). |
| 8 | `TicketSeeder` | Sample tickets across a spread of statuses (one per status value) so every Status Badge color and every Ticket Detail contextual action can be manually verified without manually walking a ticket through the whole flow. |
| 9 | `SaleSeeder` | Sample POS transactions. |
| 10 | `OperationalExpenseSeeder` | Sample expense entries across a few months, to exercise the Monitoring & Reports date-range filters. |

`DatabaseSeeder` calls Section 12.1 unconditionally and Section 12.2 only when `app()->environment(['local', 'staging'])`, so `php artisan migrate --seed` is safe to run against production and only provisions real reference data plus the initial IT account.

---

## 13. Testing Strategy

Per `AIInstructions.md`'s Development Rules ("kode yang bersih dan mudah dibaca") and `Roadmap.md`'s per-module workflow (`... → Implementation → Testing → Git Commit → Git Push`), every module ships with tests in the same Pull Request as its implementation — testing is not a separate later phase.

### 13.1 Test Types

| Type | Location | Covers |
|---|---|---|
| **Feature tests** | `tests/Feature/{Module}/` | HTTP-level: route access per role (both the "allowed" and "403" cases), form validation messages matching `ScreenSpecification.md` exactly, and the full happy-path flow through a Controller. This is the primary test type for FFixiT-MS, since almost all business value is expressed through HTTP-driven Service calls. |
| **Unit tests** | `tests/Unit/Services/` | Service methods in isolation (e.g. `TicketService::startService()` throwing when approval hasn't been recorded; `InventoryService::deductStock()` throwing on insufficient stock). Used wherever a Service method has business-rule branches worth testing without the overhead of a full HTTP request. |

### 13.2 What Every Module's Feature Test Suite Must Cover

1. **RBAC**: for every role listed in `ScreenSpecification.md`'s Accessible Roles, assert the expected access (200/redirect for allowed roles, 403 for disallowed roles, per Section 7.2 Layer 1).
2. **Validation**: for every Validation Message documented in `ScreenSpecification.md`, a test asserting that exact message appears when the corresponding invalid input is submitted.
3. **Business Rules**: for every rule listed under a screen's Business Rules section, a test proving the rule is enforced (e.g. "Start Service is disabled until Customer Decision = Approved" → a test that attempts `startService()` without a recorded approval and asserts failure).
4. **Status Transitions** (Ticket module especially): a test per transition in `BusinessFlow.md`'s Ticket Status flow, asserting the *only* valid next statuses are reachable and no status can be skipped.

### 13.3 Test Data

Every Model has a corresponding Factory (`database/factories/`). Feature tests build their own data via Factories rather than depending on the Demo Seeders (Section 12.2), so the test suite stays fast and independent of seed data changes.

### 13.4 Tooling

Laravel's default **PHPUnit** (or **Pest**, if the team prefers its syntax — either is acceptable since both run through the same Laravel `TestCase`; pick one project-wide for consistency and record the choice here once decided). No browser/E2E testing tool (e.g. Dusk, Playwright) is introduced in this phase — flagged as a candidate for later, not a Sprint 0 decision, since `AIInstructions.md` asks for justification before adding tooling and no current document calls for E2E coverage.

### 13.5 CI Expectation

Every Pull Request runs the full test suite (`php artisan test`) before merge — enforced at the Git workflow level (Section 15), not by a specific CI product choice, which is left to the team's existing tooling.

---

## 14. Git Branch Strategy

Per `Roadmap.md`'s "Git Version Control" principle and its per-feature workflow (`Requirement → Analysis → Design → Database → Backend → Frontend → Testing → Documentation → Commit → Push`), FFixiT-MS uses a simple, modular-development-friendly branching model — no complex Git-Flow with release branches, since the project ships incrementally by milestone rather than in scheduled releases.

### 14.1 Branches

| Branch | Purpose |
|---|---|
| `main` | Always deployable. Every merge to `main` corresponds to a completed Roadmap milestone (e.g. "v0.4 Customer Management done"). |
| `develop` | Integration branch for the milestone currently in progress. Feature branches merge here first; `develop` merges to `main` only when the whole milestone's Scope/Features list is complete. |
| `feature/{module}-{short-description}` | One branch per unit of work within a milestone, e.g. `feature/customer-list`, `feature/ticket-diagnosis-form`. Branches from `develop`, merges back to `develop` via Pull Request. |
| `fix/{short-description}` | Bug fixes outside an active feature branch, branched from and merged to `develop` (or `main` directly for a production hotfix, then back-merged to `develop`). |
| `docs/{short-description}` | Documentation-only changes (e.g. an approved edit to `docs/BusinessFlow.md`) — kept separate from `feature/*` so a documentation diff is never bundled with a code diff in the same review. |

### 14.2 Rules

- **One module at a time** (per `Roadmap.md`'s Development Strategy): only one `feature/*` branch per module is active at a time; a second feature for the same module waits for the first to merge, avoiding merge conflicts on shared files like `Sidebar.php` or a module's route file.
- No direct commits to `main` or `develop` — every change lands via Pull Request, even small ones, so the Feature-test requirement (Section 13.5) is always enforced.
- A `feature/*` branch is not started until its module's entry in `ScreenSpecification.md` (and, once this document exists, its entry in this document) is read in full — mirroring the "Required Reading Order" already enforced for this AI in `AIInstructions.md`, now extended to every contributor.

### 14.3 Commit Convention

Unchanged from `CodingStandards.md`/`Roadmap.md` — `feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:` — scoped to the module when helpful, e.g. `feat(ticket): add diagnosis form validation`.

---

## 15. Coding Workflow

This section operationalizes `Roadmap.md`'s per-feature workflow into concrete steps a developer (human or AI) follows for every unit of work, tying together every section above:

1. **Requirement** — locate the exact screen(s) in `ScreenSpecification.md` covering this unit of work.
2. **Analysis** — cross-check `BusinessFlow.md`, `Roles.md`, and `ERD.md` for any rule, role restriction, or table relationship the screen spec references. If anything is ambiguous or missing (e.g. the Open Items flagged in Section 11 and `ScreenSpecification.md`'s own Appendix), stop and request clarification, per `AIInstructions.md` — do not guess.
3. **Design** — confirm which layer(s) from Section 2 this unit touches (new route? new Service method? new Blade partial? a new reusable component per Section 4.2's threshold?).
4. **Database** — if a migration is needed, confirm it matches Section 11's order and does not add a table/column/relation beyond what `ERD.md` (plus any explicitly-approved Open Item resolution) allows.
5. **Backend** — implement Migration → Model → Form Request → Service → Controller → Route, in that order (each layer depends on the one before it existing).
6. **Frontend** — implement Blade view(s) using existing components from `resources/views/components/` wherever one already covers the need; only add a new component (Section 4.2) when the existing set genuinely doesn't fit.
7. **Testing** — write Feature (and Unit, where warranted) tests per Section 13.2's checklist before considering the unit done.
8. **Documentation** — if the unit surfaces any deviation from `ScreenSpecification.md` (should not normally happen) or resolves an Open Item, update the relevant document *only* with explicit approval, per the frozen-documentation rule.
9. **Commit** — per Section 14.3's convention, one logical change per commit.
10. **Push** — open a Pull Request against `develop` targeting the current milestone; the PR description references the `ScreenSpecification.md` section(s) implemented.

---

## 16. Recommended Laravel Packages

Per `AIInstructions.md` ("Menambahkan library pihak ketiga tanpa alasan yang jelas" is disallowed), every entry below states its justification. Packages already ruled out by Binding Decisions (Spatie Permission, any SPA/frontend framework, any Repository-pattern scaffolding package) are not repeated here.

| Package | Purpose | Justification |
|---|---|---|
| **laravel/breeze** | Auth scaffolding starting point | Already used in Sprint 0; official, minimal, Blade-based — matches the "no SPA" constraint exactly, and is trivially trimmed to the exact screens `ScreenSpecification.md` documents. |
| **laravel/pint** | Code style fixer | Enforces PSR-12 automatically (`CodingStandards.md` PHP Standard), removing style debate from code review. Official Laravel tool, zero config needed. |
| **larastan / phpstan** | Static analysis | Catches type errors and undefined-method mistakes (e.g. a Service method typo) before runtime — directly supports `CodingStandards.md`'s Code Quality goal ("Mudah dibaca, Konsisten"). |
| **barryvdh/laravel-ide-helper** (dev only) | IDE autocompletion for Eloquent models/facades | Developer-experience only, no runtime footprint; helps a "new developer joining later" (explicit `CodingStandards.md` Goal) ramp up faster in VS Code. |
| **maatwebsite/excel** | Export Report to Excel (Monitoring & Reports, `ScreenSpecification.md` 9.1's `Export Report` button) | The spec explicitly requires an export capability; hand-rolling XLSX generation is unnecessary risk versus this widely-used, actively maintained package. **Only added when v0.9 is implemented** — not needed before. |
| **barryvdh/laravel-dompdf** | Print Service Receipt / Invoice as a downloadable PDF, in addition to the browser print view (`ScreenSpecification.md` 4.13, 7.4) | The documented Print views work via the browser's native print dialog with no package needed; this package is **optional**, only justified if the project owner later wants a "Download PDF" capability distinct from Print — flagged here as a candidate, not a current requirement. |
| **intervention/image** | Evidence photo thumbnailing | **Not currently justified** (Section 9.4) — listed here only so that if it becomes needed, it's evaluated against this same justification bar rather than added ad hoc. |

### 16.1 Explicitly Not Recommended

- **spatie/laravel-permission** — superseded by the enum-based RBAC (Binding Decision §2).
- **Any Vue/React/Livewire/Inertia package** — superseded by the SSR Blade decision (Binding Decision §4).
- **Any Repository/Service-generator scaffolding package** — the Service layer (Section 8) is hand-written per module; a generator would encourage a shape that doesn't match this project's Controller → Service → Model contract.
- **Laravel Sanctum / Passport** — no API consumer is documented anywhere in `Modules.md` or `Roadmap.md` for the current scope (Long-Term Vision mentions "API Integration" only as a post-v1.0 idea) — introducing an API auth package now would be scope creep.

---

## Summary

This document defines the Laravel 12 architecture for FFixiT-MS across 16 areas, all derived from the existing frozen documentation set plus the six Binding Decisions approved during Sprint 0. It introduces exactly two Open Items requiring project-owner confirmation before the affected sprints begin — the `audit_logs` migration timing (Section 11) and the Sparepart Request table design (Section 11, inherited from `ScreenSpecification.md`'s own Appendix) — and one minor implementation default requiring confirmation (file upload size limit, Section 9.1). Everything else in this document is a direct, non-speculative translation of already-approved documentation and is ready to guide implementation from v0.2 onward.
