# Dev Tasks: Expense Entry

> **Feature:** Add Expense Flow  
> **Status:** In Progress  
> **Total Tasks:** 12  
> **Completed:** 0

---

## 📋 Overview

This document contains atomic, LLM-executable tasks for implementing the expense entry feature. Each task is designed to be completable in a single AI coding session.

**How to use:**
1. Copy a task to your AI assistant
2. Include relevant context files (vision.md, tech-design.md)
3. Implement and test
4. Mark complete and log in implementation-log.md

---

## 🏗️ Foundation Tasks

### TASK-001: Create AmountInput Component

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 30 minutes  
**Dependencies:** None

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (AmountInput section)
- `docs/00-context/system-state.md` (current file structure)

**Task Description:**

Create a reusable `AmountInput` component for currency input with the following requirements:

1. **Create files:**
   - `src/components/expense/AmountInput/AmountInput.jsx`
   - `src/components/expense/AmountInput/AmountInput.module.css`
   - `src/components/expense/AmountInput/index.js`

2. **Props:**
   ```jsx
   {
     value: string,
     onChange: (value: string) => void,
     error?: string,
     currencySymbol?: string, // default '$'
     autoFocus?: boolean      // default true
   }
   ```

3. **Behavior:**
   - Display currency symbol as prefix
   - Accept only numeric input and single decimal point
   - Format value on blur: `1234.5` → `1,234.50`
   - Strip formatting on focus for editing
   - Show error message below input if provided
   - Large font size (32px) for easy reading

4. **Mobile:**
   - Use `inputMode="decimal"` for numeric keyboard
   - `pattern="[0-9]*"` for iOS

5. **Accessibility:**
   - Proper label association
   - Aria-invalid when error present
   - Aria-describedby for error message

**Acceptance Criteria:**
- [ ] Component renders with currency prefix
- [ ] Only accepts numeric input
- [ ] Formats correctly on blur
- [ ] Shows error state when provided
- [ ] Works on mobile with numeric keyboard

---

### TASK-002: Create CategoryPicker Component

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 45 minutes  
**Dependencies:** Category store must exist

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (CategoryPicker section)
- `docs/01-product/prd.md` (Default Categories section)

**Task Description:**

Create a grid-based category picker component:

1. **Create files:**
   - `src/components/expense/CategoryPicker/CategoryPicker.jsx`
   - `src/components/expense/CategoryPicker/CategoryPicker.module.css`
   - `src/components/expense/CategoryPicker/index.js`

2. **Props:**
   ```jsx
   {
     value: number | null,
     onChange: (categoryId: number) => void,
     error?: string
   }
   ```

3. **Layout:**
   - 5-column grid (adapts to 3 columns on narrow screens)
   - Each cell shows: category emoji + name (truncated)
   - Selected state: border highlight + subtle background
   - Last cell: "+" button for adding new category (emit event for now)

4. **Data:**
   - Fetch categories from `useCategoryStore`
   - Show loading state while fetching
   - Handle empty state

5. **Interactions:**
   - Click/tap to select
   - Keyboard navigation: arrow keys + Enter to select

**Acceptance Criteria:**
- [ ] Displays categories in grid
- [ ] Selected category visually highlighted
- [ ] Works with keyboard navigation
- [ ] Shows error state when provided
- [ ] Responsive layout

---

### TASK-003: Create DateInput Component

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 30 minutes  
**Dependencies:** date-fns installed

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (DateInput section)

**Task Description:**

Create a date input component:

1. **Create files:**
   - `src/components/expense/DateInput/DateInput.jsx`
   - `src/components/expense/DateInput/DateInput.module.css`
   - `src/components/expense/DateInput/index.js`

2. **Props:**
   ```jsx
   {
     value: Date,
     onChange: (date: Date) => void,
     error?: string,
     maxDate?: Date  // default: today
   }
   ```

3. **Display logic:**
   - If today: show "Today, Jan 15, 2026"
   - If yesterday: show "Yesterday, Jan 14, 2026"
   - Otherwise: show "Mon, Jan 13, 2026"

4. **Behavior:**
   - Use native `<input type="date">` (styled)
   - Prevent future dates
   - Parse/format using date-fns

5. **Styling:**
   - Match other form inputs visually
   - Calendar icon hint

**Acceptance Criteria:**
- [ ] Shows user-friendly date format
- [ ] Native picker works on mobile
- [ ] Cannot select future dates
- [ ] Shows "Today" or "Yesterday" when applicable

---

