# Assumptions, Risks, and Unknowns

> **Last Updated:** 2026-01-15  
> **Review Cycle:** Weekly  
> **Owner:** Product Team

---

## 📋 Active Assumptions

Assumptions are things we believe to be true but haven't validated. Each assumption should be tracked until validated or invalidated.

### Product Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| A1 | Users prefer manual entry over bank connections | Build wrong product | User interviews (n=10) | ⏳ Pending |
| A2 | Weekly spending summary is sufficient (not daily) | Feature gap | A/B test post-launch | ⏳ Pending |
| A3 | 10-15 default categories cover 90% of expenses | Poor UX, user frustration | Analytics on custom category usage | ⏳ Pending |
| A4 | Users will remember to log expenses same-day | Data quality issues | Prompt for frequency in onboarding | ⏳ Pending |

### Technical Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| T1 | IndexedDB is sufficient for 5+ years of data | Performance issues | Load testing with 50K entries | ⏳ Pending |
| T2 | Service Worker caching handles offline adequately | Broken offline experience | Manual testing on airplane mode | ⏳ Pending |
| T3 | Modern browsers (Chrome, Firefox, Safari) cover 95% of users | Compatibility issues | Browser share research | ✅ Validated |
| T4 | No backend needed for MVP features | Architectural rework later | Scope review | ✅ Validated |

### Business Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| B1 | Users exist who want local-only finance apps | No market fit | Landing page test | ⏳ Pending |
| B2 | Free tier with optional donations is viable | No revenue | Monitor donation conversion | ⏳ Pending |

---

## ⚠️ Known Risks

### High Priority Risks

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|----|------|------------|--------|------------|-------|
| R1 | Users forget to log expenses, leading to incomplete data | High | Medium | Add reminder notifications (PWA), prompt patterns | Product |
| R2 | IndexedDB data loss on browser clear | Medium | High | Prominent export reminders, auto-backup prompts | Engineering |
| R3 | Category suggestions are inaccurate | Medium | Medium | Allow easy re-categorization, learn from corrections | Engineering |

### Medium Priority Risks

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|----|------|------------|--------|------------|-------|
| R4 | PWA install flow is confusing for users | Medium | Low | Clear install instructions, fallback to bookmark | Design |
| R5 | Charts/graphs not accessible for screen readers | Low | Medium | Provide tabular data alternatives | Engineering |
| R6 | Large data sets slow down dashboard | Low | Medium | Pagination, lazy loading, virtual scrolling | Engineering |

---

## ❓ Open Questions (Unknowns)

Questions we need answered before or during development.

### Must Answer Before v1.0

| ID | Question | Decision Needed By | Owner | Status |
|----|----------|-------------------|-------|--------|
| Q1 | What date format should we use? ISO or locale? | Before UI work | Design | 🔴 Open |
| Q2 | Should we include income tracking or just expenses? | Before data model | Product | 🔴 Open |
| Q3 | How do we handle deleted categories with existing entries? | Before category feature | Engineering | 🔴 Open |
| Q4 | What's our approach for currency formatting? | Before entry UI | Engineering | 🔴 Open |

### Can Answer During Development

| ID | Question | Notes | Status |
|----|----------|-------|--------|
| Q5 | Optimal number of recent transactions to show on dashboard? | Start with 10, adjust based on feedback | 🟡 Parked |
| Q6 | Should category icons be emoji or SVG? | Emoji simpler, SVG more consistent | 🟡 Parked |
| Q7 | Chart library choice: Chart.js vs lightweight alternative? | Evaluate bundle size impact | 🟡 Parked |

---

## 🔄 Dependency Risks

External dependencies that could impact the project.

| Dependency | Risk | Alternative | Status |
|------------|------|-------------|--------|
| IndexedDB Browser Support | If dropped by browsers, app breaks | LocalStorage fallback (limited) | ✅ Stable |
| Service Worker API | If implementation changes, offline breaks | Graceful degradation | ✅ Stable |
| PWA Manifest | Cross-browser inconsistencies | Document browser-specific behaviors | 🟡 Monitor |

---

## 📊 Assumption Validation Log

Track validation outcomes here.

### Validated ✅

| ID | Assumption | Outcome | Date | Notes |
|----|------------|---------|------|-------|
| T3 | Modern browsers cover 95% of users | Validated | 2026-01-10 | StatCounter data confirms 96.2% |
| T4 | No backend needed for MVP | Validated | 2026-01-12 | Architecture review complete |

### Invalidated ❌

| ID | Assumption | Outcome | Date | Action Taken |
|----|------------|---------|------|--------------|
| - | - | - | - | - |

---

## 📅 Next Review

**Scheduled:** 2026-01-22  
**Focus Areas:** 
- Validate A1 through user interviews
- Resolve Q1-Q4 before sprint 2
- Update risk assessment based on technical spike results

---

## 📎 Related Documents

- [Vision](./vision.md)
- [System State](./system-state.md)
- [Decisions Log](../03-logs/decisions-log.md)
