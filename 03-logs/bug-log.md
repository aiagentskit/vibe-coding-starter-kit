# Bug Log

> **Project:** Personal Finance Tracker  
> **Purpose:** Track bugs, their fixes, and root causes  
> **Update Frequency:** When bugs are found or fixed

---

## How to Use This Log

When a bug is found:
1. Create an entry with a unique ID
2. Document reproduction steps
3. Track investigation and fix

This log helps:
- Prevent regression by documenting root causes
- Speed up future debugging with similar issues
- Provide context for AI assistants when debugging

---

## Summary

| Status | Count |
|--------|-------|
| 🔴 Open | 2 |
| 🟡 In Progress | 1 |
| ✅ Fixed | 1 |
| Total | 4 |

---

## Open Bugs

### BUG-001: Date picker not respecting locale

**Status:** 🔴 Open  
**Severity:** Low  
**Reported:** 2026-01-14  
**Reporter:** QA Team

#### Description

Date picker displays dates in MM/DD/YYYY format regardless of user locale. German users expect DD.MM.YYYY.

#### Reproduction Steps

1. Set browser locale to de-DE
2. Open Add Expense page
3. Click date picker
4. Note the date format

**Expected:** DD.MM.YYYY format  
**Actual:** MM/DD/YYYY format

#### Screenshots

*Placeholder - add when available*

#### Investigation Notes

- Native `<input type="date">` should respect locale
- May be a CSS issue overriding native picker
- Check if we're using a custom date formatter that ignores locale

#### Related

- Feature: Expense Entry
- File: `src/components/expense/DateInput/DateInput.jsx`

---

### BUG-002: Category picker closes on mobile tap

**Status:** 🟡 In Progress  
**Severity:** Medium  
**Reported:** 2026-01-14  
**Reporter:** Developer during testing  
**Assigned:** Frontend Developer

#### Description

On mobile devices (iOS Safari primarily), tapping a category sometimes closes the picker without selecting. Seems to happen when tapping near the edge of a category button.

#### Reproduction Steps

1. Open Add Expense on iOS Safari
2. Tap to expand category picker
3. Try to select a category by tapping near the edge
4. ~30% of the time, picker closes without selection

**Expected:** Category selected  
**Actual:** Picker closes, no selection made

#### Investigation Notes

- **2026-01-14:** Initial report, confirmed reproduction
- **2026-01-15:** Investigated touch target sizes
  - Current: 48x48px touch targets
  - CSS looks correct
  - May be event bubbling issue
  - Added `e.stopPropagation()` to test - no change
- **2026-01-15:** Suspect this is a focus-blur battle
  - Category picker is inside form
  - Selecting might trigger blur on amount field
  - Blur handler might be interfering
  - **Next step:** Check blur handlers, add console logs

#### Possible Solutions

1. Debounce blur handler
2. Use mousedown instead of click
3. Add touch-specific handlers

#### Related

- Feature: Expense Entry
- File: `src/components/expense/CategoryPicker/CategoryPicker.jsx`

---

### BUG-003: Export includes deleted expenses

**Status:** 🔴 Open  
**Severity:** Low  
**Reported:** 2026-01-15  
**Reporter:** QA Team

#### Description

When exporting data to JSON, deleted expenses are included in the export. They appear to have a `deletedAt` timestamp.

#### Reproduction Steps

1. Add an expense
2. Delete the expense
3. Export data as JSON
4. Open JSON file
5. Deleted expense is present

**Expected:** Only active expenses exported  
**Actual:** Deleted expenses included

#### Investigation Notes

- We're using soft delete (setting deletedAt) - this is by design
- But export should filter these out
- Check the export function in `src/utils/export.js`

#### Related

- Feature: Data Export
- File: `src/utils/export.js` (likely)

---

## Fixed Bugs

### BUG-004: Amount field accepts multiple decimal points

**Status:** ✅ Fixed  
**Severity:** Medium  
**Reported:** 2026-01-13  
**Fixed:** 2026-01-13  
**Fixed By:** Frontend Developer

#### Description

Users could enter values like "12.34.56" in the amount field.

#### Root Cause

The input filter only checked for non-numeric characters, not for multiple decimals.

#### Fix

```javascript
// Before
const filtered = value.replace(/[^0-9.]/g, '');

// After
const filtered = value.replace(/[^0-9.]/g, '');
const parts = filtered.split('.');
const sanitized = parts.length > 2 
  ? parts[0] + '.' + parts.slice(1).join('') 
  : filtered;
```

#### Verification

- [x] Manual test: Cannot enter multiple decimals
- [x] Added unit test: `AMT-05` in test suite
- [x] No regression on other input behaviors

#### Commits

- `abc1234` - Fix: Prevent multiple decimal points in amount input

---

## Bug Template

Copy this for new bugs:

```markdown
### BUG-XXX: [Short description]

**Status:** 🔴 Open | 🟡 In Progress | ✅ Fixed  
**Severity:** Critical | High | Medium | Low  
**Reported:** YYYY-MM-DD  
**Reporter:** [Name/Role]

#### Description

[What's happening vs what should happen]

#### Reproduction Steps

1. [Step 1]
2. [Step 2]
3. [Step 3]

**Expected:** [Expected behavior]  
**Actual:** [Actual behavior]

#### Investigation Notes

- [Investigation entries dated]

#### Root Cause

[Once identified]

#### Fix

[Code changes or approach]

#### Related

- Feature: [Feature name]
- File: [Relevant file paths]
```

---

## Regression Prevention Checklist

After fixing a bug, ensure:

- [ ] Root cause documented
- [ ] Unit/integration test added
- [ ] Similar code patterns checked across codebase
- [ ] Fix documented in implementation-log.md
- [ ] If architectural issue, ADR added to decisions-log.md

---

## 📎 Related Documents

- [Implementation Log](./implementation-log.md)
- [Test Plans](../02-features/)
- [Validation Log](./validation-log.md)