### TASK-004: Create NotesInput Component

**Status:** ⬜ Not Started  
**Priority:** P1  
**Estimated Time:** 20 minutes  
**Dependencies:** None

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (NotesInput section)

**Task Description:**

Create a textarea component with character count:

1. **Create files:**
   - `src/components/expense/NotesInput/NotesInput.jsx`
   - `src/components/expense/NotesInput/NotesInput.module.css`
   - `src/components/expense/NotesInput/index.js`

2. **Props:**
   ```jsx
   {
     value: string,
     onChange: (value: string) => void,
     maxLength?: number,  // default: 500
     placeholder?: string
   }
   ```

3. **Features:**
   - Standard textarea (3-4 rows)
   - Character count: "45/500" in bottom right
   - Warning color when >450 characters
   - Enforce maxLength on input

4. **Styling:**
   - Resize: vertical only
   - Match other inputs visually

**Acceptance Criteria:**
- [ ] Shows character count
- [ ] Enforces max length
- [ ] Visual warning near limit
- [ ] Placeholder text shown when empty

---

## 🔧 Integration Tasks

### TASK-005: Create Expense Validation Schema

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 20 minutes  
**Dependencies:** Zod installed

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (Validation Schema section)

**Task Description:**

Create Zod schema for expense validation:

1. **Create file:**
   - `src/schemas/expenseSchema.js`

2. **Schema requirements:**
   ```javascript
   export const expenseSchema = z.object({
     amount: // required, positive, max 999999.99
     categoryId: // required, positive number
     date: // required, max today
     notes: // optional, max 500 chars
   });
   ```

3. **Export:**
   - Schema
   - Type (inferred from schema)
   - Validation function with formatted errors

4. **Error messages:**
   - User-friendly ("Amount is required" not "Required field")

**Acceptance Criteria:**
- [ ] Validates all required fields
- [ ] Rejects negative amounts
- [ ] Rejects future dates
- [ ] Truncates notes at 500 chars
- [ ] Returns user-friendly error messages

---

### TASK-006: Create ExpenseForm Component

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 45 minutes  
**Dependencies:** TASK-001 through TASK-005

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (full Component specs)
- `docs/02-features/expense-entry/feature-spec.md` (acceptance criteria)

**Task Description:**

Compose all sub-components into the main form:

1. **Create files:**
   - `src/components/expense/ExpenseForm/ExpenseForm.jsx`
   - `src/components/expense/ExpenseForm/ExpenseForm.module.css`
   - `src/components/expense/ExpenseForm/index.js`

2. **Structure:**
   ```jsx
   <form onSubmit={handleSubmit}>
     <AmountInput />
     <CategoryPicker />
     <DateInput />
     <NotesInput />
     <SubmitButton />
   </form>
   ```

3. **State management:**
   - Use React useState for form state
   - Validate with Zod schema on submit
   - Show inline errors per field

4. **Submit behavior:**
   - Validate all fields
   - If valid, call `onSubmit(expenseData)` prop
   - If invalid, show errors and focus first error field

5. **Props:**
   ```jsx
   {
     onSubmit: (data: ExpenseInput) => Promise<void>,
     isSubmitting?: boolean
   }
   ```

**Acceptance Criteria:**
- [ ] All sub-components render correctly
- [ ] Form validates on submit
- [ ] Errors shown per field
- [ ] Submit button shows loading state
- [ ] Keyboard submit works (Enter key)

---

### TASK-007: Implement addExpense Store Action

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 30 minutes  
**Dependencies:** IndexedDB setup complete

**Context Files to Include:**
- `docs/02-features/expense-entry/tech-design.md` (Store Design section)
- `docs/00-context/system-state.md` (Database Schema section)

**Task Description:**

Add expense creation to the Zustand store:

1. **Update file:**
   - `src/stores/expenseStore.js`

2. **Add action:**
   ```javascript
   addExpense: async (input) => {
     // 1. Convert amount to cents
     // 2. Add timestamps
     // 3. Write to IndexedDB
     // 4. Update state with new expense
     // 5. Handle errors
   }
   ```

3. **Amount conversion:**
   - Input: decimal dollars (19.99)
   - Storage: integer cents (1999)

4. **Error handling:**
   - Set error in store
   - Throw error for caller to handle

**Acceptance Criteria:**
- [ ] Expense saved to IndexedDB
- [ ] Store state updated optimistically
- [ ] Amount converted to cents
- [ ] Timestamps added automatically
- [ ] Errors captured and thrown

---

