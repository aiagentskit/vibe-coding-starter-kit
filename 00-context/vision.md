# Product Vision: Personal Finance Tracker

> **Last Updated:** 2026-01-15  
> **Status:** Active Development  
> **Owner:** Product Team

---

## 🎯 Purpose

Build a **simple, privacy-focused personal finance tracker** that helps individuals understand their spending patterns without the complexity of traditional budgeting apps.

### The Problem We're Solving

People want to understand where their money goes, but:
- Most finance apps are overwhelming with features
- Bank apps show transactions but not insights
- Spreadsheets require too much manual effort
- Privacy concerns prevent adoption of third-party apps

### Our Solution

A **local-first** expense tracker that:
- Runs entirely in the browser (no server required)
- Stores data locally (IndexedDB)
- Provides automatic categorization
- Generates simple, actionable insights

---

## 👤 Target Users

### Primary Persona: "Conscious Spender"

- **Age:** 25-40
- **Profile:** Working professional who earns decent income
- **Pain Point:** Knows they should track spending but finds existing tools tedious
- **Goal:** Quick weekly overview of spending patterns
- **Tech Comfort:** Medium - uses apps daily but not a power user

### Secondary Persona: "Privacy-First Saver"

- **Age:** 30-50
- **Profile:** Security-conscious individual
- **Pain Point:** Won't connect bank accounts to third-party apps
- **Goal:** Manual entry with offline-first capability
- **Tech Comfort:** High - understands local-first benefits

---

## 🚫 Boundaries (What We're NOT Building)

| We Will NOT | Rationale |
|-------------|-----------|
| Connect to bank APIs | Privacy-first approach; too complex for MVP |
| Require user accounts | No server = no accounts needed |
| Build mobile apps | Web-first, PWA for mobile access |
| Support multiple currencies | English + USD only for v1.0 |
| Provide investment tracking | Out of scope; many tools do this well |
| Build collaborative features | Personal use only |

---

## ⭐ North Star Metrics

| Metric | Target | Rationale |
|--------|--------|-----------|
| **Time to First Entry** | < 30 seconds | Must be frictionless |
| **Weekly Active Sessions** | 2+ per user | Indicates habit formation |
| **Entry Completion Rate** | > 90% | Shows UI isn't frustrating |
| **Data Export Success** | 100% | Users own their data |

---

## 🏛️ Core Principles

### 1. Privacy by Design
- All data stays in browser's IndexedDB
- No analytics, no tracking, no phone home
- Export to JSON/CSV anytime

### 2. Simplicity Over Features
- MVP has exactly 4 screens: Add Entry, Dashboard, Categories, Settings
- No feature creep until core loop is validated
- Each screen must be learnable in < 10 seconds

### 3. Offline-First
- Works without internet connection
- PWA with service worker caching
- Sync is a future consideration, not MVP

### 4. Honest Insights
- No gamification that manipulates behavior
- Clear, factual summaries
- User decides what "good" spending looks like

---

## 🔮 Future Considerations (Post-MVP)

These are explicitly OUT of scope for v1.0 but inform architectural decisions:

- [ ] Optional cloud sync (user-controlled encryption keys)
- [ ] Multiple currency support
- [ ] Recurring transaction detection
- [ ] Budget goal setting
- [ ] Receipt photo scanning (OCR)

---

## 📏 Success Definition for v1.0

The MVP is successful when:

1. ✅ User can add an expense in under 30 seconds
2. ✅ User can see weekly/monthly spending breakdown by category
3. ✅ All data persists locally across browser sessions
4. ✅ User can export all data as JSON or CSV
5. ✅ App works fully offline after first load

---

## 📎 Related Documents

- [Assumptions & Risks](./assumptions.md)
- [System State](./system-state.md)
- [Product Requirements](../01-product/prd.md)
