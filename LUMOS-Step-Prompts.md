# Stitch 分步执行提示词

> 使用方法：
> 1. 先上传 `LUMOS-Global-Constraints.md` 到 Stitch 工作面板
> 2. 每一步复制下方对应提示词，粘贴到 Stitch 输入框
> 3. 生成完检查，确认后再发下一步

---

## FILE 0

```
Referencing LUMOS-Global-Constraints.md — generate FILE 0: design-tokens.css

Output the :root block from the Global Constraints file as a standalone formatted CSS file.
One variable per line, organized by comment groups.

After output, cache this :root block. You must hardcode it in full at the top of <style> in every subsequent FILE.
BANNED: using <link> to reference this file. Every HTML must be self-contained.
```

---

## FILE 1

```
Referencing LUMOS-Global-Constraints.md — generate FILE 1: buttons.html

Title: FILE 1. Buttons
Description: 8 button variants — sizes, states, groups

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

8 variants:
1. Primary — Blue fill #2563EB, white text. Buttons: "Create" "Create" "Create" (sm/md/lg sizes shown by physical height not text). Disabled = grayed out. Loading = spinner icon.
2. Secondary — White bg + blue border var(--color-primary-600). "Cancel" "Confirm"
3. Ghost — Transparent, hover shows light bg. "Cancel" "Export"
4. Danger — Red fill. "Delete"
5. Text — Text link style. "Create" "Cancel"
6. Icon Only — Square/circle containers with SVG icons (search, trash, more)
7. Icon + Text — SVG icon + "Create", "Export"
8. Button Group — Horizontal: "Left" "Center" "Right"

Every button must have hover/active/focus/disabled CSS transitions.
Sizes: sm=32px, md=36px, lg=44px height.
```

---

## FILE 2

```
Referencing LUMOS-Global-Constraints.md — generate FILE 2: form-controls.html

Title: FILE 2. Form Controls
Description: Inputs, Selects, Checkboxes, Radios, Toggles

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

1. Inputs — 6 variants:
   Basic "Enter content..." / Floating Label / Prefix Icon (search SVG) / Suffix "USD" / Password (eye toggle SVG) / Error state "This field is required"

2. Selects — 5 variants (MUST be div-simulated, BANNED native <select>):
   Basic "Select department..." / Searchable / Multi-tag / Grouped / Disabled

3. Checkbox — 5 variants: Basic / With Description / Card Style / Indeterminate / Disabled

4. Radio — 5 variants: Basic / With Description / Card Style / Horizontal / Disabled

5. Toggle — 5 variants (div+CSS, BANNED native checkbox):
   Basic (blue when on) / With "ON"/"OFF" text / With icon / Small / Disabled

Input height: var(--size-control-md). Focus: blue border + focus-ring.
Include toggleActive() and click-outside-close JS at bottom.
```

---

## FILE 3

```
Referencing LUMOS-Global-Constraints.md — generate FILE 3: badges-avatars.html

Title: FILE 3. Badges & Avatars
Description: Badges, Avatars, Tooltips, Dividers

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

1. Badges — 6 variants:
   Solid (blue/green/amber/red) / Soft (light bg + dark text) / Outline / Dot indicator / Count "5" / Closable with X
   Labels: "In Progress" "Completed" "Pending" "Rejected" "Urgent"

2. Avatars — 5 variants:
   Image (sm 32px / md 40px / lg 64px) / Text initials "JS" "LW" "MK" on blue bg / Icon / With status dot (green=online) / Group (overlapping, +3 count)

3. Tooltips — 5 variants:
   Dark top / Dark all 4 directions / Light (white bg + shadow) / With arrow / Multiline

4. Dividers — 5 variants:
   Solid / Dashed / With text "OR" / With icon (SVG) / Vertical
```

---

## FILE 4

