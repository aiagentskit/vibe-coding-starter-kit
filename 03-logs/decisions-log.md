# Decisions Log

> **Project:** Personal Finance Tracker  
> **Purpose:** Record architectural and product decisions with rationale  
> **Format:** ADR (Architecture Decision Record)

---

## How to Use This Log

When making a significant decision, document it here using the ADR format:
- **Context**: What prompted this decision?
- **Decision**: What was decided?
- **Rationale**: Why this choice over alternatives?
- **Consequences**: What are the tradeoffs?

This prevents re-litigating the same decisions and provides context for future team members or AI assistants.

---

## Active Decisions

### ADR-001: State Management Library

**Date:** 2026-01-10  
**Status:** ✅ Accepted  
**Decision Makers:** Engineering Team

#### Context

We need a state management solution for the React app. Options considered:
- Redux Toolkit
- Zustand
- Jotai
- React Context + useReducer
- MobX

#### Decision

**Use Zustand** for global state management.

#### Rationale

| Criteria | Redux | Zustand | Context | Winner |
|----------|-------|---------|---------|--------|
| Bundle size | 11KB | 1.1KB | 0KB | Context |
| Boilerplate | High | Low | Medium | Zustand |
| DevTools | Excellent | Good | Basic | Redux |
| Learning curve | Steep | Minimal | Minimal | Zustand |
| Fits project scale | Overkill | Perfect | Okay | Zustand |

- **Small bundle**: At 1.1KB gzipped, minimal impact on load time
- **Minimal boilerplate**: No actions, reducers, slices—just stores
- **Hooks-based API**: Feels natural with modern React
- **Sufficient for scope**: This app doesn't need Redux's power

#### Consequences

**Positive:**
- Faster development with less code
- Easier onboarding for new developers
- Good React DevTools integration

**Negative:**
- Less ecosystem/middleware than Redux
- Team familiar with Redux may need to adjust

**Mitigations:**
- Document patterns in this codebase
- Use Zustand middleware for persistence if needed later

---

### ADR-002: IndexedDB Wrapper Library

**Date:** 2026-01-10  
**Status:** ✅ Accepted  
**Decision Makers:** Engineering Team

#### Context

We need to interact with IndexedDB for local storage. Options:
- Raw IndexedDB API
- Dexie.js
- idb
- localForage

#### Decision

**Use Dexie.js** for IndexedDB operations.

#### Rationale

| Library | API Ergonomics | Query Support | Size | Migrations |
|---------|----------------|---------------|------|------------|
| Raw IndexedDB | Poor | Manual | 0KB | Manual |
| Dexie.js | Excellent | Built-in | 30KB | Built-in |
| idb | Good | Limited | 1.5KB | None |
| localForage | Okay | Limited | 8KB | None |

- **Excellent query API**: `db.expenses.where('date').between(start, end).toArray()`
- **Schema migrations built-in**: `db.version(2).stores().upgrade()`
- **Promise-based**: No callback hell
- **TypeScript support**: Good types out of the box

#### Consequences

**Positive:**
- Much cleaner code for database operations
- Migration path for schema changes
- Good error handling

**Negative:**
- 30KB added to bundle (acceptable for this app)
- Another library to maintain

---

### ADR-003: Currency Storage Format

**Date:** 2026-01-12  
**Status:** ✅ Accepted  
**Decision Makers:** Engineering Team

#### Context

How should we store currency amounts in IndexedDB?

Options:
1. Float/decimal (e.g., 19.99)
2. Integer cents (e.g., 1999)
3. String (e.g., "19.99")

#### Decision

**Store amounts as integer cents** (e.g., $19.99 = 1999).

#### Rationale

- **Avoids floating point errors**: 0.1 + 0.2 ≠ 0.3 in JavaScript
- **Faster arithmetic**: Integer ops faster than float
- **Industry standard**: Banks and payment processors use this approach
- **Smaller storage**: Integers compress better

**Conversion:**
- Input: Parse, multiply by 100, round
- Display: Divide by 100, format with locale

#### Consequences

**Positive:**
- No rounding errors in calculations
- Totals will always be accurate

**Negative:**
- Extra conversion code needed
- Developer must remember the format
- Edge case: very large amounts (billions) might overflow (not a realistic concern for personal finance)

