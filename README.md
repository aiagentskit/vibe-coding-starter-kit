# Vibe Coding Documentation System

> **A structured approach to AI-assisted software development**

This documentation system is designed to maximize the effectiveness of AI coding assistants (Claude, GPT-4, Gemini, Cursor, etc.) by providing them with the context they need to generate high-quality, consistent code.

## 🎯 Why This Structure?

AI coding assistants work best when they have:
1. **Clear context** about what you're building and why
2. **Atomic, well-defined tasks** that fit within context windows
3. **Memory** of past decisions and implementations
4. **Consistent patterns** and conventions to follow

This documentation system provides all of these.

## 📁 Directory Structure

```
/docs
├── _templates/          # BASE TEMPLATES (for LLMs to generate files)
├── 00-context/          # WHY and WHAT EXISTS RIGHT NOW
├── 01-product/          # WHAT the product must do
├── 02-features/         # HOW features are designed & built
├── 03-logs/             # MEMORY (what most teams miss!)
├── 04-process/          # HOW to work with this system
└── README.md            # You are here
```

---

## 🚀 Choose Your Scenario

### Scenario A: Building from Scratch

*Starting a brand new application with AI assistance*

**Step 1: Define Your Vision (30 min)**
```
□ Copy this template to your project root
□ Open 00-context/vision.md
□ Answer these questions:
  - What problem does this solve?
  - Who is the target user?
  - What are the boundaries (what we will NOT build)?
  - How do we measure success?
```

**Step 2: Write Your PRD (1-2 hours)**
```
□ Open 01-product/prd.md
□ List your user stories
□ Define acceptance criteria for each
□ Prioritize: P0 (must have), P1 (should have), P2 (nice to have)
```

**Step 3: Plan Your First Feature (1 hour)**
```
□ Create folder: 02-features/{{first-feature-name}}/
□ Create feature-spec.md (use template in 02-features/)
□ Create tech-design.md (architecture decisions)
□ Create dev-tasks.md (atomic, LLM-executable tasks)
□ Create test-plan.md (how you'll validate)
```

**Step 4: Start Building**
```
□ Initialize system-state.md with your tech stack choices
□ Follow the daily workflow in 04-process/dev-workflow.md
□ Start with TASK-001 from dev-tasks.md
```

---

### Scenario B: Adopting for Existing Project

*Adding this documentation system to a project that already exists*

**Step 1: Audit Current State (1-2 hours)**
```
□ Open 00-context/system-state.md
□ Document:
  - Current tech stack (frameworks, libraries, versions)
  - Existing file/folder structure
  - What features are built
  - Current deployment setup
  - Known issues and technical debt
```

**Step 2: Reverse-Engineer the Vision (30 min)**
```
□ Open 00-context/vision.md
□ Based on existing code, document:
  - What the product does
  - Who uses it
  - Core principles (inferred from code patterns)
  - Boundaries (what it doesn't do)
```

**Step 3: Backfill Key Decisions (1 hour)**
```
□ Open 03-logs/decisions-log.md
□ Document major past decisions:
  - Why was this framework chosen?
  - Why this database?
  - Why this architecture pattern?
  - Any decisions you wish were different?
```

**Step 4: Create Feature Documentation for Existing Features**
```
□ For each major existing feature:
  - Create 02-features/{{feature-name}}/
  - Write a basic feature-spec.md (what it does now)
  - Write tech-design.md (current architecture)
  - Skip dev-tasks.md (already built)
  - Create test-plan.md if tests don't exist
```

**Step 5: Plan Your Next Enhancement**
```
□ Create 02-features/{{new-feature-name}}/
□ Follow the new feature workflow below
```

---

### Scenario C: Adding a New Feature

*Planning and building a new feature in an existing project*

**Step 1: Create Feature Folder**
```
□ Create 02-features/{{feature-name}}/
□ Copy templates from 02-features/_templates/ (if you have them)
```

**Step 2: Write Feature Spec (30-60 min)**
```
□ Open feature-spec.md
□ Define:
  - Purpose: Why this feature?
  - User Intent: What user is trying to do?
  - Acceptance Criteria: How do we know it's done?
  - Edge Cases: What could go wrong?
  - Out of Scope: What are we NOT building?
```

**Step 3: Write Technical Design (1-2 hours)**
```
□ Open tech-design.md
□ Define:
  - Component architecture
  - Data models
  - API changes (if any)
  - Dependencies on existing code
  - Performance considerations
```

