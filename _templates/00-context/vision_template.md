# Template: Product Vision

> **Purpose:** Define WHY this product exists and WHO it's for  
> **When to create:** At project start, before any coding  
> **Update frequency:** Rarely (only on major pivots)  
> **Output location:** `00-context/vision.md`

---

## LLM Instructions

When filling this template:
1. Keep it concise (under 500 words for the Purpose section)
2. Be specific about target users - vague personas lead to vague products
3. Boundaries are critical - explicitly state what you're NOT building
4. North star metrics should be measurable
5. This document is referenced at the start of every AI session, so clarity is essential

---

## Template

```markdown
# Product Vision: {{PRODUCT_NAME}}

> **Last Updated:** {{DATE}}  
> **Status:** Draft | Active | Archived  
> **Owner:** {{OWNER_NAME}}

---

## 🎯 Purpose

*What problem does this product solve? Why does it need to exist? (2-3 paragraphs)*

### The Problem We're Solving

{{DESCRIPTION_OF_PROBLEM}}

### Our Solution

{{HIGH_LEVEL_SOLUTION}}

---

## 👤 Target Users

### Primary Persona: "{{PERSONA_NAME}}"

- **Age:** {{AGE_RANGE}}
- **Profile:** {{BRIEF_DESCRIPTION}}
- **Pain Point:** {{MAIN_FRUSTRATION}}
- **Goal:** {{WHAT_THEY_WANT_TO_ACHIEVE}}
- **Tech Comfort:** Low | Medium | High

### Secondary Persona: "{{PERSONA_NAME}}" (Optional)

- **Profile:** {{BRIEF_DESCRIPTION}}
- **Pain Point:** {{MAIN_FRUSTRATION}}
- **Goal:** {{WHAT_THEY_WANT_TO_ACHIEVE}}

---

## 🚫 Boundaries (What We're NOT Building)

| We Will NOT | Rationale |
|-------------|-----------|
| {{EXCLUDED_FEATURE_1}} | {{WHY_NOT}} |
| {{EXCLUDED_FEATURE_2}} | {{WHY_NOT}} |
| {{EXCLUDED_FEATURE_3}} | {{WHY_NOT}} |

---

## ⭐ North Star Metrics

| Metric | Target | Rationale |
|--------|--------|-----------|
| {{METRIC_1}} | {{TARGET}} | {{WHY_THIS_MATTERS}} |
| {{METRIC_2}} | {{TARGET}} | {{WHY_THIS_MATTERS}} |
| {{METRIC_3}} | {{TARGET}} | {{WHY_THIS_MATTERS}} |

---

## 🏛️ Core Principles

### 1. {{PRINCIPLE_NAME}}
{{BRIEF_DESCRIPTION_OF_PRINCIPLE}}

### 2. {{PRINCIPLE_NAME}}
{{BRIEF_DESCRIPTION_OF_PRINCIPLE}}

### 3. {{PRINCIPLE_NAME}}
{{BRIEF_DESCRIPTION_OF_PRINCIPLE}}

---

## 🔮 Future Considerations (Post-MVP)

*Explicitly OUT of scope for v1.0 but inform architectural decisions:*

- [ ] {{FUTURE_FEATURE_1}}
- [ ] {{FUTURE_FEATURE_2}}
- [ ] {{FUTURE_FEATURE_3}}

---

## 📏 Success Definition for v1.0

The MVP is successful when:

1. ✅ {{SUCCESS_CRITERION_1}}
2. ✅ {{SUCCESS_CRITERION_2}}
3. ✅ {{SUCCESS_CRITERION_3}}
4. ✅ {{SUCCESS_CRITERION_4}}

---

## 📎 Related Documents

- [Assumptions & Risks](./assumptions.md)
- [System State](./system-state.md)
- [Product Requirements](../01-product/prd.md)
```
