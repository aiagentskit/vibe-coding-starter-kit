# Template: Bug Log

> **Purpose:** Track bugs, their fixes, and root causes  
> **When to create:** At project start  
> **Update frequency:** When bugs are found or fixed  
> **Output location:** `03-logs/bug-log.md`

---

## LLM Instructions

When filling this template:
1. Include clear reproduction steps - if it can't be reproduced, it can't be fixed
2. Document investigation steps in chronological order
3. Root cause is essential - without it, similar bugs will recur
4. Include prevention measures - what test or change prevents recurrence?
5. Link to related implementation changes
6. Use consistent severity levels: Critical/High/Medium/Low

---

## Template

```markdown
# Bug Log

> **Project:** {{PROJECT_NAME}}  
> **Purpose:** Track bugs, fixes, and root causes  
> **Update Frequency:** When bugs are found or fixed

---

## How to Use This Log

When a bug is found:
1. Create an entry with BUG-XXX ID
2. Document reproduction steps
3. Track investigation notes
4. Record root cause and fix
5. Add prevention measures

---

## Summary

| Status | Count |
|--------|-------|
| 🔴 Open | {{N}} |
| 🟡 In Progress | {{N}} |
| ✅ Fixed | {{N}} |

---

## Open Bugs

### BUG-001: {{SHORT_DESCRIPTION}}

**Status:** 🔴 Open  
**Severity:** Critical | High | Medium | Low  
**Reported:** {{DATE}}  
**Reporter:** {{NAME}}

#### Description

{{WHAT_IS_HAPPENING}}

#### Reproduction Steps

1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}

**Expected:** {{EXPECTED_BEHAVIOR}}  
**Actual:** {{ACTUAL_BEHAVIOR}}

#### Environment

- Browser: {{BROWSER_VERSION}}
- OS: {{OS}}
- Other: {{RELEVANT_INFO}}

#### Investigation Notes

- **{{DATE}}:** {{INVESTIGATION_STEP}}
- **{{DATE}}:** {{FINDING}}

#### Related

- Feature: {{FEATURE_NAME}}
- Files: `{{FILE_PATH}}`

---

## In Progress

### BUG-002: {{SHORT_DESCRIPTION}}

**Status:** 🟡 In Progress  
**Severity:** {{SEVERITY}}  
**Assigned:** {{DEVELOPER}}  
**Reported:** {{DATE}}

#### Description
{{DESCRIPTION}}

#### Reproduction Steps
1. {{STEP}}

#### Investigation Notes
- {{NOTES}}

#### Possible Solutions
1. {{SOLUTION_1}}
2. {{SOLUTION_2}}

---

## Fixed Bugs

### BUG-003: {{SHORT_DESCRIPTION}}

**Status:** ✅ Fixed  
**Severity:** {{SEVERITY}}  
**Reported:** {{DATE}}  
**Fixed:** {{DATE}}  
**Fixed By:** {{DEVELOPER}}

#### Description
{{DESCRIPTION}}

#### Root Cause
{{ROOT_CAUSE}}

#### Fix Applied
{{FIX_DESCRIPTION}}

```{{LANGUAGE}}
// Code change (optional)
{{CODE}}
```

#### Prevention
- {{TEST_ADDED}}
- {{PROCESS_CHANGE}}

#### Commits
- `{{COMMIT_HASH}}` - {{MESSAGE}}

---

## Bug Entry Template

*Copy this for new bugs:*

```
### BUG-XXX: [Short description]

**Status:** 🔴 Open
**Severity:** Critical | High | Medium | Low
**Reported:** YYYY-MM-DD
**Reporter:** [Name]

#### Description
[What's happening vs what should happen]

#### Reproduction Steps
1. [Step 1]
2. [Step 2]

**Expected:** [Expected behavior]
**Actual:** [Actual behavior]

#### Investigation Notes
- [Notes added during investigation]

#### Root Cause
[Once identified]

#### Fix Applied
[Description of fix]

#### Prevention
- [Test or change to prevent recurrence]
```

---

## Regression Prevention Checklist

After fixing a bug:
- [ ] Root cause documented
- [ ] Test added to prevent regression
- [ ] Similar patterns checked across codebase
- [ ] implementation-log.md updated

---

## 📎 Related Documents

- [Implementation Log](./implementation-log.md)
- [Test Plans](../02-features/)
- [Validation Log](./validation-log.md)
```
