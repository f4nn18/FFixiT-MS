# Design System

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

# 1. Design Philosophy

## Overview

FFixiT-MS is designed for **professional use in a fast-paced computer service environment**. The UI must support quick decision-making, efficient task management, and accurate data entry while maintaining a clean, trustworthy appearance.

## Core Principles

### Target Users

- **IT Administrators**: Need complete system oversight and control. Value efficiency and data accuracy.
- **Store Managers**: Need real-time operational insights. Value dashboards and quick analytics.
- **Warehouse Staff**: Need inventory efficiency. Value quick lookup and stock management.
- **Customer Service**: Need rapid customer interaction and ticket creation. Value speed and ease of use.
- **Technicians**: Need clear task lists and straightforward work tracking. Value simplicity and focus.

### Ease of Use

- **Task-Focused**: Every page designed around a single primary action (create ticket, view inventory, etc.)
- **Predictable**: Consistent patterns across all modules (list → detail → action)
- **Information Hierarchy**: Critical information prominent; secondary info accessible
- **Minimal Clicks**: Maximum 3 clicks to reach any major function
- **Feedback**: Clear confirmation for actions, error messages when needed

### Desktop-First Approach

- Primary design target: **1920x1080** (common office resolution)
- Secondary: **1366x768** (laptop displays)
- Responsive support: Tablets (768px+), Mobile (375px+)
- Sidebar remains visible on desktop and tablet; collapses on mobile
- Forms and tables prioritize desktop clarity first

### Professional Appearance

- **Color Scheme**: Neutral blues and grays with strategic accent colors
- **Typography**: Clean sans-serif for maximum readability
- **Whitespace**: Generous spacing for visual clarity and reduced cognitive load
- **Consistency**: Uniform component styling across all modules
- **Visual Hierarchy**: Size, weight, and color guide user attention

### Consistency

- **Component Library**: Predefined buttons, cards, forms, tables (all variations)
- **Spacing System**: 4px grid (4, 8, 12, 16, 20, 24, 32, 40 px)
- **Naming Convention**: All components use Bootstrap naming for developer familiarity
- **Icon System**: Single icon library (Bootstrap Icons) across entire system
- **Interaction Patterns**: Same actions produce same visual feedback everywhere

### Business Alignment

- **RBAC Visible**: Menu changes reflect user permissions; no broken links
- **Workflow Support**: UI follows business process (ticket → diagnosis → approval → execution)
- **Data Integrity**: Confirmations required for destructive actions
- **Audit Trail**: All changes implicitly logged (shown in documentation, not UI)

---

# 2. Color Palette

## Core Colors

### Primary - **Trust & Action**

```
Primary:        #0D6EFD (Bootstrap Primary)
Primary Dark:   #0A58CA
Primary Light:  #7ABAFF
Usage: Main CTAs, active states, selected items, primary buttons
Psychology: Blue conveys trust, essential for service/repair industry
```

### Secondary - **Neutral Background**

```
Secondary:      #6C757D (Bootstrap Secondary)
Secondary Dark: #5C636A
Secondary Light: #ADBAC1
Usage: Disabled states, inactive tabs, secondary buttons, helper text
```

### Success - **Completion & Approval**

```
Success:        #198754 (Bootstrap Success)
Success Dark:   #146C43
Success Light:  #75B798
Usage: Completed actions, approved tickets, positive status, success buttons
Psychology: Green = progress, commonly understood as "go"
```

### Danger - **Cancellation & Error**

```
Danger:         #DC3545 (Bootstrap Danger)
Danger Dark:    #BB2D3B
Danger Light:   #F8B4B8
Usage: Cancelled tickets, delete confirmations, error alerts, danger buttons
Psychology: Red = stop, alerts user to critical actions
```

### Warning - **Attention Required**

```
Warning:        #FFC107 (Bootstrap Warning)
Warning Dark:   #FFBB33
Warning Light:  #FFF3CD
Usage: Pending approvals, waiting states, caution alerts, warning buttons
Psychology: Yellow/amber = caution, slow down
```

### Info - **Informational**

```
Info:           #0DCAF0 (Bootstrap Info)
Info Dark:      #0AA2C0
Info Light:     #B6EFFB
Usage: Informational alerts, neutral notifications, info badges
Psychology: Cyan = neutral information, technical context
```

## Neutral Colors

### Background Colors

```
Body Background:        #FFFFFF (pure white)
Container Background:   #F8F9FA (very light gray - Bootstrap Light)
Card Background:        #FFFFFF (pure white)
Hover Background:       #F1F3F5 (light gray - lighter shade)
Disabled Background:    #E9ECEF (gray - Bootstrap Light variant)
```

### Sidebar & Navigation

```
Sidebar Background:     #2C3E50 (dark slate)
Sidebar Text:           #FFFFFF (white)
Sidebar Hover:          #34495E (slightly lighter slate)
Sidebar Active:         #0D6EFD (primary blue highlight)
Navbar Background:      #FFFFFF (white)
Navbar Border:          #DEE2E6 (light gray border)
```

### Text & Borders

```
Primary Text:           #212529 (Bootstrap Dark)
Secondary Text:         #6C757D (Bootstrap Secondary)
Muted Text:             #999999 (lighter gray)
Placeholder Text:       #AAAAAA (even lighter)

Border Color:           #DEE2E6 (Bootstrap Border)
Border Light:           #E9ECEF (lighter border)
Divider:                #DEE2E6 (same as border)
```

## Semantic Color Usage

```
Active Tab:             #0D6EFD (Primary)
Inactive Tab:           #6C757D (Secondary)
Active Menu Item:       #0D6EFD (Primary) with left border accent
Disabled State:         #E9ECEF (Bg) + #999999 (Text)
Focus State:            0D6EFD border (2px) + box-shadow
Hover State:            Slight opacity increase or background shift
```

---

# 3. Typography

## Font Stack

### Primary Font (System UI)

```
Font Family:    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif
Usage:          Body, UI elements, forms
Reasoning:      System fonts load instantly, no font file requests, renders consistently
```

### Monospace Font (Code/Data)

```
Font Family:    "Courier New", Courier, monospace
Usage:          Ticket IDs, product codes, serial numbers, error messages
Reasoning:      Fixed-width for alignment and clarity
```

## Heading Hierarchy

```
H1 - Page Title
    Font Size:      32px
    Font Weight:    700 (bold)
    Line Height:    1.2
    Margin Bottom:  24px
    Color:          #212529 (Primary Text)
    Usage:          Top of every page (only one per page)

H2 - Section Title
    Font Size:      24px
    Font Weight:    600 (semibold)
    Line Height:    1.3
    Margin Top:     24px
    Margin Bottom:  16px
    Color:          #212529
    Usage:          Main sections within page

H3 - Subsection Title
    Font Size:      20px
    Font Weight:    600
    Line Height:    1.3
    Margin Top:     16px
    Margin Bottom:  12px
    Color:          #212529
    Usage:          Subsections under H2

H4 - Card Title / Emphasis
    Font Size:      18px
    Font Weight:    600
    Line Height:    1.4
    Margin Bottom:  12px
    Color:          #212529
    Usage:          Card titles, emphasis headings

H5 - Small Heading
    Font Size:      16px
    Font Weight:    600
    Line Height:    1.4
    Margin Bottom:  8px
    Color:          #212529
    Usage:          Table headers, form labels

H6 - Minor Label
    Font Size:      14px
    Font Weight:    600
    Line Height:    1.4
    Color:          #6C757D
    Usage:          Secondary labels, helper text
```

## Body Text

```
Regular Body Text
    Font Size:      14px
    Font Weight:    400 (normal)
    Line Height:    1.6
    Color:          #212529
    Usage:          Main content, descriptions, paragraphs

Small Text
    Font Size:      12px
    Font Weight:    400
    Line Height:    1.5
    Color:          #6C757D
    Usage:          Helper text, timestamps, metadata

Large Text (Emphasis)
    Font Size:      16px
    Font Weight:    400
    Line Height:    1.6
    Color:          #212529
    Usage:          Important information, emphasized content

Muted Text
    Font Size:      14px
    Font Weight:    400
    Line Height:    1.6
    Color:          #999999
    Usage:          Disabled states, secondary info, placeholders
```

## Table Text

```
Table Header
    Font Size:      13px
    Font Weight:    600
    Line Height:    1.5
    Color:          #212529
    Background:     #F8F9FA
    Text Transform: None (use natural case)
    Usage:          Column headers

Table Data Cell
    Font Size:      14px
    Font Weight:    400
    Line Height:    1.5
    Color:          #212529
    Padding:        12px 16px
    Usage:          Regular table cells

Table Status/Badge
    Font Size:      12px
    Font Weight:    600
    Color:          White (with colored background)
    Usage:          Status badges within tables

Table Numeric Data
    Font Size:      14px
    Font Weight:    500 (slightly heavier for clarity)
    Color:          #212529
    Text Align:     Right
    Usage:          Prices, quantities, calculations
```

## Button Text

```
Primary/Action Button
    Font Size:      14px
    Font Weight:    600
    Text Transform: None
    Letter Spacing: normal
    Color:          White (on colored background)
    Padding:        8px 16px (medium), 6px 12px (small)
    Usage:          All interactive buttons

Button Hover State
    Font Size:      14px (unchanged)
    Opacity:        Darken background or increase contrast
    Cursor:         pointer
    Transition:     200ms
    Usage:          Visual feedback for interactivity

Button Disabled State
    Font Size:      14px (unchanged)
    Color:          #999999
    Background:     #E9ECEF
    Opacity:        0.65
    Cursor:         not-allowed
    Usage:          Unavailable actions
```

## Card Title

```
Card Title
    Font Size:      18px
    Font Weight:    600
    Line Height:    1.4
    Color:          #212529
    Margin Bottom:  16px
    Usage:          Main heading in card

Card Subtitle
    Font Size:      14px
    Font Weight:    400
    Color:          #6C757D
    Margin Bottom:  12px
    Usage:          Secondary information
```

## Special Text Styles

```
Link Color:             #0D6EFD (Primary)
Link Hover:             #0A58CA (Primary Dark) with underline
Link Visited:           #6610F2 (Purple - optional)

Success Text:           #146C43 (Success Dark)
Danger Text:            #BB2D3B (Danger Dark)
Warning Text:           #FFBB33 (Warning Dark - on light background)
Info Text:              #055160 (Info Dark)

Bold (Weight 700):      Used for emphasis within body text
Italic:                 Avoid (use bold or color instead)
Strikethrough:          Avoid (use status color instead)
```

---

# 4. Layout System

## Page Structure

### Standard Page Layout

```
┌─────────────────────────────────────────────────────┐
│                    NAVBAR                           │
│  Logo   Breadcrumb   Search   User Menu   Notif    │
├──────────┬──────────────────────────────────────────┤
│          │                                           │
│ SIDEBAR  │              CONTENT AREA                │
│          │  ┌─ Title + Action Buttons ──────────────┤
│ Menu     │  │                                        │
│ Items    │  │  ┌─ Card / Table / Form ─────────────┤
│          │  │  │                                    │
│ Active   │  │  │  [Main Content]                   │
│ Indicator│  │  │                                    │
│          │  │  └────────────────────────────────────┤
│          │  │                                        │
│          │  └────────────────────────────────────────┤
│          │                                           │
├──────────┴──────────────────────────────────────────┤
│                    FOOTER                           │
│              © 2026 FFixiT-MS                       │
└─────────────────────────────────────────────────────┘
```

