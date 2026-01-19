# Template: Feature Specification

> **Purpose:** Define WHAT a feature does and its acceptance criteria  
> **When to create:** When planning a new feature  
> **Update frequency:** Until feature is approved, then rarely  
> **Output location:** `02-features/{{feature-name}}/feature-spec.md`

---

## LLM Instructions

When filling this template:
1. Purpose should be 2-3 sentences max - if you can't explain it briefly, it's too complex
2. User journey should be a simple flow, not a detailed process map
3. Acceptance criteria must be testable - "works well" is not testable
4. Include edge cases and error states - these are often forgotten
5. Be explicit about what's OUT of scope to prevent scope creep

---

## Template

```markdown
# Feature Spec: {{FEATURE_NAME}}

> **Feature:** {{FEATURE_NAME}}  
> **Status:** Draft | In Review | Approved  
> **Owner:** {{OWNER}}  
> **Related PRD:** {{LINK_TO_USER_STORY}}

---

## 🎯 Purpose

*Why does this feature exist? (2-3 sentences)*

{{PURPOSE}}

---

## 👤 User Intent

**Who:** {{USER_TYPE}}  
**What:** {{WHAT_THEY_WANT_TO_DO}}  
**When:** {{TRIGGER_SITUATION}}  
**Why:** {{UNDERLYING_MOTIVATION}}

### User Journey

```
{{TRIGGER_STATE}}
       ↓
{{STEP_1}}
       ↓
{{STEP_2}}
       ↓
{{STEP_3}}
       ↓
{{SUCCESS_STATE}}
```

---

## ✅ Acceptance Criteria

### Core Functionality

| ID | Criterion | Priority |
|----|-----------|----------|
| AC-01 | {{CRITERION}} | P0 |
| AC-02 | {{CRITERION}} | P0 |
| AC-03 | {{CRITERION}} | P1 |

### Edge Cases

| ID | Scenario | Expected Behavior |
|----|----------|-------------------|
| EC-01 | {{EDGE_CASE}} | {{EXPECTED}} |
| EC-02 | {{EDGE_CASE}} | {{EXPECTED}} |

---

## 🎨 UI/UX Requirements

### Layout

```
┌─────────────────────────────────────┐
│        {{HEADER}}                   │
├─────────────────────────────────────┤
│                                     │
│  {{MAIN_CONTENT_AREA}}              │
│                                     │
│  {{ACTION_AREA}}                    │
│                                     │
└─────────────────────────────────────┘
```

### Interaction Details

| Element | Behavior |
|---------|----------|
| {{ELEMENT}} | {{BEHAVIOR}} |

---

## 📏 Success Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| {{METRIC}} | {{TARGET}} | {{HOW}} |

---

## 🚫 Out of Scope

- {{NOT_INCLUDED_1}}
- {{NOT_INCLUDED_2}}

---

## 🔗 Dependencies

| Dependency | Type | Status |
|------------|------|--------|
| {{DEPENDENCY}} | Technical/Feature | ✅/🚧/📋 |

---

## 📎 Related Documents

- [Technical Design](./tech-design.md)
- [Dev Tasks](./dev-tasks.md)
- [Test Plan](./test-plan.md)
```
