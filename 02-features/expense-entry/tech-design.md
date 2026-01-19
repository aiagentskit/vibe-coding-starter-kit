# Technical Design: Expense Entry

> **Feature:** Add Expense Flow  
> **Status:** Approved  
> **Last Updated:** 2026-01-15  
> **Author:** Engineering Team

---

## 📐 Architecture Overview

### Component Hierarchy

```
ExpenseEntryPage
├── PageHeader ("Add Expense")
├── ExpenseForm
│   ├── AmountInput
│   ├── CategoryPicker
│   │   └── CategoryButton (x many)
│   ├── DateInput
│   ├── NotesInput
│   └── SubmitButton
└── Toast (success/error feedback)
```

### Data Flow

```
┌──────────────────────────────────────────────────────────────┐
│                      USER INTERACTION                         │
└──────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                      ExpenseForm                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Local State: { amount, categoryId, date, notes }       │  │
│  │ Validation: useForm hook with Zod schema               │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                              │
                    handleSubmit()
                              │
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                    Expense Store (Zustand)                    │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ addExpense(expenseData) => Promise<void>               │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                    IndexedDB (via Dexie)                      │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ db.expenses.add(expense)                               │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌──────────────────────────────────────────────────────────────┐
│                      Success/Error                            │
│  ┌────────────────────────────────────────────────────────┐  │
│  │ Show toast → Reset form → Ready for next entry         │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

---

## 📦 Data Models

### Expense (Domain Model)

```typescript
interface Expense {
  id?: number;               // Auto-generated by IndexedDB
  amount: number;            // Stored in cents (e.g., 1999 = $19.99)
  categoryId: number;        // Foreign key to categories table
  date: string;              // ISO 8601 format: "2026-01-15"
  notes: string;             // User-provided description
  createdAt: string;         // ISO 8601 timestamp
  updatedAt: string;         // ISO 8601 timestamp
}
```

### Form State

```typescript
interface ExpenseFormState {
  amount: string;           // String for input handling, convert on submit
  categoryId: number | null;
  date: Date;
  notes: string;
}

interface ExpenseFormErrors {
  amount?: string;
  categoryId?: string;
  date?: string;
  notes?: string;
}
```

### Validation Schema (Zod)

```typescript
import { z } from 'zod';

const expenseSchema = z.object({
  amount: z
    .string()
    .min(1, 'Amount is required')
    .transform((val) => parseFloat(val.replace(/[^0-9.]/g, '')))
    .refine((val) => val > 0, 'Amount must be positive')
    .refine((val) => val <= 999999.99, 'Amount too large'),
  categoryId: z
    .number({ required_error: 'Please select a category' })
    .positive(),
  date: z
    .date()
    .max(new Date(), 'Future dates not allowed'),
  notes: z
    .string()
    .max(500, 'Notes must be 500 characters or less')
    .optional(),
});
```

---

## 🧩 Component Specifications

### AmountInput

```typescript
interface AmountInputProps {
  value: string;
  onChange: (value: string) => void;
  error?: string;
  currencySymbol?: string;  // Default: '$'
  autoFocus?: boolean;      // Default: true
}
```

**Implementation Notes:**
- Use `inputMode="decimal"` for mobile numeric keyboard
- Format on blur: `1234.5` → `$1,234.50`
- Strip formatting on focus for easy editing
- Prevent non-numeric characters with `onKeyDown`

### CategoryPicker

```typescript
interface CategoryPickerProps {
  value: number | null;
  onChange: (categoryId: number) => void;
  error?: string;
}

// Internal: fetches categories from store
const categories = useCategoryStore((state) => state.categories);
```

**Implementation Notes:**
- Display as grid (5 columns on mobile, adapt on desktop)
- Show icon + truncated name
- Selected state: border highlight + checkmark
- Last item: "+" button to add custom category (opens modal)

### DateInput

```typescript
interface DateInputProps {
  value: Date;
  onChange: (date: Date) => void;
  error?: string;
  maxDate?: Date;           // Default: today
}
```

**Implementation Notes:**
- Use native `<input type="date">` on mobile
- Custom date picker on desktop for consistency
- Display "Today", "Yesterday", or formatted date

### NotesInput

```typescript
interface NotesInputProps {
  value: string;
  onChange: (value: string) => void;
  maxLength?: number;       // Default: 500
  placeholder?: string;
}
```

**Implementation Notes:**
- Standard textarea
- Character count: `${value.length}/${maxLength}`
- Warn when approaching limit (>450 chars)

---

## 🗃️ Store Design (Zustand)

### Expense Store

```typescript
// stores/expenseStore.ts