## Sidebar (Left Navigation)

### Desktop Dimensions

```
Width:              260px (fixed)
Background:         #2C3E50 (dark slate)
Text Color:         #FFFFFF (white)
Border Right:       1px solid #34495E
Position:           Fixed, height 100vh
Scrollable:         Yes, if menu exceeds viewport
```

### Sidebar Components

#### Logo Section (Top)

```
Height:             80px
Display:            Logo + Brand Name
Alignment:          Centered
Padding:            16px
Font Size:          18px
Font Weight:        700
Border Bottom:      1px solid #34495E
Sticky:             Yes
```

#### Menu Item (Default)

```
Height:             44px
Padding:            12px 16px
Font Size:          14px
Font Weight:        400
Color:              #FFFFFF
Icon Size:          18px
Icon Margin:        0 12px 0 0
Hover State:        Background #34495E
Transition:         200ms
Cursor:             pointer
```

#### Menu Item (Active)

```
Height:             44px
Padding:            12px 16px
Background:         #0D6EFD (primary blue)
Font Weight:        600
Left Border:        4px solid #0A58CA
Margin Left:        -4px
Color:              #FFFFFF
Icon Size:          18px
```

#### Submenu (Nested)

```
Padding Left:       32px (nested indentation)
Font Size:          13px
Font Weight:        400
Color:              #FFFFFF
Background:         #34495E
Height:             40px
```

#### Menu Divider

```
Height:             1px
Background:         #34495E
Margin:             8px 0
```

#### Logout Button (Bottom)

```
Position:           Sticky bottom of sidebar
Height:             44px
Background:         #BB2D3B (danger dark)
Color:              #FFFFFF
Font Weight:        600
Width:              100%
Padding:            12px 16px
Border Top:         1px solid #34495E
Hover:              Background #DC3545 (danger lighter)
```

## Navbar (Top Navigation)

### Dimensions

```
Height:             60px
Background:         #FFFFFF
Border Bottom:      1px solid #DEE2E6
Position:           Fixed, top
Z-Index:            1020
Width:              calc(100% - 260px) [Desktop]
```

### Navbar Sections

#### Left Section (Breadcrumb/Title)

```
Padding:            12px 24px
Font Size:          14px
Color:              #6C757D
Separator:          " / "
Item Count:         Max 4 levels
Overflow:           Truncate with ellipsis
```

#### Center Section (Reserved)

```
Space:              For future features or search
```

#### Right Section (User Controls)

```
Display:            User Avatar + Name + Dropdown
Padding:            12px 24px
Font Size:          13px
Avatar Size:        40px circular image
Spacing:            16px between elements
```

## Content Container

### Desktop (1920px+)

```
Width:              calc(100% - 260px) [minus sidebar]
Max Width:          None (full width minus sidebar)
Margin Left:        260px
Padding:            24px
Background:         #F8F9FA
Min Height:         calc(100vh - 60px - 60px) [navbar + footer]
```

### Tablet (768px - 1024px)

```
Width:              calc(100% - 260px) [sidebar remains]
Padding:            20px
```

### Mobile (375px - 767px)

```
Width:              100%
Sidebar:            Collapse / Hamburger menu
Margin Left:        0
Padding:            16px
```

## Cards

### Standard Card

```
Background:         #FFFFFF
Border:             1px solid #DEE2E6
Border Radius:      8px
Box Shadow:         0 1px 3px rgba(0, 0, 0, 0.08)
Padding:            20px
Margin Bottom:      24px
Overflow:           Hidden
```

### Card Header (Optional)

```
Background:         #F8F9FA
Padding:            16px 20px
Border Bottom:      1px solid #DEE2E6
Font Weight:        600
Font Size:          16px
```

### Card Body

```
Padding:            20px
```

### Card Footer (Optional)

```
Background:         #F8F9FA
Padding:            16px 20px
Border Top:         1px solid #DEE2E6
Text Align:         Right
```

### Card Hover (Optional)

```
Box Shadow:         0 2px 8px rgba(0, 0, 0, 0.12)
Cursor:             pointer (if clickable)
Transition:         200ms
```

## Tables

### Table Container

```
Background:         #FFFFFF
Border:             1px solid #DEE2E6
Border Radius:      8px
Overflow:           Hidden
Width:              100%
```

### Table Header

```
Background:         #F8F9FA
Font Weight:        600
Font Size:          13px
Padding:            12px 16px
Border Bottom:      1px solid #DEE2E6
Color:              #212529
Text Align:         Left (default)
Sticky:             Yes (if scrollable)
```

### Table Row (Default)

```
Padding:            12px 16px
Border Bottom:      1px solid #DEE2E6
Height:             44px
Hover State:        Background #F1F3F5
Transition:         150ms
```

### Table Row (Striped)

```
Alternate Rows:     Background #F8F9FA
Improves:           Readability for many rows
```

### Table Cell (Data)

```
Padding:            12px 16px
Font Size:          14px
Color:              #212529
Vertical Align:     Middle
```

### Table Cell (Numeric)

```
Text Align:         Right
Font Weight:        500
Padding Right:      24px
```

### Table Cell (Status)

```
Display:            Badge (see Components)
Text Align:         Center
Width:              Auto
```

### Table Pagination

```
Position:           Bottom right of table
Margin Top:         16px
Font Size:          13px
Items Per Page:     Options: 10, 25, 50, 100
Display Info:       "Showing 1 to 10 of 250"
```

## Footer

### Dimensions

```
Height:             60px
Background:         #F8F9FA
Border Top:         1px solid #DEE2E6
Position:           Fixed, bottom
Width:              100%
```

### Footer Content

```
Text Align:         Center
Padding:            16px 24px
Font Size:          12px
Color:              #6C757D
Display:            © 2026 FFixiT-MS | Version 1.0
```

## Spacing System (4px Grid)

### Consistent Spacing

```
2xs:    4px    (minimal gap)
xs:     8px    (tight spacing)
sm:     12px   (small spacing)
md:     16px   (medium, most common)
lg:     20px   (large spacing)
xl:     24px   (extra large)
xxl:    32px   (very large)
xxxl:   40px   (maximum spacing)
```

### Vertical Spacing

```
Section to Section:     32px
Component to Component: 24px
Element to Element:     16px
Internal Padding:       16px
```

### Horizontal Spacing

```
Container Padding:      24px (desktop), 20px (tablet), 16px (mobile)
Card Padding:           20px
Table Cell Padding:     12px left/right, 12px top/bottom
Button Padding:         8px 16px (medium), 6px 12px (small)
```

## Container Widths

### Fixed Breakpoints

```
Desktop (1920px+):      Full width - 260px (sidebar) = 1660px available
Desktop (1366px):       Full width - 260px = 1106px available
Tablet (768px):         Full width - 260px = 508px available
Mobile (375px):         Full width (sidebar collapsed)

Max Content Width:      None (use full available space)
Sidebar Width:          260px (fixed, all breakpoints except mobile)
```

## Grid System

### Bootstrap 5 Grid (12 Column)

```
Usage:              Bootstrap's default 12-column grid
Gutter:             24px (12px left + 12px right)
Column Width:       Calculated automatically

Example 2-Column:   col-md-6 (50% width)
Example 3-Column:   col-md-4 (33.33% width)
Example 4-Column:   col-md-3 (25% width)
Example 6-Column:   col-md-2 (16.67% width)
```

---

# 5. UI Components

## Buttons

### Button Variants

#### Primary Button

```
Color Scheme:       #0D6EFD (blue background) / #FFFFFF (white text)
Padding:            8px 16px (medium)
Font Size:          14px
Font Weight:        600
Border:             None
Border Radius:      6px
Cursor:             pointer
State Default:      #0D6EFD
State Hover:        #0A58CA (darker blue)
State Active:       #0A58CA with pressed effect
State Disabled:     #E9ECEF (gray bg) + #999999 (gray text)
Transition:         200ms background-color
Usage:              Main actions (Save, Create, Start Service)
```

#### Success Button

```
Color Scheme:       #198754 (green)
Hover:              #146C43 (darker green)
Usage:              Confirm, Approve, Accept, Finish
```

#### Danger Button

```
Color Scheme:       #DC3545 (red)
Hover:              #BB2D3B (darker red)
Usage:              Delete, Cancel, Reject, Stop
```

#### Warning Button

```
Color Scheme:       #FFC107 (yellow)
Hover:              #FFBB33 (slightly darker)
Text Color:         #212529 (dark text on light background)
Usage:              Edit, Request Changes, Caution
```

#### Secondary Button

```
Color Scheme:       #6C757D (gray)
Hover:              #5C636A (darker gray)
Usage:              Back, Close, Optional Actions
```

#### Info Button

```
Color Scheme:       #0DCAF0 (cyan)
Hover:              #0AA2C0 (darker cyan)
Usage:              More Info, Help, Details
```

#### Link Button (Text-only)

```
Background:         Transparent
Color:              #0D6EFD (primary)
Text Decoration:    None (default), underline (hover)
Hover Color:        #0A58CA
Font Weight:        400
Padding:            0
Usage:              Secondary actions, inline links
```

### Button Sizes

#### Large Button

```
Padding:            12px 24px
Font Size:          16px
Height:             48px
Usage:              Critical actions, primary CTAs
```

#### Medium Button (Default)

```
Padding:            8px 16px
Font Size:          14px
Height:             40px
Usage:              Most common, standard actions
```

#### Small Button

```
Padding:            6px 12px
Font Size:          12px
Height:             32px
Usage:              Inline actions, table row actions, compact layouts
```

### Button State Transitions

```
Idle:               Base color + pointer cursor
Hover:              Darker shade (20% darker) + pointer cursor
Focus:              2px solid primary outline
Active/Pressed:     Even darker shade + inset shadow effect
Disabled:           Gray background + gray text + not-allowed cursor
Loading:            Show spinner inside button + disabled state
```

## Cards

### Basic Card Structure

```
┌─────────────────────────────────┐
│  Card Title         [Action]    │  ← Header (optional)
├─────────────────────────────────┤
│                                 │
│      Card Content               │  ← Body
│                                 │
├─────────────────────────────────┤
│              [Action Button]    │  ← Footer (optional)
└─────────────────────────────────┘
```

### Card Variations

#### Data Card

```
Purpose:            Display key metrics or information
Layout:             Icon + Title + Large Number + Small Label
Example:            Total Tickets: 24 | In Progress: 5
No Border:          Can have colored left border accent
```

#### Stat Card

```
Purpose:            Dashboard statistics
Layout:             Title + Large Number + Trend Indicator
Trend:              ↑ Green (increase) | ↓ Red (decrease)
Color:              Colored top border or background tint
```

#### Action Card

```
Purpose:            Call-to-action or clickable item
Layout:             Icon + Title + Description + Button
Hover State:        Raised shadow, cursor pointer
Clickable:          Entire card or just button
```

