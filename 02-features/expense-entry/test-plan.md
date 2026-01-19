# Test Plan: Expense Entry

> **Feature:** Add Expense Flow  
> **Status:** Draft  
> **Last Updated:** 2026-01-15  
> **Owner:** QA/Engineering

---

## 📋 Overview

This document defines the testing strategy for the expense entry feature, including unit tests, integration tests, and manual testing procedures.

**Testing Priorities:**
1. Data integrity (expenses save correctly)
2. Validation (invalid data rejected)
3. User experience (form is intuitive)
4. Accessibility (usable by all)

---

## 🎯 Test Coverage Goals

| Test Type | Target Coverage | Status |
|-----------|-----------------|--------|
| Unit Tests | 80%+ | ⬜ Pending |
| Integration Tests | Core flows | ⬜ Pending |
| E2E Tests | Happy path | ⬜ Pending |
| Accessibility | WCAG 2.1 AA | ⬜ Pending |
| Cross-browser | Modern browsers | ⬜ Pending |

---

## 🧪 Unit Tests

### AmountInput Component

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| AMT-01 | Render with default props | Shows $0.00 placeholder |
| AMT-02 | Format on blur (1234.5) | Displays "$1,234.50" |
| AMT-03 | Strip formatting on focus | Value is editable number |
| AMT-04 | Reject letters | Input unchanged |
| AMT-05 | Reject multiple decimals | Only first decimal kept |
| AMT-06 | Show error state | Error message visible, aria-invalid |
| AMT-07 | Currency symbol prop | Shows custom symbol |
| AMT-08 | Mobile keyboard | inputMode is decimal |

```javascript
// Example test
describe('AmountInput', () => {
  it('formats value on blur', () => {
    const { getByRole } = render(<AmountInput value="1234.5" onChange={() => {}} />);
    const input = getByRole('textbox');
    fireEvent.blur(input);
    expect(input.value).toBe('$1,234.50');
  });
});
```

---

### CategoryPicker Component

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| CAT-01 | Render with categories | Shows all categories in grid |
| CAT-02 | Select a category | Calls onChange with ID |
| CAT-03 | Visual selected state | Selected category highlighted |
| CAT-04 | Keyboard navigation | Arrow keys move selection |
| CAT-05 | Enter to select | Confirms selection |
| CAT-06 | Show error state | Error message visible |
| CAT-07 | Loading state | Skeleton shown while loading |
| CAT-08 | Empty state | Message when no categories |

---

### DateInput Component

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| DATE-01 | Default to today | Shows "Today, [date]" |
| DATE-02 | Yesterday selected | Shows "Yesterday, [date]" |
| DATE-03 | Past date | Shows formatted date |
| DATE-04 | Block future date | Cannot select beyond today |
| DATE-05 | Show error state | Error message visible |
| DATE-06 | Parse input correctly | Date object is valid |

---

### NotesInput Component

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| NOTE-01 | Show character count | Displays "0/500" |
| NOTE-02 | Update count on input | Count reflects input length |
| NOTE-03 | Warning at limit | Color changes at 450+ |
| NOTE-04 | Enforce max length | Cannot exceed 500 chars |
| NOTE-05 | Show placeholder | Placeholder visible when empty |

---

### Expense Schema

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| SCHEMA-01 | Valid complete data | Passes validation |
| SCHEMA-02 | Missing amount | Returns amount error |
| SCHEMA-03 | Negative amount | Returns amount error |
| SCHEMA-04 | Missing category | Returns category error |
| SCHEMA-05 | Future date | Returns date error |
| SCHEMA-06 | Notes too long | Truncates or errors |
| SCHEMA-07 | Amount too large | Returns amount error |

---

### Expense Store

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| STORE-01 | addExpense success | Expense in state & DB |
| STORE-02 | addExpense converts amount | Stored as cents |
| STORE-03 | addExpense adds timestamps | createdAt/updatedAt set |
| STORE-04 | addExpense DB failure | Error thrown, state unchanged |

---

## 🔗 Integration Tests

### Full Form Submission

| Test ID | Description | Steps | Expected Result |
|---------|-------------|-------|-----------------|
| INT-01 | Submit valid expense | Enter amount, select category, save | Expense saved, form reset, toast shown |
| INT-02 | Submit with notes | Fill all fields including notes | All data saved correctly |
| INT-03 | Validation errors shown | Submit empty form | All required field errors shown |
| INT-04 | Fix and resubmit | Submit invalid, fix, submit | Errors clear, expense saves |
| INT-05 | Rapid entry mode | Save expense, immediately add another | Form ready for second entry |

```javascript
// Example integration test
describe('Expense Form Flow', () => {
  it('saves a complete expense', async () => {
    render(<AddExpensePage />);
    
    // Enter amount
    await userEvent.type(screen.getByLabelText(/amount/i), '45.99');
    
    // Select category
    await userEvent.click(screen.getByRole('button', { name: /food/i }));
    
    // Submit
    await userEvent.click(screen.getByRole('button', { name: /save/i }));
    
    // Verify success
    await waitFor(() => {
      expect(screen.getByText(/expense saved/i)).toBeInTheDocument();
    });
    
    // Verify DB
    const expenses = await db.expenses.toArray();
    expect(expenses[0].amount).toBe(4599);
    expect(expenses[0].categoryId).toBe(1);
  });
});
```

