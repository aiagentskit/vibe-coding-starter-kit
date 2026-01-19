# System State

> **Last Updated:** 2026-01-15  
> **Environment:** Development  
> **Version:** 0.1.0 (Pre-Alpha)

---

## 🏗️ Current Tech Stack

### Frontend

| Component | Technology | Version | Notes |
|-----------|------------|---------|-------|
| Framework | React | 18.2.0 | Using functional components + hooks |
| Build Tool | Vite | 5.0.0 | Fast dev server, optimized builds |
| Styling | CSS Modules | - | Component-scoped styles |
| State Management | Zustand | 4.4.0 | Lightweight, simple API |
| Charts | Recharts | 2.10.0 | React-native charting |
| Date Handling | date-fns | 3.0.0 | Modular, tree-shakeable |

### Storage

| Component | Technology | Notes |
|-----------|------------|-------|
| Primary Storage | IndexedDB | Via Dexie.js wrapper (v3.2.0) |
| Backup Format | JSON/CSV | Manual export feature |
| Cache | Service Worker | Workbox (v7.0.0) |

### PWA

| Component | Status | Notes |
|-----------|--------|-------|
| Manifest | ✅ Configured | Icons for all sizes |
| Service Worker | ✅ Active | Offline-first strategy |
| Install Prompt | 🚧 In Progress | Custom install UI |

---

## 📊 What's Built vs Planned

### Core Features

| Feature | Status | Completion | Notes |
|---------|--------|------------|-------|
| Expense Entry Form | ✅ Complete | 100% | Amount, category, date, notes |
| Category Management | 🚧 In Progress | 70% | Add/edit works, delete pending |
| Dashboard Summary | 🚧 In Progress | 50% | Weekly view done, monthly pending |
| Data Export | 📋 Planned | 0% | JSON and CSV formats |
| Settings Page | 📋 Planned | 0% | Currency, date format prefs |

### Infrastructure

| Component | Status | Notes |
|-----------|--------|-------|
| Project Structure | ✅ Complete | Feature-based organization |
| Routing | ✅ Complete | React Router v6 |
| IndexedDB Setup | ✅ Complete | Schema v1 with migrations |
| Error Boundaries | ✅ Complete | Global + component level |
| PWA Shell | ✅ Complete | Installable on desktop/mobile |
| Unit Tests | 🚧 In Progress | ~40% coverage |
| E2E Tests | 📋 Planned | Playwright setup pending |

---

## 📁 Current File Structure

```
/personal-finance-tracker
├── public/
│   ├── manifest.json
│   ├── sw.js
│   └── icons/
├── src/
│   ├── components/
│   │   ├── common/
│   │   │   ├── Button/
│   │   │   ├── Input/
│   │   │   └── Modal/
│   │   ├── expense/
│   │   │   ├── ExpenseForm/
│   │   │   ├── ExpenseList/
│   │   │   └── ExpenseItem/
│   │   └── dashboard/
│   │       ├── SpendingSummary/
│   │       ├── CategoryBreakdown/
│   │       └── RecentTransactions/
│   ├── pages/
│   │   ├── Dashboard.jsx
│   │   ├── AddExpense.jsx
│   │   ├── Categories.jsx
│   │   └── Settings.jsx
│   ├── stores/
│   │   ├── expenseStore.js
│   │   └── categoryStore.js
│   ├── db/
│   │   ├── index.js
│   │   └── migrations.js
│   ├── utils/
│   │   ├── formatters.js
│   │   └── validators.js
│   ├── hooks/
│   │   ├── useExpenses.js
│   │   └── useCategories.js
│   ├── App.jsx
│   └── main.jsx
├── docs/                    # This documentation
├── package.json
├── vite.config.js
└── README.md
```

---

## 🗄️ Database Schema (IndexedDB)

### Current Schema (v1)

```javascript
// Expenses Table
{
  id: number,           // Auto-increment primary key
  amount: number,       // Stored in cents (e.g., 1999 = $19.99)
  categoryId: number,   // Foreign key to categories
  date: string,         // ISO 8601 format (YYYY-MM-DD)
  notes: string,        // Optional description
  createdAt: string,    // ISO 8601 timestamp
  updatedAt: string     // ISO 8601 timestamp
}

// Categories Table
{
  id: number,           // Auto-increment primary key
  name: string,         // Category name
  icon: string,         // Emoji or icon identifier
  color: string,        // Hex color code
  isDefault: boolean,   // System-provided vs user-created
  createdAt: string
}
```

### Indexes

- `expenses.date` - For date range queries
- `expenses.categoryId` - For category filtering
- `categories.name` - For unique constraint

---

## 🌐 Deployment Status

| Environment | URL | Status | Last Deploy |
|-------------|-----|--------|-------------|
| Local Dev | localhost:5173 | ✅ Active | - |
| Preview | - | 🔴 Not Setup | - |
| Production | - | 🔴 Not Setup | - |

### Planned Deployment

- **Host:** Cloudflare Pages (static hosting)
- **CDN:** Cloudflare Global
- **Domain:** TBD

---

## ⚡ Known Issues

### Active Bugs

| ID | Description | Severity | Status |
|----|-------------|----------|--------|
| BUG-001 | Date picker not respecting locale | Low | Open |
| BUG-002 | Category color picker closes on mobile tap | Medium | Investigating |

### Technical Debt

| ID | Description | Priority | Notes |
|----|-------------|----------|-------|
| TD-001 | Expense store has inline styles | Low | Refactor to CSS modules |
| TD-002 | No loading states for async operations | Medium | Add skeleton loaders |
| TD-003 | Console warnings on strict mode | Low | Fix useEffect dependencies |

---

## 🔧 Development Environment

### Required

- Node.js 20.x LTS
- npm 10.x or pnpm 8.x
- Modern browser with DevTools

### Recommended IDE Setup

- VS Code with extensions:
  - ESLint
  - Prettier
  - CSS Modules
  - ES7+ React Snippets

### Local Commands

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Run tests
npm test

# Build for production
npm run build

# Preview production build
npm run preview
```

---

## 📈 Performance Baseline

| Metric | Current | Target | Notes |
|--------|---------|--------|-------|
| Lighthouse Performance | 85 | 95 | Image optimization pending |
| First Contentful Paint | 1.2s | < 1.0s | Good |
| Time to Interactive | 2.1s | < 2.0s | Near target |
| Bundle Size (gzipped) | 78KB | < 100KB | On track |

---

## 📅 Last Major Changes

| Date | Change | Impact |
|------|--------|--------|
| 2026-01-15 | Added Zustand for state management | Simplified state logic |
| 2026-01-14 | Implemented IndexedDB with Dexie | Data persistence working |
| 2026-01-12 | Set up Vite + React project | Initial scaffold |
| 2026-01-10 | Created documentation structure | This system established |

---

## 📎 Related Documents

- [Vision](./vision.md)
- [Assumptions](./assumptions.md)
- [Implementation Log](../03-logs/implementation-log.md)
