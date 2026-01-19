# Template: Product Requirements Document (PRD)

> **Purpose:** Single source of truth for WHAT the product must do  
> **When to create:** After vision.md, before detailed feature work  
> **Update frequency:** As scope changes  
> **Output location:** `01-product/prd.md`

---

## LLM Instructions

When filling this template:
1. User stories must follow format: "As a [user], I want [action] so that [benefit]"
2. Every user story needs acceptance criteria - no ambiguity
3. Prioritize ruthlessly: P0 = must have for MVP, P1 = should have, P2 = nice to have
4. Out of scope is as important as in scope - be explicit
5. Non-functional requirements often get forgotten - ensure performance, accessibility, security are covered

---

## Template

```markdown
# Product Requirements Document (PRD)

> **Product:** {{PRODUCT_NAME}}  
> **Version:** {{VERSION}} (MVP)  
> **Last Updated:** {{DATE}}  
> **Status:** Draft | In Review | Approved

---

## 📋 Overview

*Brief description of the product and what this PRD covers.*

{{PRODUCT_OVERVIEW}}

**Reference:** [Product Vision](../00-context/vision.md)

---

## 🎯 Goals for v{{VERSION}}

1. {{GOAL_1}}
2. {{GOAL_2}}
3. {{GOAL_3}}

---

## 👤 User Stories

### Epic 1: {{EPIC_NAME}}

#### US-101: {{STORY_TITLE}}
> As a **{{USER_TYPE}}**, I want to **{{ACTION}}** so that **{{BENEFIT}}**.

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}
- [ ] {{CRITERION_3}}

**Priority:** P0 | P1 | P2  
**Story Points:** {{POINTS}}

---

#### US-102: {{STORY_TITLE}}
> As a **{{USER_TYPE}}**, I want to **{{ACTION}}** so that **{{BENEFIT}}**.

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}

**Priority:** P0 | P1 | P2  
**Story Points:** {{POINTS}}

---

### Epic 2: {{EPIC_NAME}}

#### US-201: {{STORY_TITLE}}
> As a **{{USER_TYPE}}**, I want to **{{ACTION}}** so that **{{BENEFIT}}**.

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}

**Priority:** P0 | P1 | P2  
**Story Points:** {{POINTS}}

---

## 🚫 Out of Scope for v{{VERSION}}

| Feature | Reason |
|---------|--------|
| {{FEATURE_1}} | {{REASON}} |
| {{FEATURE_2}} | {{REASON}} |
| {{FEATURE_3}} | {{REASON}} |

---

## 📊 Default Data/Settings (if applicable)

*Any seed data, default configurations, or initial content.*

| Name | Value | Notes |
|------|-------|-------|
| {{SETTING}} | {{VALUE}} | {{NOTES}} |

---

## 📐 Non-Functional Requirements

### Performance

| Metric | Requirement |
|--------|-------------|
| {{METRIC}} | {{REQUIREMENT}} |

### Accessibility

| Requirement | Notes |
|-------------|-------|
| WCAG 2.1 AA Compliant | {{SPECIFICS}} |

### Browser Support

| Browser | Minimum Version |
|---------|----------------|
| {{BROWSER}} | {{VERSION}}+ |

### Security

| Requirement | Implementation |
|-------------|----------------|
| {{REQUIREMENT}} | {{HOW}} |

---

## 📅 Release Plan

| Phase | Features | Duration |
|-------|----------|----------|
| Sprint 1 | {{USER_STORIES}} | {{DURATION}} |
| Sprint 2 | {{USER_STORIES}} | {{DURATION}} |

### Post-MVP Roadmap

| Version | Planned Features |
|---------|------------------|
| v{{NEXT}} | {{FEATURES}} |

---

## 📎 Related Documents

- [Vision](../00-context/vision.md)
- [Assumptions & Risks](../00-context/assumptions.md)
- [Feature Designs](../02-features/)
```
