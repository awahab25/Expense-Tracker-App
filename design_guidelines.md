# Expense Tracker Design Guidelines

## Design Approach

**Selected System:** Material Design (Data-Focused Variant)
**Rationale:** Expense tracking is a utility-focused productivity tool where data clarity, efficient input, and intuitive navigation are paramount. Material Design provides excellent patterns for forms, data display, and responsive layouts while maintaining visual hierarchy in information-dense interfaces.

**Core Principles:**
- Clarity over decoration - every element serves a functional purpose
- Instant feedback for all user actions (form validation, transaction additions)
- Scannable data presentation with clear visual hierarchy
- Mobile-first responsive design for on-the-go expense tracking

## Typography System

**Font Stack:** 
- Primary: Inter or Roboto (via Google Fonts CDN)
- Monospace: JetBrains Mono for numerical data display

**Type Scale:**
- Page Headers: text-3xl font-bold (Income & Expenses Dashboard)
- Section Titles: text-xl font-semibold (Summary, Recent Transactions, Breakdown)
- Card Headers: text-lg font-medium
- Body Text: text-base font-normal
- Labels: text-sm font-medium (form labels, table headers)
- Numerical Data: text-lg font-mono (amounts, balances)
- Helper Text: text-xs (validation messages, timestamps)

## Layout System

**Spacing Primitives:** Tailwind units of **2, 4, 6, and 8**
- Component padding: p-6
- Card spacing: gap-6 or space-y-6
- Form field spacing: space-y-4
- Button padding: px-6 py-2
- Section margins: mb-8
- Tight spacing (icons, chips): gap-2

**Grid Structure:**
- Desktop (lg:): 2-column layout (form sidebar + main content area)
- Tablet (md:): Single column with stacked sections
- Mobile: Full-width single column

**Container Strategy:**
- Maximum width: max-w-6xl mx-auto
- Horizontal padding: px-4 md:px-6 lg:px-8
- Main content area uses grid grid-cols-1 lg:grid-cols-3 gap-6
- Forms occupy 1 column, content spans 2 columns on desktop

## Component Library

### Navigation/Header
- Sticky header with app title and current balance summary
- Height: h-16
- Balance badge prominently displayed (Income vs Expenses differential)
- Optional: Quick filter tabs (All/Income/Expenses)

### Summary Cards (3-card row)
- Grid layout: grid grid-cols-1 md:grid-cols-3 gap-4
- Cards display: Total Income | Total Expenses | Net Balance
- Each card: rounded-lg border with p-6
- Large numerical display (text-2xl font-mono font-bold)
- Label above number (text-sm uppercase tracking-wide)
- Use subtle icons from Heroicons (arrow-up for income, arrow-down for expenses)

### Transaction Input Form
- Contained in rounded-lg border card with p-6
- Form fields vertically stacked with space-y-4
- Input groups:
  - Type selector: Radio buttons or segmented control (Income/Expense)
  - Amount: Number input with leading currency symbol
  - Category: Dropdown/select with common categories
  - Description: Text input (optional field)
  - Date: Date picker (defaults to today)
- Submit button: Full-width, h-10, rounded-md
- Clear visual validation states (error borders, success checkmarks)

### Transaction List
- Table layout on desktop, card layout on mobile
- Headers: Date | Description | Category | Amount | Actions
- Alternating row treatment for scannability
- Amount column right-aligned with monospace font
- Positive amounts (income) and negative amounts (expenses) with distinct visual treatment
- Delete button: Icon button with trash icon (Heroicons)
- Empty state: Centered message with illustration placeholder

### Chart Visualization
- Pie chart container: rounded-lg border with p-6
- Chart dimensions: Responsive with aspect-[1/1] or aspect-[4/3]
- Title above chart: text-lg font-semibold mb-4
- Legend positioned below or beside chart
- Interactive tooltips on hover (Chart.js default)
- Category breakdown shows percentage + absolute value

### Buttons & Actions
**Primary Actions:**
- Add Transaction: h-10 px-6 rounded-md font-medium
- Filter buttons: h-8 px-4 rounded-md

**Secondary Actions:**
- Delete icons: h-8 w-8 rounded-md icon buttons
- Edit (if applicable): icon buttons

**States:**
- Default: solid appearance
- Hover: slight elevation or brightness shift
- Active: pressed appearance
- Disabled: reduced opacity

### Form Inputs
- Height: h-10 for text inputs, h-12 for select dropdowns
- Border radius: rounded-md
- Padding: px-3
- Clear focus states with ring offset
- Error states with border treatment and text-sm error messages below

### Icons
**Library:** Heroicons (via CDN)
**Usage:**
- Navigation: h-5 w-5
- Form inputs (prefix): h-4 w-4
- Action buttons: h-5 w-5
- Summary cards: h-6 w-6
- Categories: h-4 w-4 inline icons

Common icons needed:
- Plus (add transaction)
- Trash (delete)
- Arrow-up/down (income/expense indicators)
- Chart-pie (analytics section)
- Calendar (date picker)
- Currency-dollar (amount inputs)

## Responsive Behavior

**Mobile (< 768px):**
- Single column layout
- Form positioned above content
- Summary cards stack vertically
- Transaction list becomes card-based with stacked information
- Chart adjusts to full-width

**Tablet (768px - 1024px):**
- Summary cards in 3-column grid
- Form and content sections stack
- Table view for transactions maintained

**Desktop (> 1024px):**
- Sidebar form (1 column) + content area (2 columns)
- All elements at optimal viewing size
- Hover states fully functional

## Data Visualization

**Chart.js Integration:**
- Pie chart for expense category breakdown
- Responsive canvas sizing
- Tooltip configuration with formatted currency values
- Legend with clickable category filters
- Color palette should be assigned programmatically (avoid hardcoding)

## Accessibility

- All form inputs have associated labels
- Clear focus indicators (ring-2 ring-offset-2)
- Adequate contrast ratios for all text
- Keyboard navigation support for all interactive elements
- ARIA labels for icon-only buttons
- Error messages announced to screen readers
- Semantic HTML structure (header, main, form, table)

## Animation & Micro-interactions

**Minimal, purposeful animations only:**
- Form submission: brief success confirmation (checkmark fade-in)
- Transaction deletion: row fade-out
- Chart rendering: subtle fade-in on load
- No distracting transitions - keep it snappy

## Special Considerations

**Numerical Formatting:**
- Currency symbols consistently positioned (prefix: $)
- Comma separators for thousands (1,234.56)
- Two decimal places always shown
- Monospace font for amount columns ensures alignment

**Empty States:**
- "No transactions yet" message when list is empty
- Encourage first action ("Add your first transaction above")
- Chart shows placeholder when no expense data exists

**Transaction Categories:**
Suggested defaults: Food & Dining, Transportation, Shopping, Bills & Utilities, Entertainment, Healthcare, Other

This design creates a professional, efficient expense tracking interface optimized for frequent data entry and quick financial overview - exactly what users need from a productivity finance tool.