import { create } from 'zustand';
import { db } from '../db';

interface ExpenseStore {
  // State
  expenses: Expense[];
  isLoading: boolean;
  error: string | null;

  // Actions
  addExpense: (data: CreateExpenseInput) => Promise<void>;
  loadExpenses: (filters?: ExpenseFilters) => Promise<void>;
  updateExpense: (id: number, data: Partial<Expense>) => Promise<void>;
  deleteExpense: (id: number) => Promise<void>;
}

interface CreateExpenseInput {
  amount: number;           // In cents
  categoryId: number;
  date: string;
  notes?: string;
}

export const useExpenseStore = create<ExpenseStore>((set, get) => ({
  expenses: [],
  isLoading: false,
  error: null,

  addExpense: async (data) => {
    const now = new Date().toISOString();
    const expense: Expense = {
      ...data,
      notes: data.notes || '',
      createdAt: now,
      updatedAt: now,
    };

    try {
      const id = await db.expenses.add(expense);
      set((state) => ({
        expenses: [{ ...expense, id }, ...state.expenses],
        error: null,
      }));
    } catch (error) {
      set({ error: 'Failed to save expense' });
      throw error;
    }
  },

  // ... other actions
}));
```

---

## 🛠️ Implementation Approach

### Phase 1: Core Form (Day 1)

1. Create `ExpenseForm` component with local state
2. Implement `AmountInput` with formatting
3. Setup basic form submission (console.log)

### Phase 2: Category Picker (Day 2)

1. Create `CategoryPicker` component
2. Connect to `useCategoryStore`
3. Implement selection state

### Phase 3: Date & Notes (Day 2)

1. Implement `DateInput` with date-fns
2. Implement `NotesInput` with character count
3. Add form validation with Zod

### Phase 4: Store Integration (Day 3)

1. Implement `addExpense` in store
2. Connect form submit to store
3. Add loading state to button

### Phase 5: Feedback & Polish (Day 3)

1. Add toast notifications
2. Implement form reset after success
3. Add keyboard navigation
4. Accessibility audit

---

## 📁 File Structure

```
src/
├── components/
│   └── expense/
│       ├── ExpenseForm/
│       │   ├── ExpenseForm.jsx
│       │   ├── ExpenseForm.module.css
│       │   └── index.js
│       ├── AmountInput/
│       │   ├── AmountInput.jsx
│       │   ├── AmountInput.module.css
│       │   └── index.js
│       ├── CategoryPicker/
│       │   ├── CategoryPicker.jsx
│       │   ├── CategoryPicker.module.css
│       │   └── index.js
│       ├── DateInput/
│       │   ├── DateInput.jsx
│       │   └── index.js
│       └── NotesInput/
│           ├── NotesInput.jsx
│           └── index.js
├── pages/
│   └── AddExpense.jsx
├── stores/
│   └── expenseStore.js
├── schemas/
│   └── expenseSchema.js
└── utils/
    └── formatters.js
```

---

## ⚡ Performance Considerations

| Consideration | Approach |
|---------------|----------|
| Form re-renders | Use `React.memo` on sub-components |
| Category loading | Load once on mount, cache in store |
| Large category lists | Virtual list if > 20 categories |
| Debounce validation | 300ms debounce on field blur |

---

## 🔒 Security Considerations

| Risk | Mitigation |
|------|------------|
| XSS via notes field | Sanitize on display (React handles this) |
| IndexedDB tampering | Accept - local data, user's device |
| Invalid data injection | Validate with Zod before storage |

---

## 🧪 Testing Strategy

See [test-plan.md](./test-plan.md) for complete testing approach.

**Key focus areas:**
- Form validation edge cases
- IndexedDB write/read operations
- Category picker interactions
- Mobile keyboard behavior

---

## 📎 Related Documents

- [Feature Spec](./feature-spec.md)
- [Dev Tasks](./dev-tasks.md)
- [Test Plan](./test-plan.md)
