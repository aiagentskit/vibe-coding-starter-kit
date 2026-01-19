# Development Workflow

> **Purpose:** Define workflows for all development scenarios  
> **Version:** 2.0

---

## Overview

This document provides workflows for different development scenarios. Choose the workflow that matches what you're doing today.

## 📋 Workflow Index

| I want to... | Use this workflow |
|--------------|-------------------|
| Build a new feature | [Standard Dev Loop](#standard-dev-loop) |
| Fix a bug | [Bug Fix Workflow](#bug-fix-workflow) |
| Refactor code | [Refactoring Workflow](#refactoring-workflow) |
| Do a quick enhancement | [Quick Fix Workflow](#quick-fix-workflow) |
| Research/spike | [Research Workflow](#research-workflow) |
| Review and merge | [Code Review Workflow](#code-review-workflow) |

---

## Standard Dev Loop

*For building new features or substantial changes*

```
┌───────────────────────────────────────────────────────────────────┐
│                    THE VIBE CODING LOOP                           │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   🌅 START SESSION                                                │
│      │                                                            │
│      ├──→ 1. Review logs (5 min)                                  │
│      │                                                            │
│      ├──→ 2. Load context into AI                                 │
│      │                                                            │
│      ├──→ 3. Pick task from dev-tasks.md                          │
│      │                                                            │
│      ├──→ 4. Execute with AI                                      │
│      │       │                                                    │
│      │       ├── Implement                                        │
│      │       ├── Test                                             │
│      │       └── Refine                                           │
│      │                                                            │
│      ├──→ 5. Validate against acceptance criteria                 │
│      │                                                            │
│      ├──→ 6. Update logs                                          │
│      │                                                            │
│      └──→ 7. Commit & push                                        │
│                                                                   │
│   🌙 END SESSION                                                  │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

### Step 1: Start of Session (5 minutes)

**Goal:** Catch up on project state

```
□ Read latest 3 entries in implementation-log.md
□ Check bug-log.md for critical issues
□ Review today's task priority in dev-tasks.md
□ Note any blockers or dependencies
```

### Step 2: Load Context into AI

**Minimum Context:**

```markdown
I'm working on {{PROJECT_NAME}}.

## Vision
{{vision.md → core purpose and boundaries}}

## System State
{{system-state.md → current state summary}}

## Today's Task
{{dev-tasks.md → specific task}}
```

**Additional Context (when relevant):**

```markdown
## Technical Design
{{tech-design.md → relevant sections}}

## Recent Changes
{{implementation-log.md → last 1-2 entries}}

## Known Issues
{{bug-log.md → relevant bugs}}
```

### Step 3: Pick a Task

**Task Selection Criteria:**

| Priority | Criteria |
|----------|----------|
| 1st | Blockers for other work |
| 2nd | Bugs affecting users |
| 3rd | P0 features not complete |
| 4th | P1 features not complete |
| 5th | Polish and optimization |

### Step 4: Execute with AI

```markdown
## Current Task
{{dev-tasks.md → task}}

## What Exists
{{CURRENT_RELEVANT_CODE}}

## Technical Constraints
{{tech-design.md → constraints}}

## Request
Please implement this task. Follow the patterns in tech-design.md.

After implementation, explain any decisions that deviated from the design.
```

### Step 5: Validate

```
□ Code runs without errors
□ Core functionality works
□ Edge cases handled
□ No console warnings
□ Acceptance criteria met
```

### Step 6: Update Logs

```markdown
## implementation-log.md entry

### {{DATE}} | Session: {{TASK_TITLE}}

**Task:** {{TASK_ID}}
**Duration:** {{TIME_TAKEN}}

#### What Was Implemented
- {{CHANGES}}

#### Files Changed
- `path/to/file.js`
```

### Step 7: Commit & Push

```
git add .
git commit -m "[type]: [description]

Task: TASK-XXX"
git push
```

---

## Bug Fix Workflow

*For investigating and fixing bugs*

```
┌───────────────────────────────────────────────────────────────────┐
│                    BUG FIX WORKFLOW                               │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   🐛 BUG REPORTED                                                 │
│      │                                                            │
│      ├──→ 1. Reproduce & document                                 │
│      │                                                            │
│      ├──→ 2. Investigate root cause                               │
│      │                                                            │
│      ├──→ 3. Implement fix                                        │
│      │                                                            │
│      ├──→ 4. Test fix & regressions                               │
│      │                                                            │
│      ├──→ 5. Add prevention (test)                                │
│      │                                                            │
│      └──→ 6. Document & commit                                    │
│                                                                   │
│   ✅ BUG CLOSED                                                   │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

### Step 1: Reproduce & Document

**Create bug-log.md entry:**

```markdown
### BUG-XXX: {{SHORT_DESCRIPTION}}

**Status:** 🔴 Open
**Severity:** Critical | High | Medium | Low
**Reported:** {{DATE}}

#### Reproduction Steps
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}

**Expected:** {{EXPECTED}}
**Actual:** {{ACTUAL}}

#### Error Messages
{{ERRORS}}
```

### Step 2: Investigate with AI

```markdown
I need help debugging this issue.

## Bug Description
{{bug-log.md → bug entry}}

## Relevant Code
{{CODE_FILES}}

## What I've Observed
{{OBSERVATIONS}}

Please help me identify the root cause.
```

### Step 3: Implement Fix

```markdown
The root cause is {{ROOT_CAUSE}}.

Please implement a fix that:
1. Resolves the issue
2. Doesn't break existing functionality
3. Is minimal and focused

Show me the fix and explain the change.
```

### Step 4: Test Fix & Regressions

```
□ Original reproduction steps no longer reproduce bug
□ Related functionality still works
□ No new console errors
□ Any modified tests pass
```

### Step 5: Add Prevention

```markdown
Help me write a test that will prevent this bug from recurring.

## The Bug
{{bug-log.md → bug entry}}

## The Fix
{{CODE_CHANGES}}

Please create a test case that:
1. Would have caught this bug
2. Verifies the fix works
3. Prevents regression
```

### Step 6: Document & Commit

**Update bug-log.md:**

```markdown
**Status:** ✅ Fixed
**Fixed:** {{DATE}}

#### Root Cause
{{ROOT_CAUSE}}

#### Fix Applied
{{FIX_DESCRIPTION}}

#### Prevention
- Added test: {{TEST_FILE}}
```

**Commit:**

```
git commit -m "fix: {{DESCRIPTION}} (BUG-XXX)

Root cause: {{ROOT_CAUSE}}
Prevention: {{TEST_ADDED}}"
```

---

## Refactoring Workflow

*For improving code quality without changing behavior*

```
┌───────────────────────────────────────────────────────────────────┐
│                    REFACTORING WORKFLOW                           │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   📝 DOCUMENT INTENT                                              │
│      │                                                            │
│      ├──→ 1. Create ADR (why refactor?)                           │
│      │                                                            │
│      ├──→ 2. Run all tests (baseline)                             │
│      │                                                            │
│      ├──→ 3. Plan small, safe steps                               │
│      │                                                            │
│      ├──→ 4. Execute one step                                     │
│      │       │                                                    │
│      │       ├── Refactor                                         │
│      │       ├── Test                                             │
│      │       ├── Commit                                           │
│      │       └── Repeat                                           │
│      │                                                            │
│      └──→ 5. Update documentation                                 │
│                                                                   │
│   ✨ REFACTOR COMPLETE                                            │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

### Step 1: Create ADR

**In decisions-log.md:**

```markdown
### ADR-XXX: Refactor {{WHAT}}

**Status:** In Progress
**Date:** {{DATE}}

#### Context
{{WHY_REFACTORING}}

#### Current State
{{CURRENT_PROBLEMS}}

#### Target State
{{DESIRED_OUTCOME}}

#### Approach
{{HIGH_LEVEL_PLAN}}
```

### Step 2: Establish Baseline

```bash
# Run all tests
npm test

# Note the results
# Tests: XX passed, 0 failed
```

### Step 3: Plan Safe Steps

Each step should:
- Be completable in 15-30 min
- Not change external behavior
- Be independently testable
- Be revertible

Example breakdown:
```
□ Step 1: Extract function X
□ Step 2: Rename variables for clarity
□ Step 3: Move to new file
□ Step 4: Update imports
□ Step 5: Remove dead code
```

### Step 4: Execute One Step at a Time

```markdown
I'm refactoring {{COMPONENT}}.

## Current Code
{{CODE}}

## Goal for This Step
{{SPECIFIC_REFACTORING_GOAL}}

## Constraint
The external behavior must not change.

Please refactor and explain what changed.
```

**After each step:**
```bash
npm test  # Must still pass
git commit -m "refactor: {{SPECIFIC_CHANGE}}"
```

### Step 5: Update Documentation

```
□ Update system-state.md if architecture changed
□ Update tech-design.md if patterns changed
□ Update ADR with outcome
□ Log insights in insights.md
```

---

## Quick Fix Workflow

*For small, isolated changes (< 30 minutes)*

```
┌───────────────────────────────────────────────────────────────────┐
│                    QUICK FIX WORKFLOW                             │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   ⚡ QUICK CHANGE                                                 │
│      │                                                            │
│      ├──→ 1. Identify change (< 5 files)                          │
│      │                                                            │
│      ├──→ 2. Implement with AI                                    │
│      │                                                            │
│      ├──→ 3. Quick test                                           │
│      │                                                            │
│      └──→ 4. Commit                                               │
│                                                                   │
│   ✅ DONE                                                         │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

**Use when:**
- Typo fixes
- Small styling changes
- Config updates
- Minor text changes
- Adding a missing property

**Prompt pattern:**

```markdown
Quick change needed:

## What
{{CHANGE_DESCRIPTION}}

## File(s)
{{FILE_PATHS}}

## Current
{{CURRENT_CODE_SNIPPET}}

## Desired
{{WHAT_IT_SHOULD_BE}}
```

**Commit:**
```
git commit -m "fix: {{BRIEF_DESCRIPTION}}"
```

---

## Research Workflow

*For spikes, investigations, and exploratory work*

```
┌───────────────────────────────────────────────────────────────────┐
│                    RESEARCH WORKFLOW                              │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   🔍 QUESTION                                                     │
│      │                                                            │
│      ├──→ 1. Define the question                                  │
│      │                                                            │
│      ├──→ 2. Time-box (max 2 hours)                               │
│      │                                                            │
│      ├──→ 3. Research & prototype                                 │
│      │                                                            │
│      ├──→ 4. Document findings                                    │
│      │                                                            │
│      └──→ 5. Create follow-up tasks                               │
│                                                                   │
│   💡 ANSWER                                                       │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

### Step 1: Define the Question

```markdown
## Research Goal
{{WHAT_WE_WANT_TO_LEARN}}

## Success Criteria
We'll know we're done when:
- {{CRITERIA_1}}
- {{CRITERIA_2}}

## Time Box
{{HOURS}} hours maximum
```

### Step 2-3: Research with AI

```markdown
I'm researching {{TOPIC}}.

## Question
{{SPECIFIC_QUESTION}}

## Context
{{WHY_THIS_MATTERS_FOR_PROJECT}}

## What I Know
{{EXISTING_KNOWLEDGE}}

Please help me understand:
1. {{SUB_QUESTION_1}}
2. {{SUB_QUESTION_2}}
```

### Step 4: Document in insights.md

```markdown
### Research: {{TOPIC}} ({{DATE}})

**Question:** {{QUESTION}}

**Key Findings:**
1. {{FINDING_1}}
2. {{FINDING_2}}

**Recommendation:** {{RECOMMENDATION}}

**Code Prototype:** {{LINK_OR_SNIPPET}}

**Follow-up:** {{NEXT_STEPS}}
```

### Step 5: Create Follow-up Tasks

If action needed, add to dev-tasks.md:
```markdown
### TASK-XXX: {{IMPLEMENT_RESEARCH_FINDINGS}}

Based on research: {{LINK_TO_INSIGHTS}}
```

---

## Code Review Workflow

*For reviewing AI-generated or team code*

```
┌───────────────────────────────────────────────────────────────────┐
│                    CODE REVIEW WORKFLOW                           │
├───────────────────────────────────────────────────────────────────┤
│                                                                   │
│   📝 CODE TO REVIEW                                               │
│      │                                                            │
│      ├──→ 1. Understand intent                                    │
│      │                                                            │
│      ├──→ 2. AI-assisted review                                   │
│      │                                                            │
│      ├──→ 3. Manual verification                                  │
│      │                                                            │
│      ├──→ 4. Provide feedback                                     │
│      │                                                            │
│      └──→ 5. Approve or request changes                           │
│                                                                   │
│   ✅ MERGED                                                       │
│                                                                   │
└───────────────────────────────────────────────────────────────────┘
```

### AI-Assisted Review Prompt

```markdown
Please review this code:

## Purpose
{{WHAT_THIS_CODE_DOES}}

## Code
{{CODE}}

## Our Patterns
{{tech-design.md → relevant patterns}}

Review for:
1. **Correctness** - Does it work?
2. **Patterns** - Does it follow our conventions?
3. **Edge cases** - What could break?
4. **Security** - Any vulnerabilities?
5. **Performance** - Any issues?
6. **Accessibility** - Any problems?

List issues by severity (High/Medium/Low).
```

---

## Session Patterns

### Short Session (30 min - 1 hour)

```
□ Quick log review (2 min)
□ Load context + pick 1 task (3 min)
□ Execute task (20-45 min)
□ Validate + log + commit (5-10 min)
```

### Full Session (2-4 hours)

```
□ Thorough log review (5 min)
□ Plan session: pick 2-4 related tasks (10 min)
□ Execute in sequence, committing after each
□ Update all relevant docs (15 min)
□ Update system-state.md if significant changes
```

---

## Multi-Developer Coordination

### Before Starting

```bash
git pull origin main
```

### Claiming a Task

Update dev-tasks.md:

```markdown
### TASK-005: Create DateInput Component

**Status:** 🔄 In Progress
**Assigned:** {{YOUR_NAME}}
**Started:** {{DATE}}
```

### End of Session

```
✅ Completed: TASK-005 (DateInput component)
🔄 In progress: TASK-006 (NotesInput)
⚠️ Blocked on: Need design decision for date format
```

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| AI gave broken code | Provide error message, ask for specific fix |
| Lost track of what's built | Read system-state.md, implementation-log.md |
| Tasks too vague | Break down, add acceptance criteria |
| Previous work broken | Check git log, implementation-log, bug-log |

---

## Quick Reference Card

```
┌─────────────────────────────────────────────┐
│           VIBE CODING CHEAT SHEET           │
├─────────────────────────────────────────────┤
│                                             │
│  📖 CONTEXT FILES                           │
│     • vision.md → WHY we're building        │
│     • system-state.md → WHAT exists         │
│     • tech-design.md → HOW it works         │
│     • dev-tasks.md → WHAT to do next        │
│                                             │
│  ✍️ UPDATE AFTER WORK                       │
│     • implementation-log.md                 │
│     • dev-tasks.md (status)                 │
│     • decisions-log.md (if major decision)  │
│                                             │
│  🔄 WORKFLOWS                               │
│     • New feature → Standard Dev Loop       │
│     • Bug fix → Bug Fix Workflow            │
│     • Cleanup → Refactoring Workflow        │
│     • Small change → Quick Fix Workflow     │
│                                             │
└─────────────────────────────────────────────┘
```

---

## 📎 Related Documents

- [Definition of Done](./definition-of-done.md)
- [LLM Prompts](./llm-prompts.md)
- [Implementation Log](../03-logs/implementation-log.md)