### TASK-008: Create AddExpense Page

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** 30 minutes  
**Dependencies:** TASK-006, TASK-007

**Context Files to Include:**
- `docs/02-features/expense-entry/feature-spec.md` (full spec)

**Task Description:**

Create the page component that hosts the expense form:

1. **Update file:**
   - `src/pages/AddExpense.jsx`

2. **Structure:**
   ```jsx
   <PageLayout>
     <PageHeader title="Add Expense" />
     <ExpenseForm onSubmit={handleSubmit} isSubmitting={isLoading} />
     <Toast message={...} />
   </PageLayout>
   ```

3. **Behavior:**
   - Call store action on form submit
   - Show success toast on completion
   - Reset form after success
   - Show error toast on failure

4. **Navigation:**
   - Back button to dashboard
   - Stay on page after save for quick re-entry

**Acceptance Criteria:**
- [ ] Form renders in page layout
- [ ] Success toast after save
- [ ] Form resets after save
- [ ] Error toast on failure
- [ ] Accessible page title

---

## 🎨 Polish Tasks

### TASK-009: Add Animation and Transitions

**Status:** ⬜ Not Started  
**Priority:** P2  
**Estimated Time:** 20 minutes  
**Dependencies:** TASK-008 complete

**Task Description:**

Add subtle animations to improve UX:

1. Form field focus animations
2. Category selection pop effect
3. Success toast slide-in
4. Button loading spinner
5. Error shake animation

Use CSS transitions/animations only (no JS libraries).

**Acceptance Criteria:**
- [ ] Focus states have smooth transitions
- [ ] Category selection feels tactile
- [ ] Toast animates in/out
- [ ] Respects prefers-reduced-motion

---

### TASK-010: Mobile Optimization Pass

**Status:** ⬜ Not Started  
**Priority:** P1  
**Estimated Time:** 30 minutes  
**Dependencies:** TASK-008 complete

**Task Description:**

Test and optimize for mobile devices:

1. Touch target sizes (min 44x44px)
2. Numeric keyboard for amount
3. Date picker UX on iOS/Android
4. Category grid responsiveness
5. Viewport height issues with keyboard

**Acceptance Criteria:**
- [ ] All touch targets ≥44px
- [ ] Numeric keyboard on mobile
- [ ] Form doesn't jump when keyboard opens
- [ ] Works on iOS Safari and Chrome Android

---

### TASK-011: Accessibility Audit and Fixes

**Status:** ⬜ Not Started  
**Priority:** P1  
**Estimated Time:** 30 minutes  
**Dependencies:** TASK-008 complete

**Task Description:**

Ensure WCAG 2.1 AA compliance:

1. Run axe-core audit
2. Fix any color contrast issues
3. Verify screen reader experience
4. Add proper ARIA attributes
5. Test keyboard-only navigation

**Acceptance Criteria:**
- [ ] Zero axe-core violations
- [ ] Screen reader can complete form
- [ ] Full keyboard navigation
- [ ] Error announcements work

---

### TASK-012: Unit and Integration Tests

**Status:** ⬜ Not Started  
**Priority:** P1  
**Estimated Time:** 45 minutes  
**Dependencies:** All previous tasks

**Context Files to Include:**
- `docs/02-features/expense-entry/test-plan.md`

**Task Description:**

Write tests per the test plan:

1. Unit tests for each component
2. Integration test for full form flow
3. Store action tests
4. Validation schema tests

**Acceptance Criteria:**
- [ ] >80% coverage on form components
- [ ] Integration test: submit valid expense
- [ ] Integration test: validation errors shown
- [ ] Store action tests passing

---

## 📊 Progress Tracker

| Task | Status | Completed By | Date |
|------|--------|--------------|------|
| TASK-001 | ⬜ | - | - |
| TASK-002 | ⬜ | - | - |
| TASK-003 | ⬜ | - | - |
| TASK-004 | ⬜ | - | - |
| TASK-005 | ⬜ | - | - |
| TASK-006 | ⬜ | - | - |
| TASK-007 | ⬜ | - | - |
| TASK-008 | ⬜ | - | - |
| TASK-009 | ⬜ | - | - |
| TASK-010 | ⬜ | - | - |
| TASK-011 | ⬜ | - | - |
| TASK-012 | ⬜ | - | - |

---

## 📎 Related Documents

- [Feature Spec](./feature-spec.md)
- [Technical Design](./tech-design.md)
- [Test Plan](./test-plan.md)
- [Implementation Log](../../03-logs/implementation-log.md)
