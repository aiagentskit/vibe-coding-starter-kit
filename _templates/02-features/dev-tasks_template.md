# Template: Development Tasks

> **Purpose:** Break feature into atomic, LLM-executable tasks  
> **When to create:** After tech-design is approved  
> **Update frequency:** Update status as tasks progress  
> **Output location:** `02-features/{{feature-name}}/dev-tasks.md`

---

## LLM Instructions

When filling this template:
1. Each task should be completable in 30-60 minutes
2. Tasks must be specific enough for an AI to implement without ambiguity
3. Include context files that should be shared with AI for each task
4. Acceptance criteria should be verifiable - can you check if it's done?
5. Order tasks by dependency - foundation first, integration later, polish last
6. Use status emojis consistently: ⬜ Not Started, 🔄 In Progress, ✅ Complete, ⏸️ Blocked

---

## Template

```markdown
# Dev Tasks: {{FEATURE_NAME}}

> **Feature:** {{FEATURE_NAME}}  
> **Status:** Not Started | In Progress | Complete  
> **Total Tasks:** {{COUNT}}  
> **Completed:** 0

---

## 📋 Overview

Atomic, LLM-executable tasks for implementing {{FEATURE_NAME}}.

**How to use:**
1. Pick a task
2. Share listed context files with AI
3. Implement and test
4. Update status and log in implementation-log.md

---

## 🏗️ Foundation Tasks

### TASK-001: {{TASK_TITLE}}

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** {{N}} minutes  
**Dependencies:** None

**Context Files to Include:**
- `docs/_templates/02-features/tech-design_template.md` → relevant section
- `docs/00-context/system-state.md`

**Task Description:**

{{DETAILED_DESCRIPTION_OF_WHAT_TO_BUILD}}

**Files to Create/Modify:**
- `{{FILE_PATH_1}}`
- `{{FILE_PATH_2}}`

**Requirements:**
- {{REQUIREMENT_1}}
- {{REQUIREMENT_2}}

**Acceptance Criteria:**
- [ ] {{TESTABLE_CRITERION_1}}
- [ ] {{TESTABLE_CRITERION_2}}
- [ ] {{TESTABLE_CRITERION_3}}

---

### TASK-002: {{TASK_TITLE}}

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** {{N}} minutes  
**Dependencies:** TASK-001

**Context Files to Include:**
- `{{CONTEXT_FILE}}`

**Task Description:**

{{DETAILED_DESCRIPTION}}

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}

---

## 🔧 Integration Tasks

### TASK-003: {{TASK_TITLE}}

**Status:** ⬜ Not Started  
**Priority:** P0  
**Estimated Time:** {{N}} minutes  
**Dependencies:** TASK-001, TASK-002

**Context Files to Include:**
- `{{CONTEXT_FILE}}`

**Task Description:**

{{DETAILED_DESCRIPTION}}

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}
- [ ] {{CRITERION_2}}

---

## 🎨 Polish Tasks

### TASK-004: {{TASK_TITLE}}

**Status:** ⬜ Not Started  
**Priority:** P2  
**Estimated Time:** {{N}} minutes  
**Dependencies:** TASK-003

**Task Description:**

{{DETAILED_DESCRIPTION}}

**Acceptance Criteria:**
- [ ] {{CRITERION_1}}

---

## 📊 Progress Tracker

| Task | Title | Status | Assigned | Completed |
|------|-------|--------|----------|-----------|
| TASK-001 | {{TITLE}} | ⬜ | - | - |
| TASK-002 | {{TITLE}} | ⬜ | - | - |
| TASK-003 | {{TITLE}} | ⬜ | - | - |
| TASK-004 | {{TITLE}} | ⬜ | - | - |

**Legend:** ⬜ Not Started | 🔄 In Progress | ✅ Complete | ⏸️ Blocked

---

## 📎 Related Documents

- [Feature Spec](./feature-spec.md)
- [Technical Design](./tech-design.md)
- [Test Plan](./test-plan.md)
- [Implementation Log](../../03-logs/implementation-log.md)
```
