# Template: Implementation Log

> **Purpose:** Track what changed in code, when, and why  
> **When to create:** At project start  
> **Update frequency:** After each development session  
> **Output location:** `03-logs/implementation-log.md`

---

## LLM Instructions

When filling this template:
1. Add entries after EVERY coding session, no matter how small
2. Include task references so changes can be traced to requirements
3. Document deviations from plan - these inform future decisions
4. List files changed - helps AI understand codebase evolution
5. Include "notes for future sessions" - context for next AI conversation

---

## Template

```markdown
# Implementation Log

> **Project:** {{PROJECT_NAME}}  
> **Purpose:** Track what changed in code and why  
> **Update Frequency:** After each dev session

---

## How to Use This Log

After completing a task or ending a session, add an entry with:
- Date and time
- Task reference (from dev-tasks.md)
- What was implemented
- Key decisions made
- Files changed
- Notes for future sessions

---

## Log Entries

### {{DATE}} | Session {{N}}: {{TITLE}}

**Task:** {{TASK_ID}}  
**Duration:** {{TIME}}  
**Developer:** {{NAME}}

#### What Was Implemented

1. {{CHANGE_1}}
2. {{CHANGE_2}}
3. {{CHANGE_3}}

#### Key Decisions

- **{{DECISION}}**: {{RATIONALE}}

#### Deviations from Plan

- {{DEVIATION_AND_WHY}}

#### Files Changed

- `{{FILE_PATH}}` (created/modified/deleted)
- `{{FILE_PATH}}` (created/modified/deleted)

#### Notes for Future Sessions

- {{CONTEXT_FOR_NEXT_DEVELOPER}}

---

### {{DATE}} | Session {{N}}: {{TITLE}}

**Task:** {{TASK_ID}}  
**Duration:** {{TIME}}  
**Developer:** {{NAME}}

#### What Was Implemented

1. {{CHANGE_1}}

#### Files Changed

- `{{FILE_PATH}}`

---

## Entry Template

*Copy this for new entries:*

```
### YYYY-MM-DD | Session N: [Title]

**Task:** [Task ID]  
**Duration:** [Time]  
**Developer:** [Name]

#### What Was Implemented
- [Change 1]

#### Key Decisions
- **[Decision]**: [Rationale]

#### Deviations from Plan
- [None or describe]

#### Files Changed
- `path/to/file.js`

#### Notes for Future Sessions
- [Important context]
```

---

## 📎 Related Documents

- [Dev Tasks](../02-features/)
- [Decisions Log](./decisions-log.md)
- [Bug Log](./bug-log.md)
```