```
Referencing LUMOS-Global-Constraints.md — generate FILE 4: cards.html

Title: FILE 4. Cards
Description: Statistic cards and interactive cards

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.
Cards: white bg + 1px border var(--color-border-default) + var(--shadow-md) + 8px radius. Hover: shadow increases.

Section A — Statistic Cards (4 in a row):
"$128,430" "Monthly Revenue" green "↑12.5%" / "2,840" "Active Users" red "↓2.4%" / "15.2%" "Conversion Rate" "↑0.8%" / "$45.20" "Avg Order Value" "—"

Section B — Interactive Cards (7 variants):
1. Basic — Title + description + "Cancel" "Confirm" buttons
2. Media — Top image placeholder + title + description
3. Selectable — Selected: blue border + top-right blue checkmark SVG
4. Horizontal — Left image, right text
5. User — Avatar circle + "John Smith" + "Senior PM" + "View Profile" "Message" buttons
6. Progress — "LUMOS System" + blue progress bar 75% + "12 days left"
7. Pricing — 3 columns: Basic/Free | Pro/$199/mo (blue highlight "Get Started") | Enterprise/Contact Us
```

---

## FILE 5

```
Referencing LUMOS-Global-Constraints.md — generate FILE 5: navigation.html

Title: FILE 5. Navigation
Description: Nav items, Tabs, Breadcrumbs, Pagination

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

1. Nav Items — sidebar style:
   Items: Home / Dashboard / Files (blue badge "12") / Settings (expandable: Security, Notifications, Permissions)
   Active: left 3px blue bar + var(--color-bg-active) light blue bg
   Also show Collapsed state: icons only, hover tooltip

2. Tabs — 4 variants:
   Underline: Overview | Analytics | Reports | Settings (active = blue bottom border)
   Capsule: Daily | Weekly | Monthly (active = white bg pill)
   Icon Boxes / Vertical tabs

3. Breadcrumbs — 3 variants:
   Slash: Home / Projects / LUMOS Design System
   With home SVG icon: Home > Settings > Profile
   With dropdown

4. Pagination — 3 variants:
   Full: « 1 [2] 3 ... 10 »
   Simple: Previous | Page 1 of 10 | Next
   With page size selector
```

---

## FILE 6

```
Referencing LUMOS-Global-Constraints.md — generate FILE 6: lists-alerts-stats.html

Title: FILE 6. Lists, Alerts & Stats
Description: Search bars, List items, Stat blocks, Alerts

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

1. Search Bars — 3 variants:
   Basic: search SVG + "Search..." / With filter button "Filters" / With tabs "All" "Users" "Documents" + "Search" button

2. List Items — 4 variants:
   Arrow: settings icon + "System Preferences" + chevron-right SVG
   Avatar: photo + "Emily Chen" "Senior PM" + "View Profile"
   Actions: file icon + "Q4-Financial-Report.pdf" "2.4 MB" + download/trash SVG
   Status: server icon + "Primary Database" + green dot "Running"

3. Stat Blocks — 4 variants:
   Basic: "Total Users" "84,205" / Trend: "Revenue" "$128.5k" green "↑12.5%" / Chart: "Sessions" "1,492" + mini bar chart / Progress: "Storage" "750 GB / 1 TB" + blue bar

4. Alerts — 4 variants (each with left 3px semantic color bar):
   Info (blue): "System Update" "Scheduled maintenance Saturday..."
   Success (green): "Settings Saved" "Preferences updated..."
   Warning (amber): "API Quota" "Monthly quota exceeded 80%..."
   Error (red): "Connection Failed" "Unable to connect..." + "View Logs" "Retry"
```

---

## FILE 7

```
Referencing LUMOS-Global-Constraints.md — generate FILE 7: upload.html

Title: FILE 7. Upload
Description: 6 upload variants with empty, uploaded, uploading states

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

1. Dropzone — Dashed blue border + cloud SVG + "Click or drag files here" + "Supports JPG, PNG, PDF, max 10MB"
2. Button Upload — "Choose File" button + filename display
3. Image Grid — Grid of image thumbnails + add square with plus SVG
4. File List — Filename + size + blue progress bar + trash SVG
5. Avatar — Circle + hover overlay "Change Avatar"
6. Multi-State — Uploading (blue progress) / Success (green check) / Failed (red "Retry Upload")
```

