# Feature Spec: Expense Entry

> **Feature:** Add Expense Flow  
> **Status:** In Development  
> **Owner:** Engineering Team  
> **Related PRD:** [US-101](../../01-product/prd.md#us-101-add-expense)

---

## 🎯 Purpose

Enable users to quickly log expenses with minimal friction. This is the core interaction of the app—if this flow is slow or confusing, users won't adopt the app.

---

## 👤 User Intent

**Who:** Any user who has made a purchase  
**What:** Record the expense in the app  
**When:** Ideally within minutes of the transaction  
**Why:** To build a complete picture of spending patterns

### User Journey

```
User makes a purchase
       ↓
Opens app (dashboard loads)
       ↓
Taps "Add Expense" button (floating or nav)
       ↓
Expense form appears
       ↓
Enters amount (auto-formats)
       ↓
Selects category (quick grid)
       ↓
Optionally adjusts date (defaults to today)
       ↓
Optionally adds notes
       ↓
Taps "Save"
       ↓
Success feedback → Form clears → Ready for next entry
```

---

## ✅ Acceptance Criteria

### Core Functionality

| ID | Criterion | Priority |
|----|-----------|----------|
| AC-01 | Amount field is required and validates numeric input | P0 |
| AC-02 | Amount auto-formats with currency symbol on blur | P0 |
| AC-03 | Category field is required with visual picker | P0 |
| AC-04 | Date defaults to today but is changeable | P0 |
| AC-05 | Notes field is optional with 500 char limit | P0 |
| AC-06 | Form validates before submission | P0 |
| AC-07 | Save creates record in IndexedDB | P0 |
| AC-08 | Success toast/feedback shown after save | P1 |
| AC-09 | Form clears after successful save | P0 |
| AC-10 | Keyboard accessible (tab through fields) | P1 |

### Edge Cases

| ID | Scenario | Expected Behavior |
|----|----------|-------------------|
| EC-01 | User enters letters in amount | Rejected, only numbers and decimal |
| EC-02 | User enters negative amount | Rejected, show validation error |
| EC-03 | User enters very large amount (>$999,999) | Accepted, formatted with commas |
| EC-04 | User selects future date | Rejected with friendly message |
| EC-05 | User submits without category | Validation error on category |
| EC-06 | Database write fails | Error toast with retry option |
| EC-07 | User closes form without saving | No record created, form state lost |

---

## 🎨 UI/UX Requirements

### Layout

```
┌─────────────────────────────────────┐
│        Add Expense                  │
├─────────────────────────────────────┤
│                                     │
│  Amount                             │
│  ┌─────────────────────────────┐    │
│  │ $  0.00                     │    │
│  └─────────────────────────────┘    │
│                                     │
│  Category                           │
│  ┌─────┬─────┬─────┬─────┬─────┐   │
│  │ 🍔  │ 🚗  │ 🛍️  │ 🎬  │ 📱  │   │
│  ├─────┼─────┼─────┼─────┼─────┤   │
│  │ 💊  │ ✈️  │ 📚  │ 🛒  │ +   │   │
│  └─────┴─────┴─────┴─────┴─────┘   │
│                                     │
│  Date                               │
│  ┌─────────────────────────────┐    │
│  │ Today, Jan 15, 2026         │    │
│  └─────────────────────────────┘    │
│                                     │
│  Notes (optional)                   │
│  ┌─────────────────────────────┐    │
│  │                             │    │
│  │                             │    │
│  └─────────────────────────────┘    │
│                                     │
│  ┌─────────────────────────────┐    │
│  │         Save Expense        │    │
│  └─────────────────────────────┘    │
│                                     │
└─────────────────────────────────────┘
```

### Interaction Details

| Element | Behavior |
|---------|----------|
| Amount Field | Focus on mount, large text, numeric keyboard on mobile |
| Category Grid | 2x5 grid with icons, selected state with border |
| Date Picker | Native picker on mobile, custom on desktop |
| Notes Field | Expandable textarea, character count shown |
| Save Button | Disabled until valid, loading state during save |

### Visual Design

| Property | Value |
|----------|-------|
| Form Width | 100% (max-width: 400px on desktop) |
| Spacing | 16px between form groups |
| Amount Font Size | 32px (emphasis on primary input) |
| Category Icon Size | 48px touch target |
| Button | Full width, primary color, 48px height |

---

## 📏 Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Time to complete entry | < 30 seconds | Manual testing |
| Entry completion rate | > 95% | Analytics (if added) |
| Validation error rate | < 5% | Error logging |
| Mobile usability score | > 90 | Lighthouse |

---

## 🚫 Out of Scope

- Receipt photo capture
- Voice input
- Bulk entry
- Recurring expense creation from entry
- Currency conversion

---

## 🔗 Dependencies

| Dependency | Type | Status |
|------------|------|--------|
| IndexedDB via Dexie | Technical | ✅ Ready |
| Category store | Feature | ✅ Ready |
| Date formatting utils | Utility | ✅ Ready |
| Form validation library | Library | 🚧 Evaluate options |

---

## 📎 Related Documents

- [Technical Design](./tech-design.md)
- [Dev Tasks](./dev-tasks.md)
- [Test Plan](./test-plan.md)
- [PRD](../../01-product/prd.md)
