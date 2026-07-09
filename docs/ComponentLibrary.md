# Component Library

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

# Purpose

The Component Library exists to ensure that every future UI page in FFixiT-MS uses consistent, reusable, and maintainable interface building blocks. It acts as the single source of truth for common UI patterns across dashboard, ticket, inventory, customer, and operational modules.

This library helps the team:

- keep the interface consistent across all roles and modules
- reduce duplicated design decisions during implementation
- speed up future page development
- ensure accessibility, responsiveness, and usability standards are applied uniformly
- align UI delivery with business workflows and RBAC expectations

---

# Component Naming Convention

All reusable UI components must use clear, descriptive, and consistent names. Component names should follow PascalCase and reflect the purpose of the component rather than the page where it appears.

## Naming Rules

- Use PascalCase for all component names.
- Prefer descriptive names that clearly describe the UI responsibility.
- Avoid vague names such as Box, Item, or Panel unless the context is very clear.
- Keep names short but meaningful.
- Use domain-specific names where required, especially for ticket and inventory features.

## Standard Component Names

- Sidebar
- TopNavbar
- PageHeader
- PageToolbar
- StatisticCard
- InfoCard
- SearchBar
- FilterPanel
- DataTable
- Pagination
- PrimaryButton
- SecondaryButton
- SuccessButton
- DangerButton
- FormInput
- FormSelect
- FormTextarea
- Checkbox
- RadioButton
- Modal
- ConfirmationModal
- Toast
- Badge
- LoadingSpinner
- EmptyState
- Timeline
- StatusBadge
- Breadcrumb

---

# Global Layout Components

## Sidebar

- Purpose: Provide primary navigation for the current role and module.
- Location: Left side of the main application layout.
- Reusable: Yes, across all authenticated pages.
- Responsive Behaviour: Visible on desktop and tablet; collapses or becomes drawer-based on mobile.
- Bootstrap Classes: sidebar, bg-dark, text-white, nav, nav-pills, d-flex, flex-column.
- Variants: Collapsible Sidebar, Role-Based Sidebar, Compact Sidebar.

## Top Navbar

- Purpose: Display page-level actions, user profile, search, notifications, and global utilities.
- Location: Top of the main layout.
- Reusable: Yes, for all module pages.
- Responsive Behaviour: Stacks or collapses actions on smaller screens.
- Bootstrap Classes: navbar, navbar-light, navbar-expand-lg, bg-white, border-bottom.
- Variants: Standard Navbar, Compact Navbar, Dashboard Navbar.

## Page Header

- Purpose: Introduce the page with title, subtitle, and primary action.
- Location: Top of most pages beneath the navbar.
- Reusable: Yes, on index, detail, and management pages.
- Responsive Behaviour: Stacks title and actions vertically on smaller screens.
- Bootstrap Classes: d-flex, justify-content-between, align-items-center, mb-4, h1, h2.
- Variants: Simple Header, Action Header, Filter Header.

## Page Toolbar

- Purpose: Group page-level controls such as create, refresh, export, filter, and view toggles.
- Location: Below the page header.
- Reusable: Yes, used in listing and management screens.
- Responsive Behaviour: Wraps controls for smaller widths.
- Bootstrap Classes: d-flex, flex-wrap, gap-2, mb-3.
- Variants: Action Toolbar, Search Toolbar, Report Toolbar.

## Footer

- Purpose: Provide supporting information and simple system attribution.
- Location: Bottom of the main layout.
- Reusable: Yes, in full-page application layouts.
- Responsive Behaviour: Stays compact and aligned on all screen sizes.
- Bootstrap Classes: mt-5, pt-3, border-top, text-muted.
- Variants: Minimal Footer, Application Footer, Report Footer.

---

# Navigation Components

## Sidebar

- Purpose: Guide users through the available modules according to role access.
- Use When: Any authenticated screen that requires module navigation.
- Do Not Use When: A standalone modal, embedded widget, or full-page experience with no application-level navigation.

## Top Navbar

- Purpose: Provide global tools and quick actions.
- Use When: The page lives inside the main application shell.
- Do Not Use When: The content is presented as a full-screen workflow or isolated modal experience.

## Breadcrumb