**Step 4: Break Down into Tasks (30 min)**
```
□ Open dev-tasks.md
□ Create atomic tasks (30-60 min each)
□ Each task has:
  - Clear title
  - Context files to reference
  - Detailed description
  - Acceptance criteria
```

**Step 5: Build**
```
□ Follow 04-process/dev-workflow.md
□ Complete one task at a time
□ Log everything in 03-logs/
```

---

### Scenario D: Fixing a Bug

*Investigating and fixing an issue in the codebase*

**Step 1: Log the Bug**
```
□ Open 03-logs/bug-log.md
□ Create entry with:
  - Bug ID (BUG-XXX)
  - Description
  - Reproduction steps
  - Expected vs actual behavior
  - Severity (Critical/High/Medium/Low)
```

**Step 2: Investigate with AI**
```
□ Share with AI:
  - Bug description from bug-log.md
  - Relevant code files
  - Error messages
  - What you've already tried
□ Ask AI to help identify root cause
```

**Step 3: Fix and Test**
```
□ Implement the fix
□ Verify reproduction steps no longer reproduce bug
□ Test for regressions
□ Add a test to prevent regression
```

**Step 4: Document**
```
□ Update bug-log.md with:
  - Root cause
  - Fix applied
  - Prevention measures
□ Update implementation-log.md with changes
□ Commit with message: "fix: [description] (BUG-XXX)"
```

---

### Scenario E: Refactoring Code

*Improving code quality without changing functionality*

**Step 1: Document Intent**
```
□ Open 03-logs/decisions-log.md
□ Create ADR entry:
  - What are you refactoring?
  - Why? (tech debt, performance, readability)
  - What's the target state?
```

**Step 2: Create Refactoring Tasks**
```
□ Create 02-features/refactor-{{name}}/dev-tasks.md
□ Break into small, safe refactoring steps
□ Each task should:
  - Not change external behavior
  - Be testable independently
  - Be revertible if needed
```

**Step 3: Execute Safely**
```
□ Run tests before starting
□ Refactor one task at a time
□ Run tests after each task
□ Commit after each passing test
```

**Step 4: Document Outcomes**
```
□ Update system-state.md if architecture changed
□ Update tech-design.md if patterns changed
□ Log learnings in 03-logs/insights.md
```

---

### Scenario F: Onboarding a New Developer

*Getting a new team member up to speed*

**Onboarding Checklist for New Developer:**

```
□ Day 1: Context
  - Read 00-context/vision.md (15 min)
  - Read 00-context/system-state.md (30 min)
  - Run the application locally
  - Explore the codebase structure

□ Day 1-2: History
  - Read 03-logs/decisions-log.md (understand WHY)
  - Read recent entries in implementation-log.md
  - Review bug-log.md for known issues

□ Day 2: Process
  - Read 04-process/dev-workflow.md
  - Read 04-process/definition-of-done.md
  - Review 04-process/llm-prompts.md

□ Day 2-3: First Task
  - Pick a small task from dev-tasks.md (P2 or good-first-issue)
  - Follow the full workflow
  - Ask questions, they become docs!
```

---

### Scenario G: Maintenance Mode

*Ongoing upkeep of a stable product*

**Weekly Maintenance Checklist:**
```
□ Review bug-log.md for any new reported issues
□ Check assumptions.md - any assumptions validated/invalidated?
□ Update system-state.md if dependencies updated
□ Review insights.md - any learnings to action?
```

**Monthly Maintenance Checklist:**
```
□ Dependency updates (security patches)
□ Performance review
□ User feedback review (validation-log.md)
□ Tech debt assessment
□ Documentation freshness check
```

---

## 📚 Directory Guide

### `00-context/` - WHY and WHAT EXISTS RIGHT NOW

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `vision.md` | Product purpose, boundaries, and north star | Rarely (major pivots only) |
| `assumptions.md` | Risks, unknowns, and assumptions | Weekly or when validated |
| `system-state.md` | Current tech stack and deployment status | After each major change |

**Start every LLM conversation by referencing `vision.md`**

### `01-product/` - WHAT the product must do

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `prd.md` | Single source of truth for requirements | As scope changes |

### `_templates/` - BASE TEMPLATES FOR LLM USE

All base templates are centralized here for easy reference by AI assistants:

```
_templates/
├── README.md                    # How to use templates
├── 00-context/
│   ├── vision_template.md
│   ├── assumptions_template.md
│   └── system-state_template.md
├── 01-product/
│   └── prd_template.md
├── 02-features/
│   ├── feature-spec_template.md
│   ├── tech-design_template.md
│   ├── dev-tasks_template.md
│   └── test-plan_template.md
└── 03-logs/
    ├── implementation-log_template.md
    ├── decisions-log_template.md
    ├── bug-log_template.md
    ├── validation-log_template.md
    └── insights_template.md
```

