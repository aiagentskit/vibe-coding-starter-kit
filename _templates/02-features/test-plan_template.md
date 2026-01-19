# Template: Test Plan

> **Purpose:** Define how a feature will be tested  
> **When to create:** Alongside or after feature-spec  
> **Update frequency:** As tests are executed and features change  
> **Output location:** `02-features/{{feature-name}}/test-plan.md`

---

## LLM Instructions

When filling this template:
1. Focus on WHAT to test, not just HOW to write tests
2. Include both automated tests (unit, integration) and manual testing checklists
3. Edge cases should map to acceptance criteria edge cases
4. Accessibility testing is required for all UI features
5. Include cross-browser testing for web features
6. Keep manual checklists simple - they should be executable by anyone

---

## Template

```markdown
# Test Plan: {{FEATURE_NAME}}

> **Feature:** {{FEATURE_NAME}}  
> **Status:** Draft | Active | Complete  
> **Last Updated:** {{DATE}}  
> **Owner:** {{OWNER}}

---

## 📋 Overview

Testing strategy for {{FEATURE_NAME}}.

**Testing Priorities:**
1. {{PRIORITY_1}} (e.g., data integrity)
2. {{PRIORITY_2}} (e.g., user experience)
3. {{PRIORITY_3}} (e.g., accessibility)

---

## 🎯 Test Coverage Goals

| Test Type | Target | Status |
|-----------|--------|--------|
| Unit Tests | {{PERCENT}}% | ⬜ Pending |
| Integration Tests | Core flows | ⬜ Pending |
| Accessibility | WCAG 2.1 AA | ⬜ Pending |
| Cross-browser | Major browsers | ⬜ Pending |

---

## 🧪 Unit Tests

### {{COMPONENT_NAME}}

| Test ID | Description | Expected Result |
|---------|-------------|-----------------|
| {{PREFIX}}-01 | {{WHAT_TO_TEST}} | {{EXPECTED}} |
| {{PREFIX}}-02 | {{WHAT_TO_TEST}} | {{EXPECTED}} |
| {{PREFIX}}-03 | {{WHAT_TO_TEST}} | {{EXPECTED}} |

```javascript
// Example test structure
describe('{{COMPONENT_NAME}}', () => {
  it('{{DESCRIPTION}}', () => {
    // Arrange
    // Act
    // Assert
  });
});
```

---

## 🔗 Integration Tests

### {{FLOW_NAME}}

| Test ID | Description | Steps | Expected |
|---------|-------------|-------|----------|
| INT-01 | {{DESCRIPTION}} | {{STEPS}} | {{EXPECTED}} |
| INT-02 | {{DESCRIPTION}} | {{STEPS}} | {{EXPECTED}} |

---

## 🖐️ Manual Testing Checklist

### Happy Path

| Step | Action | Expected | ✓ |
|------|--------|----------|---|
| 1 | {{ACTION}} | {{EXPECTED}} | ⬜ |
| 2 | {{ACTION}} | {{EXPECTED}} | ⬜ |
| 3 | {{ACTION}} | {{EXPECTED}} | ⬜ |

### Edge Cases

| Scenario | Steps | Expected | ✓ |
|----------|-------|----------|---|
| {{SCENARIO}} | {{STEPS}} | {{EXPECTED}} | ⬜ |
| {{SCENARIO}} | {{STEPS}} | {{EXPECTED}} | ⬜ |

### Error Handling

| Scenario | Steps | Expected | ✓ |
|----------|-------|----------|---|
| {{ERROR_CASE}} | {{STEPS}} | {{EXPECTED}} | ⬜ |

---

## ♿ Accessibility Testing

### Keyboard Navigation

| Test | Expected | ✓ |
|------|----------|---|
| Tab through all elements | Logical order | ⬜ |
| Enter/Space activates | Elements respond | ⬜ |
| Escape closes modals | Modal closes | ⬜ |
| Focus visible | Clear indicator | ⬜ |

### Screen Reader

| Test | Expected | ✓ |
|------|----------|---|
| All elements announced | Meaningful labels | ⬜ |
| Errors announced | User informed | ⬜ |
| State changes announced | Updates clear | ⬜ |

### Visual

| Test | Tool | Expected | ✓ |
|------|------|----------|---|
| Color contrast | axe DevTools | No violations | ⬜ |
| Zoom 200% | Browser | Layout intact | ⬜ |
| Reduced motion | OS setting | No animations | ⬜ |

---

## 📱 Cross-Browser Testing

| Browser | Version | Device | Status |
|---------|---------|--------|--------|
| Chrome | Latest | Desktop | ⬜ |
| Firefox | Latest | Desktop | ⬜ |
| Safari | Latest | Desktop | ⬜ |
| Chrome | Latest | Mobile | ⬜ |
| Safari | Latest | iOS | ⬜ |

---

## 📊 Performance Testing

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| {{METRIC}} | {{TARGET}} | - | ⬜ |

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
```