- Purpose: Show the user’s location within the application hierarchy.
- Use When: The page is part of a deeper module path such as customer detail or ticket detail.
- Do Not Use When: The page is a top-level landing page with no nested context.

## Page Header

- Purpose: Clearly identify the page purpose and key page-level action.
- Use When: Every primary page should have a title and context.
- Do Not Use When: A compact modal or alert does not need a page title.

## Quick Action Bar

- Purpose: Provide shortcuts for frequent actions such as create ticket, create invoice, or add stock.
- Use When: The user needs fast access to common actions from a dashboard or landing page.
- Do Not Use When: The page already has a dense toolbar or a dedicated action panel.

---

# Dashboard Components

## Statistic Card

- Purpose: Display key metrics such as ticket count, inventory value, sales total, or active technicians.
- Location: Dashboard and analytics areas.
- Reusable: Yes.
- Responsive Behaviour: Stacks into a single column on smaller screens.
- Bootstrap Classes: card, card-body, h4, text-muted, bg-light.
- Variants: Metric Card, KPI Card, Summary Card.

## Chart Card

- Purpose: Present visual trends and operational insights.
- Location: Dashboard analytics sections.
- Reusable: Yes.
- Responsive Behaviour: Uses responsive canvas or chart container and adjusts to available width.
- Bootstrap Classes: card, card-body, chart-container, mb-4.
- Variants: Line Chart Card, Bar Chart Card, Doughnut Chart Card.

## Recent Activity Card

- Purpose: Show latest actions or updates from tickets, inventory, or customer service.
- Location: Dashboard home view.
- Reusable: Yes.
- Responsive Behaviour: Uses a compact list layout that scales down gracefully.
- Bootstrap Classes: card, card-body, list-group, list-group-item.
- Variants: Activity Feed, Recent Ticket List, Recent Inventory List.

## Quick Action Card

- Purpose: Provide direct shortcuts to important workflows.
- Location: Dashboard and role-specific landing pages.
- Reusable: Yes.
- Responsive Behaviour: Adjusts to a grid layout on larger screens and stacks on smaller screens.
- Bootstrap Classes: card, card-body, btn, btn-outline-primary.
- Variants: Shortcut Card, Module Card, Action Card.

## Notification Card

- Purpose: Highlight important alerts or pending items.
- Location: Dashboard and monitoring pages.
- Reusable: Yes.
- Responsive Behaviour: Keeps content readable and concise on smaller screens.
- Bootstrap Classes: card, border-warning, alert, bg-light.
- Variants: Warning Card, Info Card, Urgent Card.

---

# Data Components

## Responsive Table

- Purpose: Display structured records such as tickets, customers, products, suppliers, and expenses.
- Location: Index and listing pages.
- Reusable: Yes.
- Responsive Behaviour: Must remain usable on smaller screens through horizontal scrolling or stacked presentation.
- Bootstrap Classes: table, table-responsive, table-hover, table-striped.
- Variants: Basic Table, Data Table, Detail Table.

## Search Bar

- Purpose: Allow users to find records quickly.
- Location: Above data lists and tables.
- Reusable: Yes.
- Responsive Behaviour: Expands and wraps naturally for smaller screens.
- Bootstrap Classes: input-group, form-control, btn, btn-outline-secondary.
- Variants: Simple Search, Advanced Search, Global Search.

## Filter Panel

- Purpose: Narrow results by status, date, category, role, or inventory condition.
- Location: Above or beside data lists.
- Reusable: Yes.
- Responsive Behaviour: Collapses into a compact row or dropdown on smaller screens.
- Bootstrap Classes: card, p-3, row, col-md-3, form-select.
- Variants: Inline Filter Panel, Collapsible Filter Panel, Advanced Filter Panel.

## Pagination

- Purpose: Split long lists into manageable pages.
- Location: Bottom of tables and data grids.
- Reusable: Yes.
- Responsive Behaviour: Must remain simple and touch-friendly on small devices.
- Bootstrap Classes: pagination, page-item, page-link.
- Variants: Standard Pagination, Compact Pagination, Simple Pagination.

## Status Badge

