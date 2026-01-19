# Template: Assumptions, Risks, and Unknowns

> **Purpose:** Track what we believe, what could go wrong, and what we don't know  
> **When to create:** At project start, alongside vision.md  
> **Update frequency:** Weekly or when assumptions are validated/invalidated  
> **Output location:** `00-context/assumptions.md`

---

## LLM Instructions

When filling this template:
1. Every assumption should have a validation method - how will you prove/disprove it?
2. Risks need mitigation strategies, not just identification
3. Open questions should have owners and deadlines
4. Update this document as assumptions are validated - this is a living document
5. Link to decisions-log.md when assumptions lead to architectural decisions

---

## Template

```markdown
# Assumptions, Risks, and Unknowns

> **Last Updated:** {{DATE}}  
> **Review Cycle:** Weekly  
> **Owner:** {{OWNER}}

---

## 📋 Active Assumptions

*Things we believe to be true but haven't validated.*

### Product Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| A1 | {{ASSUMPTION}} | {{CONSEQUENCE}} | {{HOW_TO_VALIDATE}} | ⏳ Pending |
| A2 | {{ASSUMPTION}} | {{CONSEQUENCE}} | {{HOW_TO_VALIDATE}} | ⏳ Pending |

### Technical Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| T1 | {{ASSUMPTION}} | {{CONSEQUENCE}} | {{HOW_TO_VALIDATE}} | ⏳ Pending |
| T2 | {{ASSUMPTION}} | {{CONSEQUENCE}} | {{HOW_TO_VALIDATE}} | ⏳ Pending |

### Business Assumptions

| ID | Assumption | Risk if Wrong | Validation Method | Status |
|----|------------|---------------|-------------------|--------|
| B1 | {{ASSUMPTION}} | {{CONSEQUENCE}} | {{HOW_TO_VALIDATE}} | ⏳ Pending |

---

## ⚠️ Known Risks

### High Priority Risks

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|----|------|------------|--------|------------|-------|
| R1 | {{RISK_DESCRIPTION}} | High/Medium/Low | High/Medium/Low | {{MITIGATION}} | {{OWNER}} |

### Medium Priority Risks

| ID | Risk | Likelihood | Impact | Mitigation | Owner |
|----|------|------------|--------|------------|-------|
| R2 | {{RISK_DESCRIPTION}} | High/Medium/Low | High/Medium/Low | {{MITIGATION}} | {{OWNER}} |

---

## ❓ Open Questions (Unknowns)

### Must Answer Before v1.0

| ID | Question | Decision Needed By | Owner | Status |
|----|----------|-------------------|-------|--------|
| Q1 | {{QUESTION}} | {{DATE}} | {{OWNER}} | 🔴 Open |
| Q2 | {{QUESTION}} | {{DATE}} | {{OWNER}} | 🔴 Open |

### Can Answer During Development

| ID | Question | Notes | Status |
|----|----------|-------|--------|
| Q3 | {{QUESTION}} | {{NOTES}} | 🟡 Parked |

---

## 🔄 Dependency Risks

| Dependency | Risk | Alternative | Status |
|------------|------|-------------|--------|
| {{DEPENDENCY}} | {{RISK}} | {{ALTERNATIVE}} | ✅ Stable / 🟡 Monitor / 🔴 Concern |

---

## 📊 Assumption Validation Log

### Validated ✅

| ID | Assumption | Outcome | Date | Notes |
|----|------------|---------|------|-------|
| - | - | - | - | - |

### Invalidated ❌

| ID | Assumption | Outcome | Date | Action Taken |
|----|------------|---------|------|--------------|
| - | - | - | - | - |

---

## 📅 Next Review

**Scheduled:** {{DATE}}  
**Focus Areas:** {{WHAT_TO_REVIEW}}

---

## 📎 Related Documents

- [Vision](./vision.md)
- [System State](./system-state.md)
- [Decisions Log](../03-logs/decisions-log.md)
```