#### Status Card

```
Purpose:            Show current status or summary
Layout:             Title + Status Badge + Info List
Example:            Current Tickets | Status: Waiting | By: Irfan
```

### Card States

```
Default:            White background, subtle border shadow
Hover:              Slightly raised (0 2px 8px shadow)
Selected:           Left border 4px primary color
Disabled:           Opacity 0.6 + not-allowed cursor
Loading:            Spinner overlay
Error:              Left border red, optional error badge
```

## Tables

### Table Structure

```
┌────────────────────────────────────────────────────────────────┐
│  Column 1    Column 2      Column 3      Column 4      Action  │  ← Header
├────────────────────────────────────────────────────────────────┤
│  Data        Data          Data          Data          [•••]   │  ← Row 1
├────────────────────────────────────────────────────────────────┤
│  Data        Data          Data          Data          [•••]   │  ← Row 2 (Striped)
├────────────────────────────────────────────────────────────────┤
│  Data        Data          Data          Data          [•••]   │  ← Row 3
├────────────────────────────────────────────────────────────────┤
│  Data        Data          Data          Data          [•••]   │  ← Row 4 (Striped)
└────────────────────────────────────────────────────────────────┘
     < 1 2 3 >  Showing 1 to 10 of 250  [10 ▾]  [First] [Last]
```

### Table Features

#### Striping

```
Enabled:            Alternate row backgrounds (#F8F9FA)
Purpose:            Improves readability for many rows
Applies to:         All data rows (not header/footer)
```

#### Sorting

```
Indicator:          ↑ ↓ ← Arrow in column header
Default:            No sort icon (neutral state)
On Click:           Toggle between ↑ (asc) and ↓ (desc)
Hover:              Highlight header, show cursor pointer
Active:             Bold header + darker background
```

#### Filtering

```
Location:           Above table (optional)
Style:              Search box + Filter dropdowns
Resets:             Clear button to reset all
Updates:            Instant (no submit button needed)
```

#### Pagination

```
Position:           Bottom right of table
Format:             "Showing X to Y of Z" + Previous/Next + Page selector
Items Per Page:     Default 10 | Options: 10, 25, 50, 100
Pages:              Maximum 5 page buttons visible
Navigation:         [< Previous] [1] [2] [3] [4] [Next >]
```

#### Row Actions

```
Position:           Rightmost column (sticky)
Buttons:            View (info) | Edit (pencil) | Delete (trash)
Hover State:        Show action buttons more prominently
Icons:              Bootstrap Icons only
Confirmation:       Delete requires confirmation modal
```

### Table Cell Types

#### Text Cell

```
Alignment:          Left
Padding:            12px 16px
Vertical Align:     Middle
Overflow:           Truncate with ellipsis (if needed)
Max Width:          Defined per column
```

#### Numeric Cell

```
Alignment:          Right
Padding:            12px 24px (more right padding)
Font Weight:        500
Color:              #212529
Prefix/Suffix:      Rp, %, etc.
```

#### Status Cell

```
Content:            Badge component
Alignment:          Center
Background:         Colored based on status
Padding:            6px 12px
```

#### Date Cell

```
Format:             DD MMM YYYY (e.g., 09 Jul 2026)
Alignment:          Left
Padding:            12px 16px
Monospace:          Optional for consistency
```

#### Action Cell

```
Display:            Icon buttons or dropdown menu
Alignment:          Center or Right
Icons:              View, Edit, Delete, More
Hover:              Icons become more prominent
```

## Badges

### Badge Structure

```
Display:            Inline-block label with background color
Padding:            4px 8px
Font Size:          12px
Font Weight:        600
Border Radius:      12px (pill-shaped)
Color:              White text (on colored background)
```

### Badge Types (see Ticket Status Design for specific uses)

#### Primary Badge

```
Background:         #0D6EFD
Color:              #FFFFFF
Usage:              General labels, categorization
```

#### Success Badge

```
Background:         #198754
Color:              #FFFFFF
Usage:              Completed, approved, active
```

#### Danger Badge

```
Background:         #DC3545
Color:              #FFFFFF
Usage:              Error, cancelled, inactive
```

#### Warning Badge

```
Background:         #FFC107
Color:              #212529 (dark text on light bg)
Usage:              Pending, caution, warning
```

#### Info Badge

```
Background:         #0DCAF0
Color:              #212529 (dark text on light bg)
Usage:              Information, neutral status
```

#### Light Badge

```
Background:         #F8F9FA
Color:              #212529 (dark text)
Border:             1px solid #DEE2E6
Usage:              Muted information
```

## Alerts

### Alert Structure

```
┌──────────────────────────────────────────────────────┐
│ Icon  Alert Title                           [Close]  │
│       Alert message or description                   │
└──────────────────────────────────────────────────────┘
```

### Alert Types

#### Success Alert

```
Background:         #D1E7DD (light green)
Border:             1px solid #BADBCC
Text Color:         #0F5132 (dark green)
Icon:               ✓ (check)
Usage:              Action completed, ticket finished, approval granted
```

#### Danger Alert

```
Background:         #F8D7DA (light red)
Border:             1px solid #F5C2C7
Text Color:         #842029 (dark red)
Icon:               ✕ (times)
Usage:              Error, ticket cancelled, operation failed
```

#### Warning Alert

```
Background:         #FFF3CD (light yellow)
Border:             1px solid #FFECB5
Text Color:         #664D03 (dark brown)
Icon:               ⚠ (warning)
Usage:              Caution, waiting approval, incomplete action
```

#### Info Alert

```
Background:         #CFF4FC (light cyan)
Border:             1px solid #B6EFFB
Text Color:         #055160 (dark cyan)
Icon:               ℹ (info)
Usage:              Information, tip, neutral notification
```

### Alert Features

```
Close Button:       [×] button (top right), optional
Padding:            12px 16px
Border Radius:      6px
Font Size:          14px
Icon Size:          18px (left side)
Dismissable:        Optional (set in code)
Auto Hide:          Optional timer (e.g., 5 seconds)
```

## Modals

### Modal Structure

```
┌───────────────────────────────────────┐
│  Modal Title              [×] Close   │  ← Header
├───────────────────────────────────────┤
│                                       │
│    Modal Body (Form / Message)        │  ← Content
│                                       │
├───────────────────────────────────────┤
│         [Cancel]  [Confirm Action]    │  ← Footer
└───────────────────────────────────────┘
```

### Modal Dimensions

```
Desktop:            Min 400px, Max 600px width | Center screen
Tablet:             Min 350px, Max 90% width | Center screen
Mobile:             100% width - 32px margin | Full height
Overlay:            Darken background (rgba(0,0,0,0.5))
```

### Modal Types

#### Confirmation Modal

```
Title:              "Confirm Action"
Body:               Clear question or warning message
Buttons:            [Cancel] [Confirm]
Example:            "Are you sure you want to cancel this ticket?"
```

#### Form Modal

```
Title:              "Create / Edit [Item]"
Body:               Form with inputs
Buttons:            [Cancel] [Save]
Validation:         Show inline errors
```

#### Alert Modal

```
Title:              "Success / Error / Warning"
Body:               Status message
Buttons:            [Close] or [OK]
Auto-Close:         Optional (5-10 seconds for success)
```

#### Loading Modal

```
Title:              Optional
Body:               Spinner + "Processing..."
Buttons:            None (overlay blocks interaction)
Dismissable:        No
```

## Forms

### Form Structure

```
┌─────────────────────────────────────┐
│  Form Title                         │
├─────────────────────────────────────┤
│  Label ⓘ                           │
│  [Input Field]                      │  ← Input Group
│  Helper text or error message       │
│                                     │
│  Label                              │
│  [Textarea]                         │
│                                     │
│  Label                              │
│  [Select Dropdown]                  │
│                                     │
│  ☑ Checkbox Label                   │
│  ☑ Another Checkbox                 │
│                                     │
│  ○ Radio Label                      │
│  ○ Another Radio                    │
│                                     │
│       [Cancel]  [Save]              │
└─────────────────────────────────────┘
```

### Form Layout

```
Vertical Layout:    Default (mobile-friendly)
Label Position:     Above input field
Label Font:         13px, 600 weight, #212529 color
Required Marker:    Red asterisk * (left of label)
Helper Text:        Gray small text below input
Error Message:      Red text below input + red border on field
Spacing:            16px between form groups
```

### Form Input

#### Text Input

```
Height:             40px (include padding)
Padding:            8px 12px
Border:             1px solid #DEE2E6
Border Radius:      6px
Font Size:          14px
Placeholder:        #AAAAAA (light gray)
Focus State:        Blue border (2px) + box-shadow
Disabled State:     Gray background + not-allowed cursor
Valid State:        Green border (1px) + checkmark icon
Error State:        Red border (1px) + error icon
```

#### Password Input

```
Same as Text Input
Show/Hide Toggle:   Eye icon on right
Icon Color:         #6C757D
Icon Clickable:     Toggle visibility on click
```

### Form Textarea

#### Textarea

```
Height:             120px minimum
Padding:            8px 12px
Border:             1px solid #DEE2E6
Border Radius:      6px
Font Size:          14px
Font Family:        System font (same as input)
Resize:             Vertical only (not horizontal)
Line Height:        1.5
Placeholder:        #AAAAAA
Focus/Error:        Same as text input
Character Count:    Optional below field
Max Length:         Enforce in code
```

### Form Select

#### Select Dropdown

```
Height:             40px
Padding:            8px 12px
Border:             1px solid #DEE2E6
Border Radius:      6px
Background:         #FFFFFF with dropdown arrow
Font Size:          14px
Focus State:        Blue border + box-shadow
Disabled State:     Gray background
Option Height:      40px
Option Padding:     12px 16px
Option Hover:       Light blue background
Option Selected:    Blue background + checkmark
```

### Form Checkbox

#### Checkbox

```
Size:               18px × 18px
Border:             1px solid #DEE2E6
Border Radius:      4px
Checked State:      Blue background (#0D6EFD) + white checkmark
Hover State:        Lighter blue background
Focus State:        Blue outline
Disabled State:     Gray background + not-allowed cursor
Label Spacing:      8px right of checkbox
Label Font:         14px regular
```

### Form Radio

#### Radio Button

```
Size:               18px diameter
Border:             2px solid #DEE2E6
Checked State:      Blue border + blue inner circle
Hover State:        Lighter blue border
Focus State:        Blue box-shadow outline
Disabled State:     Gray border + not-allowed cursor
Label Spacing:      8px right of radio
Label Font:         14px regular
```

### Form Submit

```
Position:           Bottom of form
Button Style:       Primary button (blue)
Button Text:        "Save", "Submit", "Create" (context-specific)
Cancel Button:      Secondary button (gray) to left of submit
Spacing:            8px between buttons, 16px from form edge
Loading State:      Disable button + show spinner during submission
```

## Breadcrumb

### Breadcrumb Structure

```
Home / Ticket / TK-001 / Diagnosis

├─ Home              ← Clickable link (primary color)
├─ /                 ← Separator (light gray)
├─ Ticket            ← Clickable link (primary color)
├─ /                 ← Separator
├─ TK-001            ← Clickable link (primary color)
├─ /                 ← Separator
└─ Diagnosis         ← Current page (not clickable, gray)
```