- Purpose: Represent states such as Waiting Technician, In Progress, Approved, Cancelled, or Low Stock.
- Location: Tables, cards, and detail pages.
- Reusable: Yes.
- Responsive Behaviour: Must remain clear and readable in compact layouts.
- Bootstrap Classes: badge, bg-primary, bg-success, bg-warning, bg-danger.
- Variants: Success Badge, Warning Badge, Danger Badge, Info Badge.

## Action Button Group

- Purpose: Group related actions such as view, edit, delete, or print.
- Location: Tables and detail pages.
- Reusable: Yes.
- Responsive Behaviour: Wraps or stacks when space is limited.
- Bootstrap Classes: btn-group, d-flex, gap-2.
- Variants: Inline Actions, Dropdown Actions, Bulk Actions.

## Empty State

- Purpose: Inform users when no data is available.
- Location: Empty tables, empty search results, and empty dashboards.
- Reusable: Yes.
- Responsive Behaviour: Keeps the message centered and readable.
- Bootstrap Classes: text-center, py-5, text-muted, btn.
- Variants: No Data State, No Results State, Empty Dashboard State.

## Loading State

- Purpose: Indicate that data is being loaded or processed.
- Location: Tables, forms, dashboards, and asynchronous actions.
- Reusable: Yes.
- Responsive Behaviour: Uses lightweight visual treatment on smaller screens.
- Bootstrap Classes: spinner-border, placeholder-glow, d-flex, justify-content-center.
- Variants: Spinner, Skeleton Loader, Progress Indicator.

---

# Form Components

## Text Input

- Purpose: Collect short free-text information.
- Use When: Name, notes, reference number, or short descriptions are required.
- Do Not Use When: The value must be selected from a fixed list.

## Number Input

- Purpose: Capture numeric values such as quantity, cost, or quantity on hand.
- Use When: The value is strictly numeric.
- Do Not Use When: The field should allow text or a selectable option.

## Email Input

- Purpose: Collect a valid email address.
- Use When: Customer, user, or supplier contact details are required.
- Do Not Use When: A non-email identifier is expected.

## Password Input

- Purpose: Capture confidential credentials.
- Use When: Login, account setup, or password change flows are involved.
- Do Not Use When: The field is not security-sensitive.

## Textarea

- Purpose: Collect longer free-form text such as complaints, technician notes, or service descriptions.
- Use When: Multiline input is necessary.
- Do Not Use When: A short field or fixed choice is sufficient.

## Select

- Purpose: Allow users to choose from a predefined list.
- Use When: A field has limited, known values such as ticket status, supplier, or category.
- Do Not Use When: The value is open-ended or better handled with free text.

## Checkbox

- Purpose: Allow multiple selections or binary choices.
- Use When: The user can choose more than one option or confirm a simple condition.
- Do Not Use When: Only one choice is valid.

## Radio

- Purpose: Allow one selection from a small set of mutually exclusive options.
- Use When: Only one option should be chosen.
- Do Not Use When: Multiple selections are allowed.

## Date Picker

- Purpose: Select a date or date range.
- Use When: The form requires a calendar-based date input such as service date or purchase date.
- Do Not Use When: A simple text field is sufficient.

## File Upload

- Purpose: Accept evidence files, documents, or attachments.
- Use When: The workflow requires uploading images or supporting documents.
- Do Not Use When: No attachment is needed.

## Validation Message

- Purpose: Explain errors or missing inputs clearly.
- Use When: A field fails validation or requires correction.
- Do Not Use When: No validation issue exists.

## Form Action Buttons

- Purpose: Confirm, cancel, save, or submit form actions.
- Use When: A form requires a final action or reset.
- Do Not Use When: The form is informational only and no action is required.

---

# Modal Components

## Information Modal

- Purpose: Present important information that does not require immediate action.
- Use When: The user needs context or explanation before continuing.
- Do Not Use When: A simple alert or inline message is sufficient.

## Confirmation Modal

- Purpose: Ask the user to confirm a non-destructive action.
- Use When: The action changes state but should be reviewed first.
- Do Not Use When: The action is trivial and does not warrant interruption.

## Delete Confirmation