---

## FILE 8

```
Referencing LUMOS-Global-Constraints.md — generate FILE 8: steps.html

Title: FILE 8. Steps
Description: 8 step variants

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.

Unified 3 steps, current = step 2. Done = blue circle + white check SVG. Active = blue highlight. Todo = gray.
Connector = 4px thick progress bar, NOT thin line.

1. Horizontal Basic — "Step 1" "Step 2" "Step 3"
2. Horizontal With Description — Title + subtitle per step
3. Horizontal With Toolbar — Steps bar + right-side toggle + action button in a white card bar
4. Vertical — Left circles + vertical connector + right content
5. Icon Steps — SVG icons replace numbers
6. Dot Steps — Small dots + thin connector
7. Step Form — Steps + form below + "Previous" / "Next Step" buttons. Include JS switching.
8. Progress Dashboard — White background card with toolbar + progress bar percentage + JS animation. MUST be white bg, BANNED dark.
```

---

## FILE 9

```
Referencing LUMOS-Global-Constraints.md — generate FILE 9: date-picker.html

Title: FILE 9. Date Picker
Description: 6 date picker variants

Follow the HTML skeleton from Global Constraints exactly. Raw CSS only.
Calendar MUST be div-based. BANNED: native <input type="date"> or <select>.

Selected day: blue filled circle + white text. Range: var(--color-primary-50) light blue bg.
Header: "January 2025". Weekdays: Mon Tue Wed Thu Fri Sat Sun.

1. Single Date — Click to select one day
2. Date Range — Dual calendar panels
3. Quick Range — Shortcut buttons: Today | 7 Days | This Month | Last Month | Quarter + calendar
4. Year-Month — Grid picker
5. DateTime — Date + time (hours:minutes)
6. Week — Select entire week row

Include JS for date selection interaction.
```

---

## FILE 10a

```
Referencing LUMOS-Global-Constraints.md — generate FILE 10a: table-base.html

Title: FILE 10a. Table Base
Description: 4 base table forms

Follow the HTML skeleton. Raw CSS only. Use .lumos-table base class for all tables.
CSS limit: under 200 lines. Each variant: min 3 data rows + full thead/tbody.
Mock data: "Project Alpha" "John Smith" "In Progress" "2025-01-15"

A. Classic — Standard rows, thin border dividers, gray header bg
B. Striped — Alternating row backgrounds
C. Card — Each row as independent card (white + shadow + 8px gap)
D. Compact — Reduced row height, 12px font
Bottom pagination (right-aligned).
```

---

## FILE 10b

```
Referencing LUMOS-Global-Constraints.md — generate FILE 10b: table-toolbar.html

Title: FILE 10b. Table Toolbar
Description: Filter, Search, Sort, Batch actions

Follow the HTML skeleton. Raw CSS only. .lumos-table class. CSS under 200 lines.

1. Tab Filter — "All" "Active" "Pending" "Archived" with counts
2. Toolbar — Search "Search records..." + date range + sort + "Reset" + blue "Search" + view toggle (SVG icons only, NO text: list-icon / grid-icon)
3. Batch Bar — "3 items selected" + "Edit" "Archive" "Delete"
4. Sortable Header — Up/down arrow SVGs in column headers
```

---

## FILE 10c