### Breadcrumb Styling

```
Font Size:          13px
Font Weight:        400
Color (Link):       #0D6EFD (primary)
Color (Separator):  #DEE2E6 (border color)
Color (Current):    #6C757D (secondary)
Padding:            8px 0
Line Height:        1.5
Overflow:           Truncate parent items if needed (show first + ... + last)
```

## Pagination

### Pagination Structure

```
Info                          Navigation                    Selector
Showing 1 to 10 of 250        [< Previous] [1] [2] [3] [4] [Next >]     [10 ▾]
```

### Pagination Components

#### Info Text

```
Font Size:          13px
Color:              #6C757D
Display:            "Showing X to Y of Z"
Alignment:          Left
```

#### Page Buttons

```
Size:               36px × 36px (square)
Font Size:          13px
Font Weight:        500
Border:             1px solid #DEE2E6
Margin:             0 2px
Border Radius:      4px

Default State:      White background, dark text
Current Page:       Blue background (#0D6EFD), white text
Hover State:        Blue background (even non-current pages)
Disabled State:     Gray background, gray text, not-allowed cursor
```

#### Navigation Buttons

```
Text:               [< Previous] or [Next >]
Style:              Same as page buttons
Disabled:           When on first/last page
```

#### Items Per Page Selector

```
Component:          Dropdown select
Options:            10, 25, 50, 100
Default:            10
Alignment:          Right
Font Size:          13px
Display:            "[10 ▾]"
```

## Dropdown Menu

### Dropdown Structure

```
Trigger Button: [▼ User Menu]
                ├─ My Profile
                ├─ Settings
                ├─ ─────────── (divider)
                └─ Logout
```

### Dropdown Styling

```
Background:         #FFFFFF
Border:             1px solid #DEE2E6
Border Radius:      6px
Box Shadow:         0 2px 8px rgba(0,0,0,0.12)
Position:           Below/above trigger (auto)
Min Width:          200px

Menu Item:
  Padding:          12px 16px
  Font Size:        14px
  Color:            #212529
  Hover:            Background #F8F9FA
  Height:           40px

Divider:
  Height:           1px
  Background:       #DEE2E6
  Margin:           4px 0

Icon:
  Size:             16px
  Margin Right:     8px
```

## Status Badge

### Status Badge (Visual)

```
Format:             [Color Dot] Status Text
Display:            Inline-block with background
Padding:            6px 12px
Border Radius:      16px (pill)
Font Size:          12px
Font Weight:        600
Width:              Auto (fit content)
```

### Status Colors

#### Waiting Technician

```
Color:              #FFC107 (Warning)
Background:         #FFF3CD (light yellow)
Text:               #664D03 (dark brown)
Icon Dot:           ⏳ (hourglass)
```

#### Diagnosis

```
Color:              #0DCAF0 (Info)
Background:         #CFF4FC (light cyan)
Text:               #055160 (dark cyan)
Icon Dot:           🔍 (magnifying glass)
```

#### Waiting Customer Approval

```
Color:              #FFC107 (Warning)
Background:         #FFF3CD (light yellow)
Text:               #664D03 (dark brown)
Icon Dot:           ⏳ (hourglass)
```

#### In Progress

```
Color:              #0D6EFD (Primary)
Background:         #E7F1FF (light blue)
Text:               #0A3161 (dark blue)
Icon Dot:           ⚙ (gear)
```

#### Finished

```
Color:              #198754 (Success)
Background:         #D1E7DD (light green)
Text:               #0F5132 (dark green)
Icon Dot:           ✓ (checkmark)
```

#### Waiting Payment

```
Color:              #FFC107 (Warning)
Background:         #FFF3CD (light yellow)
Text:               #664D03 (dark brown)
Icon Dot:           💳 (credit card)
```

#### Paid

```
Color:              #198754 (Success)
Background:         #D1E7DD (light green)
Text:               #0F5132 (dark green)
Icon Dot:           ✓ (checkmark)
```

#### Closed

```
Color:              #6C757D (Secondary)
Background:         #E9ECEF (light gray)
Text:               #41464B (dark gray)
Icon Dot:           ✓ (checkmark)
```

#### Cancelled

```
Color:              #DC3545 (Danger)
Background:         #F8D7DA (light red)
Text:               #842029 (dark red)
Icon Dot:           ✕ (times)
```

## Loading Spinner

### Spinner Display

```
Type:               Animated circular spinner
Size:               40px × 40px (default), 24px (small), 60px (large)
Animation:          Rotating 360° continuously
Speed:              2 seconds per rotation
Color:              #0D6EFD (primary blue)
Background:         Transparent
Position:           Center of container
```

### Spinner Usage

```
Page Loading:       Full-screen overlay with spinner
Form Submission:    Inside button, show spinner + disable button
Data Table:         Center of table with message "Loading..."
Modal:              Center of modal with "Processing..."
```

## Empty State

### Empty State Design

```
┌─────────────────────────────────────┐
│                                     │
│           📭 (Large Icon)           │
│                                     │
│      No Data Available              │  ← Heading
│                                     │
│  No tickets found. Create your      │  ← Description
│  first ticket to get started.       │
│                                     │
│         [Create Ticket]             │  ← Action Button
│                                     │
└─────────────────────────────────────┘
```

### Empty State Components

#### Icon

```
Size:               64px
Color:              #DEE2E6 (light gray)
Type:               Bootstrap Icon (inbox, folder, etc.)
```

#### Heading

```
Font Size:          18px
Font Weight:        600
Color:              #212529
Margin Bottom:      12px
```

#### Description

```
Font Size:          14px
Color:              #6C757D
Line Height:        1.6
Margin Bottom:      24px
Text Align:         Center
Max Width:          300px
```

#### Action Button

```
Type:               Primary button
Text:               Context-specific (e.g., "Create Ticket")
```

---

# 6. Ticket Status Design

## Status Hierarchy

```
NEW TICKET
    ↓
Waiting Technician ────────────┐
    ↓                           │
Diagnosis                       │
    ↓                           │
Waiting Approval                │
    ├─ APPROVED                 │
    │   ↓                       │
    │ In Progress               │
    │   ↓                       │
    │ Finished                  │
    │   ↓                       │
    │ Waiting Invoice           │
    │   ↓                       │
    │ Paid                      │
    │   ↓                       │
    │ Closed                    │
    │                           │
    └─ REJECTED                 │
        ↓                       │
      Cancelled ←───────────────┘
```

## Status Details

### 1. Waiting Technician

```
Color:              #FFC107 (Warning/Yellow)
Background:         #FFF3CD (light yellow)
Text Color:         #664D03 (dark brown)
Icon:               ⏳ hourglass
Bootstrap Class:    badge bg-warning text-dark
Display:            "Waiting Technician"
Business Meaning:   Ticket created, waiting for technician to pick up
Actions Available:  View, Assign (Admin only)
Duration:           Variable
Next Status:        Diagnosis (when technician takes ticket)
```

### 2. Diagnosis

```
Color:              #0DCAF0 (Info/Cyan)
Background:         #CFF4FC (light cyan)
Text Color:         #055160 (dark cyan)
Icon:               🔍 magnifying-glass
Bootstrap Class:    badge bg-info text-dark
Display:            "Diagnosis"
Business Meaning:   Technician is diagnosing the device
Actions Available:  View, Edit diagnosis, Upload evidence
Duration:           1-2 hours (typical)
Next Status:        Waiting Customer Approval (after diagnosis complete)
```

### 3. Waiting Customer Approval

```
Color:              #FFC107 (Warning/Yellow)
Background:         #FFF3CD (light yellow)
Text Color:         #664D03 (dark brown)
Icon:               ⏳ hourglass
Bootstrap Class:    badge bg-warning text-dark
Display:            "Waiting Approval"
Business Meaning:   Diagnosis sent, awaiting customer approval
Actions Available:  View, Edit (for CS), Follow up
Duration:           1-24 hours (customer decision time)
Next Status:        In Progress (if approved) OR Cancelled (if rejected)
```

### 4. In Progress

```
Color:              #0D6EFD (Primary/Blue)
Background:         #E7F1FF (light blue)
Text Color:         #0A3161 (dark blue)
Icon:               ⚙️ gear
Bootstrap Class:    badge bg-primary
Display:            "In Progress"
Business Meaning:   Technician actively working on device
Actions Available:  Update progress, Add notes, Upload evidence, Request parts
Duration:           2-24 hours (depends on repair complexity)
Next Status:        Finished (when technician completes work)
```

### 5. Finished

```
Color:              #198754 (Success/Green)
Background:         #D1E7DD (light green)
Text Color:         #0F5132 (dark green)
Icon:               ✓ check
Bootstrap Class:    badge bg-success
Display:            "Finished"
Business Meaning:   Service work completed, ready for invoice
Actions Available:  View, Create Invoice, Generate receipt
Duration:           Brief (minutes)
Next Status:        Waiting Invoice
```

### 6. Waiting Invoice

```
Color:              #FFC107 (Warning/Yellow)
Background:         #FFF3CD (light yellow)
Text Color:         #664D03 (dark brown)
Icon:               💳 credit-card
Bootstrap Class:    badge bg-warning text-dark
Display:            "Waiting Invoice"
Business Meaning:   Awaiting invoice creation by CS
Actions Available:  View, Create Invoice
Duration:           Minutes
Next Status:        Paid (after payment)
```

### 7. Paid

```
Color:              #198754 (Success/Green)
Background:         #D1E7DD (light green)
Text Color:         #0F5132 (dark green)
Icon:               ✓ check
Bootstrap Class:    badge bg-success
Display:            "Paid"
Business Meaning:   Payment received, transaction complete
Actions Available:  View, Print receipt, Record warranty
Duration:           Ongoing (warranty period)
Next Status:        Closed
```

### 8. Closed

```
Color:              #6C757D (Secondary/Gray)
Background:         #E9ECEF (light gray)
Text Color:         #41464B (dark gray)
Icon:               ✓ check
Bootstrap Class:    badge bg-secondary
Display:            "Closed"
Business Meaning:   Ticket completed and archived
Actions Available:  View only, View history
Duration:           Permanent (closed state)
Next Status:        None (final state)
```

### 9. Cancelled

```
Color:              #DC3545 (Danger/Red)
Background:         #F8D7DA (light red)
Text Color:         #842029 (dark red)
Icon:               ✕ times
Bootstrap Class:    badge bg-danger
Display:            "Cancelled"
Business Meaning:   Ticket rejected by customer or admin, no service rendered
Actions Available:  View, View cancellation reason
Duration:           Permanent (closed state)
Next Status:        None (final state)
```

## Status Badge Rendering

### In Tables

```
Display:            Inline badge with background
Alignment:          Center or Left (depending on column)
Space:              24px width minimum
Sortable:           Yes (by status value)
Filterable:         Yes (show only specific statuses)
```

### In Cards

```
Display:            Badge in top-right corner
Position:           Absolute positioning on card
Sizing:             Smaller badge (12px font)
Visibility:         Always visible, not clipped
```

### In Timeline