**Implementation:**
```javascript
// Input to storage
const cents = Math.round(parseFloat(input) * 100);

// Storage to display
const dollars = (cents / 100).toLocaleString('en-US', {
  style: 'currency',
  currency: 'USD'
});
```

---

### ADR-004: Date Storage Format

**Date:** 2026-01-12  
**Status:** ✅ Accepted  
**Decision Makers:** Engineering Team

#### Context

How should we store dates in IndexedDB?

Options:
1. JavaScript Date object
2. Unix timestamp (milliseconds)
3. ISO 8601 string (YYYY-MM-DD)
4. Full ISO 8601 with time (YYYY-MM-DDTHH:mm:ss.sssZ)

#### Decision

**Store dates as ISO 8601 date strings** (YYYY-MM-DD format).

#### Rationale

- **Human readable**: Easy to debug and inspect
- **Sortable as strings**: Lexicographic order = chronological order
- **No timezone issues**: Dates only, no time component
- **Easy to query**: Can use string comparison for ranges

#### Consequences

**Positive:**
- Simple to work with
- Clear in debugging
- Works well with date-fns parseISO()

**Negative:**
- Slightly larger than timestamp
- No sub-day precision (not needed for this app)

---

### ADR-005: Component Styling Approach

**Date:** 2026-01-10  
**Status:** ✅ Accepted  
**Decision Makers:** Engineering Team

#### Context

How should we handle component styling?

Options:
1. CSS Modules
2. styled-components
3. Tailwind CSS
4. Plain CSS with BEM
5. Emotion

#### Decision

**Use CSS Modules** for component styling.

#### Rationale

- **Zero runtime cost**: Styles resolved at build time
- **Scoped by default**: No class name collisions
- **Vite integration**: Works out of the box
- **Familiar**: Just CSS, no new syntax
- **No library lock-in**: Can migrate easily

#### Consequences

**Positive:**
- Fast, no style injection at runtime
- Type-safe with TypeScript plugin
- CSS features like :hover work normally

**Negative:**
- Verbose for dynamic styles (use inline for those)
- Can't share styles easily (use CSS variables)

---

### ADR-006: Form Library Choice

**Date:** 2026-01-12  
**Status:** ✅ Accepted  
**Decision Makers:** Frontend Developer

#### Context

Initially planned to use manual form state with useState. During implementation, found this led to:
- Repetitive validation code
- Complex error handling
- Difficulty with field-level re-renders

Options:
1. Manual useState + custom hooks
2. React Hook Form
3. Formik
4. React Final Form

#### Decision

**Use React Hook Form** with Zod resolver.

#### Rationale

- **Performance**: Uncontrolled inputs by default, minimal re-renders
- **Bundle size**: ~9KB gzipped (Formik is 15KB)
- **Zod integration**: First-class resolver support
- **Developer experience**: Minimal boilerplate

#### Consequences

**Positive:**
- Faster form interactions
- Cleaner component code
- Type-safe form data with Zod

**Negative:**
- Requires learning RHF API
- Uncontrolled inputs can be tricky for some cases

**Migration Note:** This was a mid-development change. See implementation-log.md Session 4.

---

## Proposed Decisions

### ADR-007: Toast Notification Approach

**Date:** 2026-01-15  
**Status:** 🟡 Proposed  
**Decision Makers:** Pending

#### Context

Need to show success/error feedback to users. Options:
1. Build custom toast component
2. Use react-hot-toast
3. Use sonner
4. Use notistack

#### Options Analysis

| Library | Size | Features | API |
|---------|------|----------|-----|
| Custom | 0KB | What we build | Full control |
| react-hot-toast | 5KB | Good | Clean |
| sonner | 3KB | Excellent | Clean |
| notistack | 8KB | Features++ | Complex |

#### Recommendation

Leaning toward **sonner** - small, modern, great UX.

#### Open Questions

- Do we need stacked notifications?
- Do we need actions in toasts?

---

## Superseded Decisions

*Decisions that were made but later changed.*

*None yet.*

---

## 📎 Related Documents

- [Implementation Log](./implementation-log.md)
- [Technical Design](../02-features/expense-entry/tech-design.md)
- [Assumptions](../00-context/assumptions.md)
