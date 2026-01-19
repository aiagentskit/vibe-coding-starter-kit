# Insights & Learnings

> **Project:** Personal Finance Tracker  
> **Purpose:** Capture lessons learned and ideas for future improvement  
> **Update Frequency:** Ongoing, especially after sprints and releases

---

## How to Use This Document

This is your team's "learning journal" for the project. Capture:
- **What went well** - Patterns to repeat
- **What went poorly** - Mistakes to avoid
- **Ideas** - Future improvements and features
- **Technical discoveries** - Useful techniques found

Review this document during retrospectives and when starting similar projects.

---

## Technical Insights

### What Worked Well

#### 🟢 Zustand for State Management

**Context:** Chose Zustand over Redux for simplicity  
**Learning:** Perfect choice for this scale. Zero boilerplate, great DevTools integration.

**Pattern to Repeat:**
```javascript
// Simple, readable store
const useStore = create((set) => ({
  items: [],
  addItem: (item) => set((s) => ({ items: [...s.items, item] })),
}));
```

**When to Use Again:**
- Small-medium apps (< 20 store slices)
- Teams familiar with hooks
- When Redux feels like overkill

---

#### 🟢 Dexie.js for IndexedDB

**Context:** Needed local database with good DX  
**Learning:** Dexie's query API is a joy. Migrations work seamlessly.

**Pattern to Repeat:**
```javascript
// Clean query syntax
const expenses = await db.expenses
  .where('date')
  .between('2026-01-01', '2026-01-31')
  .toArray();
```

**When to Use Again:**
- Any local-first application
- When you need complex queries on IndexedDB
- Projects requiring data migrations

---

#### 🟢 Documentation-First Development with AI

**Context:** This documentation system for AI-assisted coding  
**Learning:** Having structured docs dramatically improves AI output quality.

**Key Insight:**
- Vision.md as anchor = consistent context across sessions
- Atomic tasks in dev-tasks.md = focused, successful completions
- Logs as memory = AI can pick up where last session left off

---

### What Didn't Work

#### 🔴 Manual Form State Initially

**Context:** Started with useState for form management  
**Problem:** Repetitive code, complex error handling, too many re-renders  
**Solution:** Migrated to react-hook-form mid-sprint

**Lesson:** Evaluate form complexity early. If >3 fields with validation, use a form library from the start.

**Time Lost:** ~3 hours refactoring

---

#### 🔴 Underestimating IndexedDB Edge Cases

**Context:** Assumed IndexedDB was straightforward  
**Problem:** Safari private mode silently fails, quota limits vary

**Lessons:**
- Always wrap IndexedDB operations in try-catch
- Add quota checking and warnings
- Test in private/incognito mode early

**What We Should Have Done:**
- Research browser quirks before committing to approach
- Add graceful degradation from day 1

---

#### 🔴 Delaying Accessibility Considerations

**Context:** Planned to add a11y at the end  
**Problem:** Retrofitting is harder than building in

**Specific Issues:**
- Had to restructure CategoryPicker for keyboard nav
- Focus management not planned in modal flows
- Color contrast issues required design changes

**Lesson:** Include accessibility in acceptance criteria from the start. Not as a polish task.

---

## Process Insights

### What Worked Well

#### 🟢 Feature Folders in docs/02-features/

**Learning:** Having spec, design, tasks, and tests together for each feature was excellent. Easy to find everything related to a feature.

---

#### 🟢 Atomic Tasks for AI Sessions

**Learning:** Tasks that were specific and completable in one session had much higher success rates with AI assistants.

**Good Task:**
> "Create AmountInput component with currency formatting, error states, and mobile keyboard support. See tech-design.md section X for specs."

**Bad Task:**
> "Build the expense form"

---

### What Didn't Work

#### 🔴 Not Updating system-state.md Often Enough

**Problem:** System state got stale, causing confusion about what was actually built.

**Solution:** Add to dev workflow: "Update system-state.md" as final step.

---

## Feature Ideas for Future

### Near-term (v1.x)

| Idea | Value | Effort | Notes |
|------|-------|--------|-------|
| Recurring transactions | High | Medium | Detect patterns automatically |
| Budget goals per category | High | Medium | Users have requested |
| Widget for quick add | Medium | Medium | iOS/Android PWA widgets |
| Voice entry | Medium | High | "Twenty dollars for lunch" |

### Long-term (v2.0+)

| Idea | Value | Effort | Notes |
|------|-------|--------|-------|
| Optional cloud sync | High | High | User-controlled, E2E encrypted |
| Bank statement import | High | High | CSV/OFX parsing |
| Multiple currencies | Medium | Medium | Display only, no conversion |
| Family/shared tracking | Medium | High | Requires accounts |
| AI-powered insights | Medium | High | "You spent 20% more on food this month" |

---

## Retrospective Notes

### Sprint 1 Retro (2026-01-17)

**What went well:**
- Documentation system helped everyone stay aligned
- AI pairing worked better than expected with context docs

**What to improve:**
- Need better handoff between developers (see logs more often)
- Should have spiked IndexedDB earlier to find edge cases

**Action items:**
- [ ] Add IndexedDB testing to onboarding checklist
- [ ] Create a "start of day" ritual: read latest implementation-log entries

---

### Sprint 2 Retro (2026-01-31)

*To be added*

---

## Knowledge Base

### Useful Code Patterns

#### Currency Formatting
```javascript
const formatCurrency = (cents) => {
  return (cents / 100).toLocaleString('en-US', {
    style: 'currency',
    currency: 'USD',
  });
};
```

#### Safe IndexedDB Operation
```javascript
const safeDbOperation = async (operation) => {
  try {
    return await operation();
  } catch (error) {
    if (error.name === 'QuotaExceededError') {
      // Handle storage full
    }
    throw error;
  }
};
```

### External Resources

- [Dexie.js Documentation](https://dexie.org/docs/)
- [Zustand Best Practices](https://github.com/pmndrs/zustand)
- [PWA Checklist](https://web.dev/pwa-checklist/)
- [IndexedDB Browser Support](https://caniuse.com/indexeddb)

---

## Quotes & Testimonials

*Save notable quotes from users or team members*

> "The documentation system made it so easy to onboard our new developer."  
> — Team Lead

> "I love that I can export my data anytime. Finally an app that respects my privacy."  
> — Beta User

---

## 📎 Related Documents

- [Assumptions](../00-context/assumptions.md) - Update when assumptions are validated
- [Decisions Log](./decisions-log.md) - Reference when proposing changes
- [Validation Log](./validation-log.md) - Source of user feedback