```
Display:            Badge + timestamp + action description
Format:             "Status Change · 09 Jul 2026, 14:30 · Admin Irfan"
Sequence:           Chronological from oldest to newest
Color:              Same as status
```

## Status Transitions (Business Rules)

```
Waiting Technician
├─ → Diagnosis (action: technician takes ticket)
└─ → Cancelled (action: admin cancels)

Diagnosis
├─ → Waiting Approval (action: diagnosis complete)
└─ → Cancelled (action: admin cancels)

Waiting Approval
├─ → In Progress (action: customer approves)
├─ → Cancelled (action: customer rejects, admin approves)
└─ → Cancelled (action: admin cancels)

In Progress
├─ → Finished (action: technician completes)
└─ → Cancelled (action: admin cancels - rare)

Finished
├─ → Waiting Invoice (automatic)
└─ → Cancelled (action: admin cancels - rare)

Waiting Invoice
├─ → Paid (action: CS creates invoice, payment received)
└─ → Cancelled (action: admin cancels - rare)

Paid
└─ → Closed (action: automatic or manual)

Closed
└─ (no transitions)

Cancelled
└─ (no transitions)
```

---

# 7. Icons

## Icon Library

**System**: Bootstrap Icons (v1.x)
**Format**: SVG (recommended), Icon Font (alternative)
**Size Convention**: 16px (small), 20px (medium), 24px (large), 32px (extra large)

## Module Icons

### Dashboard

```
Icon:           house
Size:           20px
Color:          Primary
Usage:          Dashboard menu item, navigation
Description:    Home icon represents main dashboard view
```

### Customer Management

```
Icon:           person
Size:           20px
Color:          Primary
Usage:          Customer menu, customer list, contact info
Description:    Person icon for user/customer management
```

### Service Ticket

```
Icon:           ticket
Size:           20px
Color:          Primary
Usage:          Ticket menu, ticket list, ticket operations
Description:    Ticket icon for service management (Bootstrap Icons: ticket-detailed)
Alternative:    wrench (if ticket icon unavailable)
```

### Inventory Management

```
Icon:           box
Size:           20px
Color:          Primary
Usage:          Inventory menu, stock list, warehouse
Description:    Box icon represents inventory/storage
Alternative:    boxes (for plural items)
```

### Supplier Management

```
Icon:           truck
Size:           20px
Color:          Primary
Usage:          Supplier menu, purchase orders, vendors
Description:    Truck icon represents suppliers and shipments
```

### Direct Sales (POS)

```
Icon:           cash-coin
Size:           20px
Color:          Primary
Usage:          Sales menu, POS transactions, direct sales
Description:    Cash/coin icon represents monetary transactions
```

### Operational Expense

```
Icon:           receipt
Size:           20px
Color:          Primary
Usage:          Expense menu, expense list, operational costs
Description:    Receipt icon for expense tracking
Alternative:    credit-card
```

### Monitoring & Reports

```
Icon:           graph-up
Size:           20px
Color:          Primary
Usage:          Monitoring menu, reports, analytics, KPI
Description:    Graph/chart icon represents data visualization
Alternative:    bar-chart
```

### User Management

```
Icon:           people
Size:           20px
Color:          Primary
Usage:          User menu, employee list, user management
Description:    People icon for user administration
```

### Audit Log

```
Icon:           clock-history
Size:           20px
Color:          Primary
Usage:          Audit menu, activity history, change log
Description:    Clock/history icon for temporal activity tracking
```

### Settings

```
Icon:           gear
Size:           20px
Color:          Primary
Usage:          System settings, configuration, admin tools
Description:    Gear icon universally represents settings
```

## Action Icons

### Create/Add

```
Icon:           plus
Size:           16px (button) / 24px (toolbar)
Color:          Primary
Usage:          New item buttons, "Add" actions
```

### View/Details

```
Icon:           eye
Size:           16px
Color:          Info
Usage:          View button, show details, expand
```

### Edit

```
Icon:           pencil
Size:           16px
Color:          Warning
Usage:          Edit button, modify item
```

### Delete

```
Icon:           trash
Size:           16px
Color:          Danger
Usage:          Delete button, remove item
```

### Download/Export

```
Icon:           download
Size:           16px
Color:          Primary
Usage:          Export data, download file, PDF
```

### Upload

```
Icon:           upload
Size:           16px
Color:          Primary
Usage:          Upload file, attach evidence, add image
```

### Search

```
Icon:           search
Size:           16px
Color:          Secondary
Usage:          Search box, filter, lookup
```

### Menu/More

```
Icon:           three-dots-vertical
Size:           16px
Color:          Secondary
Usage:          More options, dropdown menu, action menu
```

### Print

```
Icon:           printer
Size:           16px
Color:          Primary
Usage:          Print document, generate receipt, print ticket
```

### Settings/Gear

```
Icon:           gear
Size:           16px
Color:          Secondary
Usage:          Configuration, preferences, settings
```

### Help/Information

```
Icon:           question-circle
Size:           16px
Color:          Info
Usage:          Help tooltip, information button, help menu
```

### Close/Exit

```
Icon:           x
Size:           16px
Color:          Secondary
Usage:          Close modal, close notification, exit
```

### Back/Arrow

```
Icon:           arrow-left
Size:           16px
Color:          Primary
Usage:          Back button, previous page, return
```

### Next/Arrow

```
Icon:           arrow-right
Size:           16px
Color:          Primary
Usage:          Next button, forward, proceed
```

## Status Icons

### Success

```
Icon:           check
Size:           16px
Color:          Success
Usage:          Completed, approved, confirmed
```

### Error/Danger

```
Icon:           x-circle
Size:           16px
Color:          Danger
Usage:          Error, failed, cancelled
```

### Warning

```
Icon:           exclamation-triangle
Size:           16px
Color:          Warning
Usage:          Warning, caution, attention needed
```

### Info

```
Icon:           info-circle
Size:           16px
Color:          Info
Usage:          Information, notification, tip
```

### Loading/Spinner

```
Icon:           hourglass-split (animated)
Size:           20px
Color:          Primary
Usage:          Loading, processing, waiting
```

### Clock/Time

```
Icon:           clock
Size:           16px
Color:          Secondary
Usage:          Timestamp, time-related, pending
```

---

# 8. Sidebar Navigation

## Sidebar General Structure

```
┌──────────────────┐
│  FFixiT-MS Logo  │  ← Logo/Branding
├──────────────────┤
│ Menu Item 1      │  ← Main menu items
│ ├─ Sub Item 1    │  ← Submenu (if expanded)
│ ├─ Sub Item 2    │
│ └─ Sub Item 3    │
│ Menu Item 2      │
│ Menu Item 3      │
│ Menu Item 4      │
│                  │
│ (scrollable)     │
│                  │
├──────────────────┤
│  Logout Button   │  ← Fixed at bottom
└──────────────────┘
```

## Navigation for IT (Super Administrator)

```
┌──────────────────────────────┐
│   FFixiT-MS                  │  [Logo]
│   Super Admin                │  [Subtitle]
├──────────────────────────────┤
│ 🏠 Dashboard                 │
├──────────────────────────────┤
│ OPERATIONS                   │  [Section Header]
│ 🎟️  Service Ticket           │
│ 👥 Customer Management       │
│ 📦 Inventory                 │
│ 🚚 Supplier                  │
│ 💰 Direct Sales              │
│ 📝 Operational Expense       │
├──────────────────────────────┤
│ MONITORING                   │  [Section Header]
│ 📊 Monitoring & Reports      │
├──────────────────────────────┤
│ SYSTEM                       │  [Section Header]
│ 👤 User Management           │
│ 🛡️  Role & Permission        │
│ 📋 Audit Log                 │
│ ⚙️  System Configuration      │
├──────────────────────────────┤
│                              │  [Scrollable area]
│                              │
├──────────────────────────────┤
│ 🚪 Logout (IT User)          │
└──────────────────────────────┘
```

## Navigation for Kepala Toko (Manager)

```
┌──────────────────────────────┐
│   FFixiT-MS                  │
│   Manager                    │
├──────────────────────────────┤
│ 🏠 Dashboard                 │
├──────────────────────────────┤
│ MONITORING                   │
│ 📊 Monitoring & Reports      │
│    ├─ Ticket Status         │
│    ├─ Revenue Report        │
│    ├─ Inventory Status      │
│    ├─ KPI Dashboard         │
│    └─ Expense Summary       │
├──────────────────────────────┤
│ OPERATIONS                   │
│ 📝 Operational Expense       │
├──────────────────────────────┤
│                              │
│ (Limited access for         │
│  operational oversight)     │
│                              │
├──────────────────────────────┤
│ 🚪 Logout (Manager)          │
└──────────────────────────────┘
```

## Navigation for Admin Gudang (Warehouse)

```
┌──────────────────────────────┐
│   FFixiT-MS                  │
│   Warehouse Admin            │
├──────────────────────────────┤
│ 🏠 Dashboard                 │
├──────────────────────────────┤
│ INVENTORY                    │
│ 📦 Inventory Management      │
│    ├─ Stock View            │
│    ├─ Barang Masuk          │
│    ├─ Stock Opname          │
│    └─ Stock Adjustment      │
│ 🚚 Supplier Management       │
│    ├─ Supplier List         │
│    ├─ Purchase Order        │
│    └─ Purchase History      │
│ 📋 Master Barang            │
│    ├─ Product List          │
│    ├─ Category              │
│    └─ Product Details       │
├──────────────────────────────┤
│ REQUESTS                     │
│ 🔔 Sparepart Requests       │
├──────────────────────────────┤
│                              │
│ (Focused on inventory)      │
│                              │
├──────────────────────────────┤
│ 🚪 Logout (Warehouse Admin)  │
└──────────────────────────────┘
```

## Navigation for Customer Service (CS)

```
┌──────────────────────────────┐
│   FFixiT-MS                  │
│   Customer Service           │
├──────────────────────────────┤
│ 🏠 Dashboard                 │
├──────────────────────────────┤
│ SERVICE                      │
│ 🎟️  Service Ticket           │
│    ├─ Create Ticket         │
│    ├─ Ticket List           │
│    ├─ Pending Approval      │
│    └─ Invoice Pending       │
│ 👥 Customer Management       │
│    ├─ Customer List         │
│    ├─ Add Customer          │
│    └─ Customer History      │
├──────────────────────────────┤
│ SALES                        │
│ 💰 Direct Sales (POS)       │
│    ├─ Create Invoice        │
│    ├─ Sales History         │
│    └─ Refund                │
├──────────────────────────────┤
│ REPORTS                      │
│ 📊 Invoice Report            │
├──────────────────────────────┤
│                              │
│ (Customer-facing operations) │
│                              │
├──────────────────────────────┤
│ 🚪 Logout (CS)               │
└──────────────────────────────┘
```

## Navigation for Teknisi (Technician)