---

## 🖐️ Manual Testing Checklist

### Happy Path Testing

| Step | Action | Expected Result | ✓ |
|------|--------|-----------------|---|
| 1 | Open app | Dashboard loads | ⬜ |
| 2 | Tap "Add Expense" | Form appears, amount focused | ⬜ |
| 3 | Type "19.99" | Amount shown | ⬜ |
| 4 | Tap Food category | Category highlighted | ⬜ |
| 5 | Tap Save | Success toast, form clears | ⬜ |
| 6 | Check dashboard | New expense visible | ⬜ |
| 7 | Refresh page | Expense persists | ⬜ |

---

### Edge Cases Testing

| Scenario | Steps | Expected Result | ✓ |
|----------|-------|-----------------|---|
| Empty submit | Open form, tap Save | All required fields show errors | ⬜ |
| Letters in amount | Try typing "abc" | Nothing appears | ⬜ |
| Negative amount | Type "-10" | Error message | ⬜ |
| Huge amount | Type "9999999.99" | Formats with commas | ⬜ |
| Future date | Select tomorrow | Date rejected | ⬜ |
| Long notes | Paste 600 chars | Truncated at 500 | ⬜ |
| Offline submit | Enable airplane mode, save | Works, syncs NOT required | ⬜ |
| Quick double-tap | Double-tap Save fast | Only one expense created | ⬜ |

---

## ♿ Accessibility Testing

### Keyboard Navigation

| Test | Steps | Expected | ✓ |
|------|-------|----------|---|
| Tab order | Tab through form | Logical: amount → category → date → notes → save | ⬜ |
| Enter to submit | Fill form, press Enter | Form submits | ⬜ |
| Escape to cancel | Press Escape on form | Form resets (if modal) | ⬜ |
| Category arrows | Arrow keys in picker | Selection moves | ⬜ |
| Category Enter | Press Enter on category | Category selected | ⬜ |

### Screen Reader

| Test | Steps | Expected | ✓ |
|------|-------|----------|---|
| Form labels | Tab through with VoiceOver | All fields announced | ⬜ |
| Error announcement | Submit invalid | Errors announced | ⬜ |
| Success announcement | Submit valid | "Expense saved" announced | ⬜ |
| Category grid | Navigate grid | Current selection announced | ⬜ |

### Visual

| Test | Tool | Expected | ✓ |
|------|------|----------|---|
| Contrast | axe DevTools | No contrast issues | ⬜ |
| Focus visible | Manual | Focus ring on all elements | ⬜ |
| Zoom 200% | Browser zoom | Layout not broken | ⬜ |
| Reduced motion | OS setting | No animations | ⬜ |

---

## 📱 Cross-Browser Testing

| Browser | Version | Device | Status |
|---------|---------|--------|--------|
| Chrome | 120+ | Desktop | ⬜ Pending |
| Firefox | 120+ | Desktop | ⬜ Pending |
| Safari | 17+ | Desktop | ⬜ Pending |
| Edge | 120+ | Desktop | ⬜ Pending |
| Chrome | Latest | Android | ⬜ Pending |
| Safari | Latest | iOS 17+ | ⬜ Pending |

### Mobile-Specific Tests

| Test | Device | Expected | ✓ |
|------|--------|----------|---|
| Numeric keyboard | iOS | Number pad for amount | ⬜ |
| Numeric keyboard | Android | Number pad for amount | ⬜ |
| Date picker | iOS | Native picker works | ⬜ |
| Date picker | Android | Native picker works | ⬜ |
| Touch targets | Any | All ≥44px | ⬜ |
| Keyboard open | Any | Form doesn't jump oddly | ⬜ |

---

## 📊 Performance Testing

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| Time to Interactive | < 2s | - | ⬜ Pending |
| Form render | < 100ms | - | ⬜ Pending |
| Save operation | < 500ms | - | ⬜ Pending |
| Re-renders on input | Minimal | - | ⬜ Pending |

---

## 🐛 Known Issues / Risks

| Risk | Mitigation | Status |
|------|------------|--------|
| IndexedDB quota | Show warning at 80% | ⬜ TODO |
| Safari private mode | Detect and warn user | ⬜ TODO |
| Concurrent saves | Queue operations | ⬜ Low priority |

---

## ✅ Sign-Off

| Role | Name | Date | Status |
|------|------|------|--------|
| Developer | - | - | ⬜ |
| QA | - | - | ⬜ |
| Product | - | - | ⬜ |

---

## 📎 Related Documents

- [Feature Spec](./feature-spec.md)
- [Technical Design](./tech-design.md)
- [Dev Tasks](./dev-tasks.md)
- [Bug Log](../../03-logs/bug-log.md)