```
Referencing LUMOS-Global-Constraints.md — generate FILE 10c: table-cell-patterns.html

Title: FILE 10c. Table Cell Patterns
Description: 6 reusable cell content patterns

Follow the HTML skeleton. Raw CSS only. .lumos-table class. CSS under 200 lines.
Show each pattern inside a real table context (not isolated fragments).

1. Meta Lines — Bold primary + gray secondary line
2. Rich Notes — Left 3px semantic color bar + notes text + status line
3. Badge Group — Stacked capsule badges
4. Status Dot — Colored dot + "Running" / "Pending" / "Completed" / "Failed"
5. Action Links — "View" | "Edit" | "Delete"
6. Voided — Gray text + strikethrough
```

---

## FILE 10d

```
Referencing LUMOS-Global-Constraints.md — generate FILE 10d: table-views.html

Title: FILE 10d. Table Views
Description: Expandable rows, Card grid, View toggle

Follow the HTML skeleton. Raw CSS only. .lumos-table class.

1. Expandable Row — Click row to expand detail panel (light gray bg)
2. Card Grid — 4-column card layout
3. View Toggle — Two small SVG icon buttons only (list / grid), NO text. JS switches between views.
```

---

## FILE 10e

```
Referencing LUMOS-Global-Constraints.md — generate FILE 10e: table-showcase.html

Title: FILE 10e. Table Showcase
Description: 3 complete table combinations

Follow the HTML skeleton. Raw CSS only. Reuse .lumos-table classes from 10a-10d. CSS under 200 lines.
Each solution: min 3 data rows + full thead/tbody.

1. Classic Full — Tab filter + toolbar + sortable headers + row select + rich cells + pagination
2. Card Grid Full — Tab filter + toolbar + 4-column cards + pagination
3. Toggle View — Top-right SVG icon toggle (list/grid) + JS animated switch
```

---

## FILE 11

```
Referencing LUMOS-Global-Constraints.md — generate FILE 11: sidebar-menu.html

Title: FILE 11. Sidebar Menu
Description: 8 sidebar menu variants

Follow the HTML skeleton. Raw CSS only. This page ONLY shows sidebar components — no navbar, no header, no extra elements.

Menu items: Dashboard / User Management / Order Center / Content Management / Data Reports / System Settings

8 variants:
1. Basic Expanded — Icons + labels, groups "MAIN MENU" / "SETTINGS", active = left blue bar + light blue bg
2. With Sub-Menu — "System Settings" expands: Account Security / Notifications / Permissions / Data Backup
3. With Badges — "Order Center" blue badge "12", "Notifications" red dot
4. Collapsed — Icons only 56px wide, hover tooltip
5. With Search — "Search menu..." input at top
6. With User Zone — Bottom: avatar + "John Smith" + "Admin" + logout SVG
7. Multi-Level — 3 levels: Settings > Permissions > Role Management
8. Dark Theme — ONLY the sidebar is dark (slate-900 bg, light text), page background stays white

Each variant displayed independently, width 220px, simulated full height.
```

---

## FILE 12

```
Referencing LUMOS-Global-Constraints.md — generate FILE 12: header-footer.html

Title: FILE 12. Header & Footer
Description: 6 header variants + 5 footer variants

Follow the HTML skeleton. Raw CSS only.

Headers:
1. Basic — "LUMOS V2.0" logo + nav links: Overview / Components / Templates / Docs + avatar "JS"
2. With Search — Center search input "Search components..."
3. With Notification — Bell SVG + red badge "3"
4. With Breadcrumb — Home > Settings integrated below
5. With Language — "ZH / EN" toggle
6. With Action — Right-side blue button "+ New Project"

Footers:
1. Minimal — "© 2025 LUMOS. All rights reserved."
2. Links — Terms of Service | Privacy Policy | Help Center
3. Multi-Column — Product / Company / Support columns
4. With Logo — Logo + tagline + social SVG icons
5. Admin — Left: copyright, Right: support link
```

---

## FILE 13