```
┌──────────────────────────────┐
│   FFixiT-MS                  │
│   Technician                 │
├──────────────────────────────┤
│ 🏠 Dashboard                 │
├──────────────────────────────┤
│ MY WORK                      │
│ 🎟️  My Tickets               │
│    ├─ Assigned to Me        │
│    ├─ In Progress           │
│    ├─ Completed             │
│    └─ Pending               │
├──────────────────────────────┤
│ ACTIONS                      │
│ 🔍 Diagnosis                 │
│ 📊 Progress Service          │
│ 📸 Evidence Upload           │
│ 🔔 Request Sparepart         │
├──────────────────────────────┤
│                              │
│ (Simple, task-focused)       │
│                              │
├──────────────────────────────┤
│ 🚪 Logout (Technician)       │
└──────────────────────────────┘
```

## Sidebar Interaction Patterns

### Menu Expansion

```
Single-Click:       Expand/collapse submenu
Default:            Collapsed (except current section)
Animation:          Smooth slide-down effect (200ms)
Indicator:          Chevron down/up next to menu item
```

### Active State

```
Current Page:       Highlighted menu item
Highlight Style:    Blue background + white text
Left Border:        4px blue accent
Section:            Parent menu also highlighted
```

### Hover State

```
Menu Item Hover:    Light background color
Color:              Slightly lighter than normal
Cursor:             pointer
Transition:         150ms
```

### Mobile Behavior (< 768px)

```
Sidebar:            Collapsed by default
Trigger:            Hamburger menu icon (top-left)
Animation:          Slide-in from left
Overlay:            Semi-transparent overlay on content
Width:              80% of viewport or 260px (whichever is smaller)
Close:              Click overlay or close button
```

---

# 9. Dashboard Widgets

## Dashboard Grid Layout

```
12-Column Bootstrap Grid
Row Height:         Auto (based on content)
Gap:                24px (gutter)
Card Width:         Full width / 50% (2 col) / 33% (3 col) / 25% (4 col)
Responsive:         Stack vertically on smaller screens
```

## Dashboard for IT (Super Administrator)

### Layout

```
Row 1 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │                    SYSTEM STATUS                             │
  └──────────────────────────────────────────────────────────────┘

Row 2 (4 Equal Columns):
  ┌──────────────┬──────────────┬──────────────┬──────────────┐
  │ Total Users  │ Active Users │ System Load  │ Last Backup  │
  └──────────────┴──────────────┴──────────────┴──────────────┘

Row 3 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Ticket Summary (Chart)       │ Operational Summary (Chart)  │
  └──────────────────────────────┴──────────────────────────────┘

Row 4 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Recent Activity Log (Table)                                  │
  └──────────────────────────────────────────────────────────────┘

Row 5 (3 Equal Columns):
  ┌────────────────┬────────────────┬────────────────┐
  │ Backup Status  │ System Health  │ Update Check   │
  └────────────────┴────────────────┴────────────────┘
```

### Widgets

#### Widget 1: System Status (Stat Card)

```
Title:              "System Status"
Display:            System Health: 98% | Uptime: 45 days
Trend:              ↑ +2% (green)
Background:         Green tint
Action:             Click → System Logs
```

#### Widget 2: Total Users (Metric Card)

```
Number:             156 (large)
Label:              "Total Users"
Trend:              +5 this month
Sparkline:          (optional) mini chart
```

#### Widget 3: Active Users (Metric Card)

```
Number:             24 (large)
Label:              "Active Now"
Trend:              (live count)
Status:             Green indicator
```

#### Widget 4: System Load (Gauge Card)

```
Gauge Chart:        Current: 45%
Label:              "CPU Usage"
Range:              0-100%
Color:              Green (< 50%), Yellow (50-75%), Red (> 75%)
```

#### Widget 5: Last Backup (Info Card)

```
Last Backup:        "09 Jul 2026, 02:00 AM"
Duration:           "3 minutes"
Status:             ✓ Success
Next Backup:        "10 Jul 2026, 02:00 AM"
```

#### Widget 6: Ticket Summary Chart (Line/Bar Chart)

```
Chart Type:         Line chart (trend) or Bar chart (distribution)
X-Axis:             Days of week / Last 7 days
Y-Axis:             Ticket count
Lines:              New | In Progress | Completed
Legend:             Color-coded
Tooltip:            Show exact values on hover
```

#### Widget 7: Operational Summary Chart (Pie Chart)

```
Chart Type:         Pie or Donut chart
Slices:             Revenue | Expenses | Profit
Colors:             Primary, Success, Danger
Legend:             Right side
Percentage:         Shown on each slice
Tooltip:            Show rupiah amount on hover
```

#### Widget 8: Recent Activity Log (Table)

```
Columns:            Timestamp | User | Action | Status
Rows:               Last 10 activities
Height:             Scrollable (5-10 rows visible)
Colors:             Based on action type (success/warning/danger)
Search:             Filter by user or action
```

#### Widget 9: Backup Status (Status Card)

```
Status:             ✓ Active
Last Run:           09 Jul 2026, 02:00 AM
Next Run:           10 Jul 2026, 02:00 AM
Retention:          30 days
```

#### Widget 10: System Health (Score Card)

```
Score:              98 / 100
Factors:            Uptime ✓ | CPU ✓ | Memory ✓ | Disk ⚠
Issues:             None
Recommendation:     (if any)
```

#### Widget 11: Update Check (Action Card)

```
Status:             ✓ Up to date
Current:            v1.0.0
Latest:             v1.0.0
Check:              [Check Now] button
```

---

## Dashboard for Kepala Toko (Manager)

### Layout

```
Row 1 (4 Equal Columns):
  ┌──────────────┬──────────────┬──────────────┬──────────────┐
  │ Today Omzet  │ This Month   │ Avg Service  │ Tickets Due  │
  └──────────────┴──────────────┴──────────────┴──────────────┘

Row 2 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Revenue Trend (Chart)        │ Ticket Status (Bar Chart)    │
  └──────────────────────────────┴──────────────────────────────┘

Row 3 (3 Equal Columns):
  ┌────────────────┬────────────────┬────────────────┐
  │ Expense Today  │ Top Expenses   │ KPI Summary    │
  └────────────────┴────────────────┴────────────────┘

Row 4 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Top Performing Technicians (Table)                           │
  └──────────────────────────────────────────────────────────────┘

Row 5 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Inventory Alert              │ Action Items                 │
  └──────────────────────────────┴──────────────────────────────┘
```

### Widgets

#### Widget 1: Today Omzet (Large Metric)

```
Number:             Rp 2.450.000 (large, bold)
Label:              "Today's Revenue"
Trend:              ↑ +15% vs yesterday
Badge:              Green success
```

#### Widget 2: This Month (Metric Card)

```
Number:             Rp 45.670.000
Label:              "This Month"
Target:             Rp 50.000.000 (progress bar)
Progress:           91%
```

#### Widget 3: Avg Service Time (Metric Card)

```
Number:             2.5 hours
Label:              "Average Service Time"
Trend:              ↓ -0.3 hours (improvement)
```

#### Widget 4: Tickets Due Today (Alert Card)

```
Number:             8
Label:              "Tickets Due Today"
Severity:           Yellow (warning)
Action:             [View All]
```

#### Widget 5: Revenue Trend Chart (Line Chart)

```
Chart Type:         Line chart
X-Axis:             Last 30 days
Y-Axis:             Revenue (Rupiah)
Line Color:         Primary blue
Fill:               Light blue area
Tooltip:            Show date + amount
Legend:             "Daily Revenue"
```

#### Widget 6: Ticket Status Distribution (Bar Chart)

```
Chart Type:         Horizontal bar chart
Categories:         Waiting | Diagnosis | In Progress | Finished | Paid
Bars:               Color-coded by status
Values:             Count of tickets in each status
Tooltip:            Show exact count
```

#### Widget 7: Expense Today (Metric Card)

```
Number:             Rp 125.000
Label:              "Operational Expense Today"
Color:              Orange/warning
```

#### Widget 8: Top Expenses (List Card)

```
List Items:
  1. Rental - Rp 50.000
  2. Electricity - Rp 35.000
  3. Internet - Rp 25.000
  4. Supplies - Rp 15.000
Color:              Each item has category color
```

#### Widget 9: KPI Summary (Stats Grid)

```
Stats:
  - Customer Satisfaction: 92%
  - Technician Efficiency: 87%
  - On-Time Delivery: 94%
  - Return Rate: 2%
Colors:             Green (> 85%), Yellow (70-85%), Red (< 70%)
```

#### Widget 10: Top Performing Technicians (Table)

```
Columns:            Rank | Name | Tickets | Completed | Rating
Rows:               Top 5 technicians
Sort:               By tickets completed
Color:              Row highlight for top performer
```

#### Widget 11: Inventory Alert (Alert Card)

```
Items Low:          5 items below minimum
Critical:           2 items out of stock
Action:             [View Inventory]
Color:              Red for critical, Yellow for low
```

#### Widget 12: Action Items (Task List)

```
Items:
  ☐ Review pending approvals (3)
  ☐ Check inventory reorder (5 items)
  ☐ Approve overtime requests (2)
Checkboxes:         Clickable to mark done
```

---

## Dashboard for Admin Gudang (Warehouse)

### Layout

```
Row 1 (4 Equal Columns):
  ┌──────────────┬──────────────┬──────────────┬──────────────┐
  │ Total Items  │ Low Stock    │ Overstock    │ Recent Adds  │
  └──────────────┴──────────────┴──────────────┴──────────────┘

Row 2 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Stock Movement (Line Chart)  │ Category Distribution (Pie)  │
  └──────────────────────────────┴──────────────────────────────┘

Row 3 (3 Equal Columns):
  ┌────────────────┬────────────────┬────────────────┐
  │ Pending Orders │ Sparepart Req. │ Stock Opname   │
  └────────────────┴────────────────┴────────────────┘

Row 4 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Stock Alert Summary (Alert List)                             │
  └──────────────────────────────────────────────────────────────┘

Row 5 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Recent Stock Movements (Table)                               │
  └──────────────────────────────────────────────────────────────┘
```

### Widgets

#### Widget 1: Total Items (Metric Card)

```
Number:             8,456
Label:              "Total Unique Items"
Trend:              ↑ +12 this week
```

#### Widget 2: Low Stock (Alert Card)

```
Number:             47
Label:              "Items Below Minimum"
Severity:           Yellow warning
Action:             [View & Order]
```

#### Widget 3: Overstock (Warning Card)

```
Number:             15
Label:              "Overstocked Items"
Severity:           Yellow/warning
Action:             [Review]
Recommendation:     Consider promotional sale
```

#### Widget 4: Recent Adds (Metric Card)

```
Number:             23
Label:              "Items Added This Week"
Trend:              Last 7 days
```

#### Widget 5: Stock Movement Chart (Line Chart)

```
Chart Type:         Line chart
X-Axis:             Last 30 days
Y-Axis:             Unit count
Lines:              In | Out | Net (stacked area)
Tooltip:            Show daily movements
Legend:             Color-coded by type
```

#### Widget 6: Category Distribution (Pie Chart)

```
Chart Type:         Pie chart
Slices:             Each product category
Colors:             Distinct colors
Percentage:         Shown on each slice
Tooltip:            Category name + count + percentage
```

#### Widget 7: Pending Orders (Action Card)

```
Number:             5
Label:              "Purchase Orders Pending"
Severity:           Blue info
Oldest:             "3 days waiting"
Action:             [Follow Up]
```