- Purpose: Confirm destructive actions such as removing a record or item.
- Use When: The action could permanently alter or delete data.
- Do Not Use When: The user is only viewing content or performing a read-only action.

## Success Modal

- Purpose: Confirm a task completed successfully.
- Use When: A process finishes successfully and the user should receive positive feedback.
- Do Not Use When: The success state can be shown inline or with a toast.

## Error Modal

- Purpose: Communicate a blocking or critical issue.
- Use When: The user must understand a failure state and follow next steps.
- Do Not Use When: A smaller alert or inline validation message is enough.

---

# Notification Components

## Success Alert

- Purpose: Show successful outcomes.
- Use When: Saving, approving, or completing an action succeeds.
- Do Not Use When: The success is already obvious in the page state.

## Warning Alert

- Purpose: Draw attention to pending or cautionary conditions.
- Use When: Approval is pending, stock is low, or an action requires caution.
- Do Not Use When: The situation is a standard or neutral state.

## Danger Alert

- Purpose: Show critical problems or failures.
- Use When: Deletion, validation failure, or system error occurs.
- Do Not Use When: The message is informative rather than urgent.

## Info Alert

- Purpose: Share neutral information relevant to the current task.
- Use When: Helpful context or guidance is needed.
- Do Not Use When: A more urgent feedback style is required.

## Toast Notification

- Purpose: Provide brief feedback after an action.
- Use When: A quick confirmation is needed without interrupting the workflow.
- Do Not Use When: The user needs a long explanation or confirmation step.

---

# Ticket Components

## Ticket Status Badge

- Purpose: Show the current ticket state such as Waiting Technician, In Progress, Waiting Customer Approval, or Completed.
- Use When: Ticket lists and ticket detail views require quick state recognition.
- Do Not Use When: The status is already visible in a full workflow summary.

## Priority Badge

- Purpose: Indicate urgency or severity.
- Use When: Service tickets need immediate triage or visual prioritization.
- Do Not Use When: No prioritization is needed.

## Technician Badge

- Purpose: Display the assigned technician or technician group.
- Use When: Ticket assignment is relevant.
- Do Not Use When: The assignee is irrelevant to the current view.

## Warranty Badge

- Purpose: Show warranty eligibility or warranty status.
- Use When: Service and product history views need warranty context.
- Do Not Use When: The ticket or product has no warranty relevance.

## Timeline

- Purpose: Visualize the progression of service activity over time.
- Use When: Ticket progress, service flow, or history must be reviewed.
- Do Not Use When: A simple status summary is sufficient.

## Progress History

- Purpose: Show historical updates related to service work.
- Use When: Detailed progress tracking is important.
- Do Not Use When: The page only needs a high-level status summary.

## Evidence Gallery

- Purpose: Display before and after evidence images.
- Use When: Ticket diagnosis or service completion needs visual proof.
- Do Not Use When: No evidence needs to be shown.

---

# Inventory Components

## Stock Badge

- Purpose: Show stock availability state.
- Use When: Inventory items need quick visibility of availability.
- Do Not Use When: The stock level is not relevant to the current view.

## Low Stock Warning

- Purpose: Highlight products that need replenishment.
- Use When: Inventory lists or dashboard summary need immediate attention.
- Do Not Use When: Stock levels are healthy and no action is required.

## Stock Movement Card

- Purpose: Show recent incoming, outgoing, or adjustment history for an item.
- Use When: Inventory movement detail is needed.
- Do Not Use When: A simple current stock summary is enough.

## Purchase Summary Card

- Purpose: Present purchase details such as supplier, amount, and item count.
- Use When: Inventory purchase review is required.
- Do Not Use When: The context is operational only and not purchase related.

---

# Common Button Standards

## Primary

- Purpose: Main action for the current screen.
- Use When: The user should take the main next step.
- Do Not Use When: A secondary or contextual action is more appropriate.

## Secondary

- Purpose: Supportive or less prominent action.
- Use When: The user needs to navigate back or cancel.
- Do Not Use When: The action should be the primary focus.

## Success

- Purpose: Confirm completion or approval.
- Use When: A save, approve, or complete action is performed.
- Do Not Use When: The action is destructive or cautionary.

## Warning