```
Referencing LUMOS-Global-Constraints.md — generate FILE 13: forms-modals-states.html

Title: FILE 13. Forms, Modals & States
Description: Form sections, Modals, Empty states, Loading states

Follow the HTML skeleton. Raw CSS only. All selects/dropdowns = div-simulated.

1. Form Sections — 6 variants:
   Vertical / Horizontal / Inline / Grouped / Card / Stepper
   Fields: Project Name / Department (dropdown) / Owner / Start Date / Description (textarea)

2. Modals — 6 variants (triggered by button, JS open/close, overlay var(--color-bg-overlay)):
   Confirm "Submit changes?" / Danger "Delete permanently?" / Form modal / Success+Fail result / Fullscreen / Stepper

3. Empty States — 5 variants:
   No Data + "Create Now" / No Results / Error + "Reload" / No Permission + "Contact Admin" / Welcome "Welcome to LUMOS"

4. Loading — 5 variants:
   Skeleton (gray blocks + CSS pulse) / Spinner / Top blue progress bar / Button spinner / Inline "Loading..."
```

---

## FILE 14

```
Referencing LUMOS-Global-Constraints.md — generate FILE 14: rich-components.html

Title: FILE 14. Rich Components
Description: Dock, Attachments, Media, Audio, Editor, Contact Profile

Follow the HTML skeleton. Raw CSS only.

1. Floating Dock — 5 variants: Left Vertical / Bottom Horizontal / Top / With Labels / Collapsible (JS)
2. Attachment Cards — 5 variants: Inline / Card / Media Preview / List Group / 4-col Grid
3. Media Embeds — 6 variants: Map card / Link preview / Video thumbnail / Image gallery / Code snippet (dark bg allowed only here) / Quote block (left blue bar)
4. Audio Waveform — 4 variants: Standard (play + waveform + duration) / Mini / Voice bubble / Spectrum (CSS animation)
5. Rich Editor — 5 variants: Basic reply / With formatting bar / Minimal expandable / With @mention (JS) / With attachment preview
6. Contact Profile — 5 variants: Detail panel 320px / Hover card / List row / 4-col grid card / Compact bar
```

---

## FILE 15

```
Referencing LUMOS-Global-Constraints.md — generate FILE 15: layout-showcase.html

Title: FILE 15. Layout Showcase
Description: 5 layout skeletons

Follow the HTML skeleton. Raw CSS only. Content areas = gray dashed border + "Content Area" text.

1. Classic Admin — Header 56px + Sidebar 220px (collapsible to 56px) + page-header + content max-1200px
2. Top Nav — Header 56px with nav + content centered 1200px + Footer 48px
3. Dual Panel — Header + Sidebar 200px + content + Right Panel 320px
4. Tab Layout — Header + sticky Tab Bar + content centered 1400px
5. Full Canvas — Toolbar 48px + full-width content
6. Full-Height Sidebar— Sidebar 240px (To top) + Header 56px (Right-aligned) + Content Area
Full-height sidebar with integrated logo, right-aligned header with centered search bar and status pills.

Include sidebar collapse/expand JS.
```

---

## FILE 16

```
Referencing LUMOS-Global-Constraints.md — generate FILE 16: template-demo.html

Title: FILE 16. Template Demo
Description: Complete page — visual consistency validation only

Follow Global Constraints. Raw CSS only. Uses Layout 1 (Classic Admin).
This is for validation only, NOT a business template.

Header: "LUMOS V2.0" + search + bell(3) + "ZH/EN" + avatar "JS"
Sidebar: Dashboard (active) / User Management / Order Center / Content / Reports / Settings
Page-header: Home > Dashboard | "Dashboard" | date range | "Export Report"

Content (top to bottom):
1. Stat Cards ×4 — Total Users / Active Users / New Orders / Revenue (with trend arrows)
2. Tabs — Underline: Overview | User Analytics | Order Analytics
3. Table — Classic full: tab filter + toolbar + sort + select + pagination
4. Steps — 3 steps + form + "Next Step"
5. Upload — Dropzone + file list (3 files)

Block spacing: 40px between sections. Include full JS: sidebar toggle, tab switch, table interactions, step navigation.
```