#### Widget 8: Sparepart Requests (Alert Card)

```
Number:             8
Label:              "Pending Sparepart Requests"
Severity:           Orange warning
Priority:           "2 URGENT" badge
Action:             [View Requests]
```

#### Widget 9: Stock Opname (Status Card)

```
Status:             "Last Opname: 30 Jun 2026"
Days Ago:           9 days
Next Due:           15 Jul 2026
Action:             [Start Opname]
```

#### Widget 10: Stock Alert Summary (Alert List)

```
Items:
  🔴 CRITICAL - SSD 240GB: 0 units (out of stock)
  🟡 WARNING - RAM 8GB: 2 units (min: 5)
  🟡 WARNING - Thermal Paste: 1 unit (min: 10)
  🔵 INFO - New item: Ryzen 5 2600 (15 units added)
Each item: Clickable to view details
```

#### Widget 11: Recent Stock Movements (Table)

```
Columns:            Date | Type | Item | Quantity | By | Reference
Rows:               Last 20 movements
Sortable:           By date, quantity, type
Filter:             By type (In/Out)
Colors:             In = Green | Out = Orange
```

---

## Dashboard for Customer Service (CS)

### Layout

```
Row 1 (4 Equal Columns):
  ┌──────────────┬──────────────┬──────────────┬──────────────┐
  │ My Tickets   │ Pending App. │ Invoices Owe │ Recent Sales │
  └──────────────┴──────────────┴──────────────┴──────────────┘

Row 2 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Ticket Status (Bar Chart)    │ Today's Sales (Metric)       │
  └──────────────────────────────┴──────────────────────────────┘

Row 3 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Today's Tickets (Table)                                      │
  └──────────────────────────────────────────────────────────────┘

Row 4 (2 Columns):
  ┌──────────────────────────────┬──────────────────────────────┐
  │ Follow-Up Needed             │ Customer Callbacks           │
  └──────────────────────────────┴──────────────────────────────┘
```

### Widgets

#### Widget 1: My Tickets (Metric Card)

```
Number:             12
Label:              "My Tickets Today"
Breakdown:          Waiting: 5 | In Progress: 4 | Finished: 3
```

#### Widget 2: Pending Approvals (Alert Card)

```
Number:             3
Label:              "Waiting Customer Approval"
Severity:           Yellow warning
Oldest:             "Since 08:00 AM"
Action:             [View & Follow Up]
```

#### Widget 3: Invoices Owed (Warning Card)

```
Amount:             Rp 2.350.000
Label:              "Unpaid Invoices"
Count:              7 invoices
Action:             [Send Reminder]
```

#### Widget 4: Recent Sales (Metric Card)

```
Amount:             Rp 875.000
Label:              "Today's Direct Sales"
Count:              12 transactions
Trend:              ↑ vs yesterday
```

#### Widget 5: Ticket Status Chart (Bar Chart)

```
Chart Type:         Horizontal bar chart
Status Types:       Waiting | Diagnosis | Approval | In Progress | Finished
Current Count:      Color-coded bars
Total:              "12 tickets"
```

#### Widget 6: Today's Sales (Metric Card)

```
Amount:             Rp 875.000
Transactions:       12
Average:            Rp 72.917 per transaction
Trend:              Current day tracking
```

#### Widget 7: Today's Tickets (Table)

```
Columns:            ID | Customer | Status | Tech | Time In | Action
Rows:               All tickets created/updated today
Sortable:           By time, status
Filter:             By status
Quick Actions:      View, Edit, Call, Print
```

#### Widget 8: Follow-Up Needed (Task List)

```
Items:
  📞 Budi Santoso - Waiting approval since 10:30 AM
  📞 Siti Nurhaliza - Invoice Rp 450.000 unpaid
  📞 Ahmad Rizki - Device ready for pickup
Checkboxes:         Mark as done
Priority:           Urgent items first
```

#### Widget 9: Customer Callbacks (Info Card)

```
Scheduled:          3 callbacks today
Times:              14:00 (Budi), 16:00 (Siti), 17:00 (Ahmad)
Status:             Reminders set
Next Callback:      "Budi - in 30 minutes" (with countdown)
```

---

## Dashboard for Teknisi (Technician)

### Layout

```
Row 1 (4 Equal Columns):
  ┌──────────────┬──────────────┬──────────────┬──────────────┐
  │ My Tickets   │ In Progress  │ Completed    │ Rating       │
  └──────────────┴──────────────┴──────────────┴──────────────┘

Row 2 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ My Work Queue (Ticket Cards / Table)                         │
  └──────────────────────────────────────────────────────────────┘

Row 3 (3 Equal Columns):
  ┌────────────────┬────────────────┬────────────────┐
  │ Time Tracking  │ Sparepart Req. │ My Statistics  │
  └────────────────┴────────────────┴────────────────┘

Row 4 (Full Width):
  ┌──────────────────────────────────────────────────────────────┐
  │ Quick Actions (Action Buttons)                               │
  └──────────────────────────────────────────────────────────────┘
```

### Widgets

#### Widget 1: My Tickets (Metric Card)

```
Number:             7
Label:              "Assigned to Me"
Breakdown:          Waiting: 2 | In Progress: 3 | Completed: 2
```

#### Widget 2: In Progress (Metric Card)

```
Number:             3
Label:              "Currently Working On"
Time In:            1h 30m (current ticket)
Next:               "TK-0089 - Ready when done"
```

#### Widget 3: Completed Today (Metric Card)

```
Number:             2
Label:              "Completed Today"
Avg Time:           2h 15m
Rating:             ⭐ 4.5/5
```

#### Widget 4: My Rating (Score Card)

```
Score:              4.8 / 5.0
Reviews:            24 customer reviews
Trend:              ↑ +0.2 this month
Status:             ⭐ Excellent
```

#### Widget 5: My Work Queue (Card Grid / Table)

```
Display:
  ┌─ TK-0089 ─────────────────────────┐
  │ Customer: Budi Santoso            │
  │ Device: MacBook Pro 13"           │
  │ Issue: Won't power on             │
  │ Time In: 1h 30m                   │
  │ [Update Progress] [Mark Finished] │
  └───────────────────────────────────┘

  ┌─ TK-0090 ─────────────────────────┐
  │ Customer: Siti Nurhaliza          │
  │ Device: Dell XPS 15               │
  │ Issue: Screen flickering          │
  │ Status: Waiting Approval          │
  │ [View] [Call CS]                  │
  └───────────────────────────────────┘

For each card: Show priority, time remaining, quick actions
```

#### Widget 6: Time Tracking (Timer Card)

```
Current Task:       TK-0089
Time:               1h 30m (live timer)
Billable:           Yes / No (toggle)
Status:             On Clock
Controls:           [Pause] [Stop] [Extend]
```

#### Widget 7: Sparepart Requests (Pending Card)

```
Number:             1
Label:              "Pending Sparepart Request"
Item:               "SSD Samsung 256GB"
Requested:          2h ago
Status:             "Waiting warehouse approval"
Estimated:          "Available in 2 hours"
```

#### Widget 8: My Statistics (Stats Card)

```
This Week:
  - Tickets: 15
  - Completed: 14
  - Avg Rating: 4.7/5
  - Efficiency: 93%
This Month:
  - Tickets: 62
  - Completed: 61
  - Avg Rating: 4.8/5
```

#### Widget 9: Quick Actions (Button Grid)

```
[📸 Upload Evidence]  [📝 Update Progress]
[📞 Call CS]          [🔔 Request Sparepart]
[💾 Save Notes]       [✓ Mark Ready]
```

---

# 10. Responsive Rules

## Breakpoint Strategy

### Desktop (1920px and above)

```
Layout:             Full sidebar + full navbar + wide content
Sidebar Width:      260px (fixed)
Content Width:      calc(100% - 260px) = 1660px available
Main Content:       Use 2-3 column layouts
Cards:              4 columns per row (3-column for variety)
Tables:             Show all columns with horizontal scroll if needed
Fonts:              As specified (standard sizes)
Spacing:            Generous 24px padding and margins
Viewport:           Optimized for 1920x1080 primary target

Grid System:
  - 4-column layouts common
  - 2-column for comparison views
  - Full-width for single focus
  - Sidebar navigation with all items visible
```

### Standard Desktop (1366px - 1919px)

```
Layout:             Same as large desktop (sidebar + navbar + content)
Sidebar Width:      260px (fixed)
Content Width:      calc(100% - 260px) = 1106px available
Main Content:       Adjust to 2-3 columns based on space
Cards:              3 columns per row (2-column for variety)
Tables:             Scrollable if needed (horizontal scroll)
Spacing:            Maintain 24px padding
Fonts:              Maintain standard sizes

Adjustments:
  - Less horizontal whitespace
  - Cards may resize to 33% width
  - Table columns may reduce slightly
  - Sidebar remains fixed
```

### Tablet (768px - 1365px)

```
Layout:             Sidebar + navbar + stacked content
Sidebar Width:      260px (fixed)
Content Width:      calc(100% - 260px) = 508px available (768px tablet)
Main Content:       Stack to single column or 2 columns maximum
Cards:              2 columns per row (full width if needed)
Tables:             Simplified (hide less critical columns, show only essential info)
Spacing:            Reduce to 20px padding
Fonts:              Keep same sizes (readable at this distance)

Sidebar:            Remains visible and full-width
Content Cards:
  - 2 columns at 768px
  - Stack to 1 column if needed
  - Full width minus sidebar

Table Adjustments:
  - Hide columns with low priority
  - Show row actions as dropdown menu
  - Increase row height for easier touch targets
  - Make pagination controls larger

Navbar:             Adjust width to accommodate sidebar
```

### Mobile Landscape (667px - 767px)

```
Layout:             Sidebar collapsed + navbar + full-width content
Sidebar Width:      Collapsed (hamburger menu)
Content Width:      100% (full screen width)
Main Content:       Single column stack
Cards:              Full width, stacked vertically
Tables:             Card-based layout (each row becomes a card)
Spacing:            Reduce to 16px padding
Fonts:              Reduce heading sizes slightly

Sidebar Behavior:
  - Hidden by default
  - Hamburger menu in navbar (top-left)
  - Slide-in from left when activated
  - Overlay covers content
  - Swipe left to close
  - Same menu items as desktop

Content Area:
  - Becomes full width
  - Padding reduced to 16px
  - Tables convert to card format
  - Single column layouts

Navbar:             Width = 100% (full width)
  - Compact version of desktop navbar
  - User menu remains accessible
  - Search optional (or move to secondary action)
```

### Mobile Portrait (375px - 666px)