- Purpose: Indicate review or caution.
- Use When: An action needs extra attention, such as editing or pending approval.
- Do Not Use When: The action is clearly safe and straightforward.

## Danger

- Purpose: Highlight destructive or irreversible actions.
- Use When: Delete, cancel, or remove is required.
- Do Not Use When: The action should not risk data loss.

## Outline Buttons

- Purpose: Provide low-emphasis actions while keeping visual balance.
- Use When: Secondary actions should not compete with the primary call to action.
- Do Not Use When: The action is the primary focus.

## Icon Buttons

- Purpose: Represent a compact action with an icon and optional tooltip.
- Use When: Space is limited or the action is obvious from the icon.
- Do Not Use When: The action is ambiguous or needs a text label.

## Disabled Buttons

- Purpose: Prevent interaction when an action is unavailable.
- Use When: Validation, permission, or state prevents the action.
- Do Not Use When: The action should remain available.

## Loading Buttons

- Purpose: Show that an action is being processed.
- Use When: Saving, submitting, or updating data that may take time.
- Do Not Use When: The action is instant and should not interrupt the workflow.

---

# Table Standards

Every table must include:

- Search
- Filter
- Pagination
- Refresh
- Column Sorting
- Action Column
- Row Number
- Responsive behaviour

Additional rules:

- Tables must remain readable on desktop first and usable on smaller screens.
- Important columns should remain visible and prioritized.
- Status and action columns should be visually clear.
- Tables should support empty and loading states.

---

# Form Standards

## Label Position

- Labels should be placed above each input for clarity and consistency.

## Required Field

- Required fields must be clearly marked.
- Required indicators should be consistent across all forms.

## Placeholder Rules

- Use placeholders only as hints, not as substitutes for labels.
- Avoid redundant or generic placeholder text.

## Validation Rules

- Validation messages must be short, specific, and actionable.
- Errors should appear near the relevant field.

## Button Position

- Primary action buttons should appear at the end of the form.
- Secondary actions should appear before or beside the primary action.

## Responsive Behaviour

- Form fields should stack or wrap appropriately on smaller screens.
- Long forms should remain readable and avoid excessive horizontal scrolling.

---

# Empty State Standards

- Standard illustration placement should be centered near the top of the empty area.
- Message format should be clear, concise, and explain what is missing.
- The primary action button should guide the user toward the next step.
- Empty states should be used for empty tables, empty search results, and empty dashboards.

---

# Loading Standards

## Spinner

- Use for short actions or page transitions.

## Skeleton Loader

- Use for content-heavy cards or tables when data is loading.

## Progress Bar

- Use for longer or multi-step processes where progress should be visible.

---

# Accessibility Rules

## Keyboard Navigation

- All interactive components must be reachable and operable using the keyboard.
- Focus order must be logical and predictable.

## Focus State

- Focus indicators must be clearly visible.
- Focus should be preserved appropriately in modals, forms, and navigation.

## Color Contrast

- Text and interactive elements must maintain sufficient contrast.
- Status colors should not be the only means of conveying meaning.

## ARIA Recommendation

- Use ARIA labels and roles where appropriate for dialogs, navigation, alerts, and dynamic updates.
- Decorative icons should not create unnecessary noise for assistive technologies.

---

# Component Usage Rules

Each component should be used only when it matches the business intent and the current UI context.

## Use Components When

- The pattern is repeated across multiple pages or modules.
- The UI needs consistency and predictability.
- The component supports a clear user task.
- The component improves readability or decision-making.

## Do Not Use Components When

- The information is one-off and does not need reuse.
- A simpler pattern would be more understandable.
- The component adds visual complexity without a clear benefit.
- The UI would become inconsistent with the rest of the system.

## Practical Guidance

- Use cards for grouped summaries and metrics.
- Use tables for structured records and lists.
- Use forms for data entry and updates.
- Use modals only for focused or interruptive actions.
- Use badges for quick state recognition.
- Use alerts and toasts for feedback, not for primary content.

---

# Summary

This document will be used as the UI component standard for every future page in FFixiT-MS. It defines the common reusable components, naming rules, layout expectations, interaction standards, accessibility requirements, and usage guidance needed to build a consistent and professional interface across the entire system.