**LLM Usage:** When asked to create a document, reference the appropriate template from this folder.

### `02-features/` - HOW features are designed & built

Create a new folder for each feature:

```
02-features/
├── expense-entry/           # Example completed feature
│   ├── feature-spec.md
│   ├── tech-design.md
│   ├── dev-tasks.md
│   └── test-plan.md
└── {{new-feature}}/         # Copy templates for new features
    └── ...
```

### `03-logs/` - MEMORY (This is what most teams miss!)

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `implementation-log.md` | What changed and why | After each session |
| `decisions-log.md` | Architectural decisions (ADRs) | When decisions are made |
| `bug-log.md` | Bugs and their fixes | When bugs are found/fixed |
| `validation-log.md` | Post-shipping observations | After releases |
| `insights.md` | Learnings for future | Ongoing |

**These logs give the LLM "memory" across sessions!**

### `04-process/` - HOW to work with this system

| File | Purpose |
|------|---------|
| `dev-workflow.md` | Daily development loop (human + LLM) |
| `definition-of-done.md` | Quality gates and checklists |
| `llm-prompts.md` | Copy-paste prompt templates |

---

## 🔄 The Development Loop

```
┌─────────────────────────────────────────────────────────────┐
│                    DAILY DEV LOOP                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. CONTEXT LOAD                                            │
│     └── Share vision.md + relevant feature docs with LLM    │
│                                                             │
│  2. TASK SELECTION                                          │
│     └── Pick next task from dev-tasks.md                    │
│                                                             │
│  3. IMPLEMENTATION                                          │
│     └── Execute task with LLM assistance                    │
│                                                             │
│  4. VALIDATION                                              │
│     └── Test against test-plan.md criteria                  │
│                                                             │
│  5. DOCUMENTATION                                           │
│     └── Update logs (implementation, decisions, bugs)       │
│                                                             │
│  6. COMMIT                                                  │
│     └── Clear commit message referencing task               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 💡 Best Practices

### DO ✅

- **Keep vision.md concise** - Under 500 words, it's an anchor not a novel
- **Make tasks atomic** - Each task in dev-tasks.md should be completable in one LLM session
- **Log everything** - The logs ARE your project's memory
- **Reference docs in prompts** - "Based on vision.md and tech-design.md, implement..."
- **Update system-state.md** - Keep it current so LLM knows what exists

### DON'T ❌

- **Don't skip the logs** - Without them, every conversation starts from zero
- **Don't write vague tasks** - "Make it work" is not a task
- **Don't let docs go stale** - Outdated docs = confused LLM = bad code
- **Don't mix features** - One feature folder per capability

---

## 🛠️ LLM Prompt Patterns

**Placeholder Syntax:** `{{file.md}}` means insert content from that file

### Starting a New Session

```markdown
I'm working on {{PROJECT_NAME}}. Here's the context:

## Vision
{{vision.md}}

## Current Feature
{{feature-spec.md}}

## Technical Design
{{tech-design.md}}

## Current Task
{{dev-tasks.md → specific task}}

Please implement this task following the patterns established in the technical design.
```

### Continuing Work

```markdown
Continuing our work on {{PROJECT_NAME}}.

## Recent Implementation
{{implementation-log.md → latest entries}}

## Next Task
{{dev-tasks.md → next task}}

Please continue from where we left off.
```

---

## 📊 Example Project

This template includes a complete example for a **Personal Finance Tracker** app. Review the files to see how each document type should be filled out.

---

## 🔗 Quick Links by Scenario

| I want to... | Start here |
|--------------|------------|
| Build a new app | [Scenario A](#scenario-a-building-from-scratch) → `vision.md` |
| Document existing project | [Scenario B](#scenario-b-adopting-for-existing-project) → `system-state.md` |
| Add a new feature | [Scenario C](#scenario-c-adding-a-new-feature) → `02-features/` |
| Fix a bug | [Scenario D](#scenario-d-fixing-a-bug) → `bug-log.md` |
| Refactor code | [Scenario E](#scenario-e-refactoring-code) → `decisions-log.md` |
| Onboard new developer | [Scenario F](#scenario-f-onboarding-a-new-developer) → This README |
| Maintain the project | [Scenario G](#scenario-g-maintenance-mode) → Weekly checklist |

---

**Happy Vibe Coding! 🎸**