```
Layout:             Sidebar hidden + compact navbar + full-width content
Sidebar Width:      Collapsed (hamburger menu only)
Content Width:      100% - 32px (16px padding each side)
Main Content:       Single column exclusively
Cards:              Full width, stacked
Tables:             Card-view (each row = mini card)
Spacing:            Reduce to 12px between elements
Fonts:              Reduce significantly for readability

Sidebar:
  - Hidden (hamburger menu only)
  - Full height when opened
  - 80% viewport width or 260px (smaller wins)
  - Overlay with semi-transparent background
  - Close on selection or tap outside

Navbar:
  - Height: 56px (smaller than desktop)
  - Logo/title: Text only (no image)
  - User menu: Compressed
  - Breadcrumb: Hidden (show in title area if needed)

Content Adaptations:
  - Single column only
  - Cards: Full width
  - Padding: 12px - 16px
  - Margins: 12px between sections

Form Inputs:
  - Width: 100%
  - Height: 48px (for touch)
  - Font size: 16px (prevent zoom on iOS)
  - Spacing between fields: 16px

Buttons:
  - Min height: 48px (touch target)
  - Width: 100% or side-by-side if 2 buttons
  - Font size: 16px

Tables:
  - Convert to card format
  - One column per row
  - Large touch targets
  - Actions as button row

Images:
  - Responsive: width 100%
  - Max-width: 100vw
  - Height: Auto

Typography:
  - Headings: 18-20px (from 24-32px)
  - Body: 14px (maintain)
  - Small: 12px (maintain)
  - Line height: 1.6 (unchanged)
```

## Responsive Components

### Navbar

```
Desktop:            Full navbar with breadcrumb + search + user menu
Tablet:             Breadcrumb optional, compress user menu
Mobile:             Title only, user menu in dropdown, no breadcrumb
```

### Sidebar

```
Desktop:            Fixed, always visible
Tablet:             Fixed, always visible (260px width maintained)
Mobile:             Collapsed, hamburger menu trigger, slide-in overlay
```

### Content Grid

```
Desktop (4-col):    col-lg-3
Tablet (2-col):     col-md-6
Mobile (1-col):     col-12 (full width)
```

### Tables

```
Desktop:            Full table with all columns
Tablet:             Hide low-priority columns (ID, timestamps optional)
Mobile:             Convert to card view (each row = card)

Card View Format:
  ┌──────────────────┐
  │ Field 1: Value 1 │
  │ Field 2: Value 2 │
  │ Field 3: Value 3 │
  │ [View] [Edit]    │
  └──────────────────┘
```

### Forms

```
Desktop:            Side-by-side fields (2 columns where appropriate)
Tablet:             1-2 columns (reduce to 1 if cramped)
Mobile:             1 column only (vertical stack)

Input Heights:
  Desktop:          40px
  Tablet:           40px
  Mobile:           48px (larger for touch)
```

### Cards

```
Desktop:            4 columns (25% width)
Tablet:             2 columns (50% width)
Mobile:             1 column (100% width)

Spacing:
  Desktop:          24px gap
  Tablet:           20px gap
  Mobile:           16px gap
```

### Buttons

```
Desktop:            Standard sizes (40px height)
Tablet:             Standard sizes (40px height)
Mobile:             Large (48px height) for touch accuracy
  - Min width: 48px
  - Padding: 12px 24px or larger
  - Spacing between buttons: 8px (stack if needed)
```

### Images & Media

```
Desktop:            Max-width defined per component
Tablet:             Responsive width, max 100% of container
Mobile:             Responsive width, max 100vw

Aspect Ratios:      Maintain 4:3, 16:9, or 1:1 as defined
```

## Touch Targets (Mobile)

```
Minimum Size:       48px × 48px (Apple & Google guidelines)
Spacing:            8px minimum between touch targets
Button Height:      48px minimum on mobile
Checkbox/Radio:     18px × 18px (acceptable for experienced users, but 24px preferred)
Input Fields:       48px height (including padding)
Link Text:          Adequate size (14px+ font)
```

## Performance Optimization

```
Desktop:            Load full assets, no optimization needed
Tablet:             Consider lazy loading for images below fold
Mobile:
  - Lazy load images
  - Limit animations (reduce motion)
  - Compress images
  - Minimize JavaScript execution
  - Optimize font loading
  - Use system fonts primarily
```

## Text & Reading

```
Desktop:            Full content, multi-column where appropriate
Tablet:             Full content, adjust column count
Mobile:             Full content, single column
  - Maintain line length < 50 characters per line for readability
  - Increase line spacing if needed (1.6 maintained)
  - Use clear hierarchy

Font Size Hierarchy Mobile:
  H1: 20px (from 32px)
  H2: 18px (from 24px)
  H3: 16px (from 20px)
  Body: 14px (unchanged)
  Small: 12px (unchanged)
```

---

# Color Reference Card

## Bootstrap Default Colors Used

```
Primary Blue:       #0D6EFD
Primary Dark:       #0A58CA
Secondary Gray:     #6C757D
Success Green:      #198754
Danger Red:         #DC3545
Warning Yellow:     #FFC107
Info Cyan:          #0DCAF0
Light:              #F8F9FA
Dark:               #212529
White:              #FFFFFF
```

## Custom Palette Additions

```
Sidebar Dark:       #2C3E50
Sidebar Hover:      #34495E
Sidebar Active:     #0D6EFD
Border Light:       #DEE2E6
Hover BG:           #F1F3F5
Disabled BG:        #E9ECEF
Muted Text:         #999999
```

---

---

# FFixiT Design Rules

FFixiT-MS merupakan sistem operasional toko komputer. Seluruh desain antarmuka harus mengutamakan efisiensi kerja dibandingkan tampilan dekoratif.

Prinsip utama:

- Speed over Decoration
- Data Visibility over Animation
- Desktop First
- Minimal Click
- Consistent Layout
- Easy to Learn
- Responsive
- Professional Appearance

Setiap halaman harus membantu pengguna menyelesaikan pekerjaan dengan langkah sesedikit mungkin.

---

# Page Layout Standard

Setiap halaman utama wajib menggunakan struktur berikut.

```
Sidebar
    │
Top Navigation
    │
Breadcrumb
    │
Page Title
    │
Action Button
    │
Search & Filter
    │
Main Content
    │
Pagination
```

Urutan layout tidak boleh diubah tanpa alasan yang jelas.

---

# Dashboard Standard

Seluruh Dashboard menggunakan struktur yang sama.

```
Summary Cards
      │
      ▼
Charts
      │
      ▼
Recent Activity
      │
      ▼
Latest Transactions
      │
      ▼
Quick Actions
```

Perbedaan setiap Dashboard hanya terletak pada data yang ditampilkan sesuai Role.

---

# Form Design Rules

Semua Form harus mengikuti aturan berikut.

- Label berada di atas Input.
- Field wajib diberi tanda (\*).
- Placeholder hanya digunakan jika diperlukan.
- Error Validation ditampilkan tepat di bawah field.
- Button Save berada di kanan bawah.
- Button Cancel berada di sebelah kiri Save.
- Form menggunakan maksimal dua kolom pada Desktop.
- Pada Mobile seluruh field berubah menjadi satu kolom.

---

# Table Design Rules

Seluruh halaman Master Data menggunakan struktur tabel yang sama.

Wajib memiliki:

- Search
- Filter
- Refresh
- Pagination
- Sort Column
- Total Records
- Action Column

Action Column menggunakan urutan berikut.

```
View
Edit
Delete
```

Apabila Role tidak memiliki hak Edit atau Delete, tombol tidak ditampilkan.

---

# Modal Design Rules

Gunakan Modal Bootstrap dengan ukuran yang konsisten.

Jenis Modal:

- Confirmation
- Information
- Warning
- Success
- Error

Modal konfirmasi harus memiliki tombol:

- Cancel
- Confirm

---

# Status Badge Standard

Status Ticket menggunakan warna Bootstrap yang konsisten.

| Status                    | Color     |
| ------------------------- | --------- |
| Waiting Technician        | Secondary |
| Diagnosis                 | Info      |
| Waiting Customer Approval | Warning   |
| In Progress               | Primary   |
| Finished                  | Success   |
| Waiting Invoice           | Dark      |
| Paid                      | Success   |
| Closed                    | Secondary |
| Cancelled                 | Danger    |

Status lain harus mengikuti standar Bootstrap.

---

# Empty State Rules

Apabila data kosong, tampilkan pesan yang spesifik.

Contoh:

- No Customer Found
- No Ticket Available
- No Product Available
- No Supplier Available

Hindari menggunakan pesan umum seperti:

```
No Data
```

---

# Notification Rules

Gunakan Alert Bootstrap.

Jenis notifikasi.

Success

```
Data saved successfully.
```

Warning

```
Please complete all required fields.
```

Danger

```
Unable to save data.
```

Info

```
No changes detected.
```

---

# Icon Standard

Gunakan Bootstrap Icons.

Contoh:

Dashboard

```
bi-speedometer2
```

Customer

```
bi-people
```

Ticket

```
bi-tools
```

Inventory

```
bi-box-seam
```

Supplier

```
bi-truck
```

Sales

```
bi-receipt
```

Expense

```
bi-wallet2
```

Monitoring

```
bi-bar-chart
```

Users

```
bi-person-badge
```

Audit

```
bi-clock-history
```

Settings

```
bi-gear
```

---

# Accessibility Rules

Seluruh halaman harus memenuhi prinsip berikut.

- Kontras warna yang cukup.
- Seluruh tombol memiliki teks yang jelas.
- Form dapat digunakan menggunakan keyboard.
- Focus indicator harus terlihat.
- Tidak mengandalkan warna sebagai satu-satunya indikator status.

---

# Performance Guidelines

UI harus tetap ringan.

Hindari:

- Animasi berlebihan.
- Shadow berlebihan.
- Gradient kompleks.
- JavaScript yang tidak diperlukan.

Prioritaskan kecepatan loading dibanding efek visual.

---

# Design Checklist

Sebelum halaman dianggap selesai, pastikan:

- Mengikuti Business Flow.
- Mengikuti Role yang sesuai.
- Menggunakan Layout Standard.
- Menggunakan Component Standard.
- Menggunakan Bootstrap 5.
- Responsive.
- Konsisten dengan halaman lain.
- Tidak menambahkan fitur di luar dokumentasi proyek.

---

# AI Development Reminder

AI tidak diperbolehkan mengubah desain maupun struktur sistem tanpa persetujuan.

Apabila menemukan kebutuhan baru:

1. Jelaskan alasan perubahan.
2. Berikan rekomendasi.
3. Tunggu persetujuan sebelum implementasi.

# Summary

This Design System provides a comprehensive foundation for FFixiT-MS frontend development. All components, colors, typography, and layouts are defined for consistency across the entire project.

**Key Principles**:

1. Bootstrap 5 framework (no custom CSS framework)
2. Desktop-first approach (1920px primary, responsive to mobile)
3. RBAC-aware navigation (different sidebars per role)
4. Professional, clean aesthetic (blue + gray + accent colors)
5. Task-focused UI (clear CTAs and information hierarchy)
6. Consistent component library (buttons, cards, tables, forms, etc.)
7. Comprehensive status indicators (9 ticket statuses)
8. Fully responsive (desktop, tablet, mobile with breakpoints)

**Component Reusability**:

- Use Bootstrap components as base
- Override with custom spacing, colors, and sizing as needed
- Create SCSS/CSS utility classes for common patterns
- Build reusable component templates in HTML
- Maintain consistency through shared design tokens

**Next Steps**: Use this system as reference when creating HTML templates, CSS stylesheets, and JavaScript components for FFixiT-MS.
