# Expense Tracker

## Overview
A beautiful, fully-functional expense tracker application built with React, Express, and Chart.js. Users can track income and expenses, view summary statistics, and visualize spending patterns with interactive pie charts.

**Current State:** ✅ MVP Complete - All features working and tested end-to-end

## Features
- **Transaction Management**
  - Add income and expense transactions with amount, category, and description
  - Categorized transactions (Income: Salary, Freelance, Investment, Gift, Other; Expenses: Food & Dining, Transportation, Shopping, Bills & Utilities, Entertainment, Healthcare, Other)
  - Delete transactions with one click
  
- **Financial Summary**
  - Real-time summary cards showing Total Income, Total Expenses, and Net Balance
  - Color-coded amounts (green for income/positive, red for expenses/negative)
  - Sticky header with current balance display

- **Data Visualization**
  - Interactive pie chart showing expense breakdown by category
  - Built with Chart.js for smooth, responsive charts
  - Percentage and dollar amount tooltips

- **Filtering & Organization**
  - Filter transactions by type (All, Income, Expenses)
  - Sorted by date (most recent first)
  - Responsive table/card layout for all screen sizes

## Technology Stack

### Frontend
- **React** with TypeScript for type safety
- **Wouter** for client-side routing
- **TanStack React Query** for data fetching and state management
- **Chart.js** with react-chartjs-2 for visualizations
- **Shadcn UI** components for consistent design
- **Tailwind CSS** for styling
- **Lucide React** for icons

### Backend
- **Express.js** REST API
- **Zod** for request validation
- **In-memory storage** (MemStorage) for fast development and testing

### Design System
- Material Design (Data-Focused Variant)
- Custom color palette with dark mode support
- Inter/Roboto fonts for UI, JetBrains Mono for numerical data
- Responsive grid layouts (mobile-first)

## Project Structure

```
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── expense-chart.tsx      # Pie chart visualization
│   │   │   ├── summary-cards.tsx      # Income/Expenses/Balance cards
│   │   │   ├── transaction-form.tsx   # Add transaction form
│   │   │   └── transaction-list.tsx   # Transaction table/list
│   │   ├── pages/
│   │   │   └── home.tsx               # Main dashboard page
│   │   └── App.tsx                     # App router
│
├── server/
│   ├── routes.ts                       # API endpoints
│   └── storage.ts                      # In-memory data storage
│
├── shared/
│   └── schema.ts                       # Shared TypeScript types and Zod schemas
│
└── design_guidelines.md                # Design system documentation
```

## API Endpoints

### GET /api/transactions
Fetches all transactions sorted by date (most recent first)
- **Response:** Array of Transaction objects

### POST /api/transactions
Creates a new transaction
- **Request Body:** `{ type: "income" | "expense", amount: string, category: string, description: string }`
- **Response:** Transaction object with id and date (201 Created)
- **Validation:** Zod schema ensures amount > 0, type is valid, category is provided

### DELETE /api/transactions/:id
Deletes a transaction by ID
- **Response:** 204 No Content

## Data Schema

```typescript
Transaction {
  id: string;           // UUID
  type: "income" | "expense";
  amount: string;       // Decimal string (e.g., "100.00")
  category: string;
  description: string;
  date: Date;
}
```

## Recent Changes

### October 29, 2025 - Initial MVP Implementation
- ✅ Implemented complete data schema with transaction model
- ✅ Built all frontend components following Material Design guidelines
- ✅ Created RESTful API with validation
- ✅ Integrated React Query for data fetching and mutations
- ✅ Added Chart.js pie chart for expense visualization
- ✅ Implemented filtering and deletion features
- ✅ End-to-end testing completed - all features working
- ✅ Responsive design tested on mobile, tablet, and desktop layouts

## Development

### Running the Application
The app runs via the "Start application" workflow which executes `npm run dev`:
- Frontend: Vite dev server
- Backend: Express server on port 5000
- Both served on the same port with Vite proxy configuration

### Testing
Comprehensive e2e test coverage including:
- Adding income and expense transactions
- Summary card calculations
- Pie chart rendering
- Transaction filtering
- Delete functionality
- Form validation and error handling

## User Preferences
- Clean, data-focused Material Design aesthetic
- Monospace fonts for financial amounts
- Green/red color coding for positive/negative values
- Sticky header with quick balance view
- Empty states with helpful messaging

## Architecture Decisions

1. **In-Memory Storage:** Using MemStorage for fast prototyping. Can easily swap to PostgreSQL database in future.

2. **Schema-First Development:** Defined TypeScript types and Zod schemas first to ensure type safety across frontend and backend.

3. **Component Organization:** Separated concerns with dedicated components for form, list, chart, and summary - maximizing reusability.

4. **React Query:** Centralized data fetching with automatic caching, invalidation on mutations, and optimistic updates.

5. **Material Design:** Data-focused variant chosen for clarity in financial information display with proper visual hierarchy.

## Next Steps (Future Enhancements)
- Add date range filtering
- Implement category management (custom categories)
- Create monthly/yearly comparison charts
- Add budget setting and tracking
- Export data to CSV
- Migrate to PostgreSQL for persistent storage
- Add user authentication
- Implement recurring transactions
