# Quick Prompts (Reference-Based)

> **Purpose:** Minimal prompts that reference existing templates  
> **For:** AI tools with file access (Cursor, Claude Desktop, Windsurf, etc.)  
> **Usage:** AI reads the template file and creates the output

---

## 🎯 When to Use This

Use these quick prompts when your AI tool can **read files from your project**:
- ✅ Cursor
- ✅ Claude Desktop with MCP
- ✅ Windsurf
- ✅ GitHub Copilot Workspace
- ✅ Any AI with file system access

For web-based AI (ChatGPT, Claude.ai), use [prompts-guide.md](./prompts-guide.md) instead.

---

## Complete Project Setup (All Documents)

```
I'm starting a new project and want to set up all Vibe Coding documentation.

My project idea: [DESCRIBE YOUR IDEA IN 2-3 SENTENCES]

Target user: [WHO WILL USE THIS]

Key features:
1. [FEATURE 1]
2. [FEATURE 2]
3. [FEATURE 3]

Please read the templates in docs/_templates/ and create:

1. docs/00-context/vision.md
   → Use template: docs/_templates/00-context/vision_template.md

2. docs/00-context/assumptions.md
   → Use template: docs/_templates/00-context/assumptions_template.md

3. docs/01-product/prd.md
   → Use template: docs/_templates/01-product/prd_template.md

4. docs/00-context/system-state.md
   → Use template: docs/_templates/00-context/system-state_template.md

5. docs/02-features/[first-feature]/feature-spec.md
   → Use template: docs/_templates/02-features/feature-spec_template.md

6. docs/02-features/[first-feature]/tech-design.md
   → Use template: docs/_templates/02-features/tech-design_template.md

7. docs/02-features/[first-feature]/dev-tasks.md
   → Use template: docs/_templates/02-features/dev-tasks_template.md

8. docs/03-logs/implementation-log.md
   → Use template: docs/_templates/03-logs/implementation-log_template.md

9. docs/03-logs/decisions-log.md
   → Use template: docs/_templates/03-logs/decisions-log_template.md

Follow the LLM Instructions in each template. Fill all {{PLACEHOLDER}} values with actual content.
```

---

## Individual Document Prompts

### Step 1: Vision

```
Create docs/00-context/vision.md for my project.

My idea: [YOUR IDEA]
Target user: [WHO]
Main problem: [PROBLEM IT SOLVES]
Not building: [OUT OF SCOPE]

Use template: docs/_templates/00-context/vision_template.md
Follow the LLM Instructions section.
```

---

### Step 2: Assumptions

```
Create docs/00-context/assumptions.md based on my vision.

Reference: docs/00-context/vision.md (already created)
Use template: docs/_templates/00-context/assumptions_template.md

Identify product assumptions, technical assumptions, risks, and open questions.
```

---

### Step 3: PRD

```
Create docs/01-product/prd.md based on my vision and assumptions.

Reference: 
- docs/00-context/vision.md
- docs/00-context/assumptions.md

Use template: docs/_templates/01-product/prd_template.md

Create user stories with acceptance criteria for all features.
```

---

### Step 4: System State

```
Create docs/00-context/system-state.md for my project.

Reference: docs/01-product/prd.md (for requirements)
Use template: docs/_templates/00-context/system-state_template.md

Recommend an appropriate tech stack based on the requirements.
Mark all features as "📋 Planned" since we're just starting.
```

---

### Step 5A: Feature Spec

```
Create docs/02-features/[FEATURE_NAME]/feature-spec.md

Reference:
- docs/00-context/vision.md
- docs/01-product/prd.md (relevant user stories)

Use template: docs/_templates/02-features/feature-spec_template.md

Focus on: [SPECIFIC FEATURE FROM PRD]
```

---

### Step 5B: Technical Design

```
Create docs/02-features/[FEATURE_NAME]/tech-design.md

Reference:
- docs/02-features/[FEATURE_NAME]/feature-spec.md
- docs/00-context/system-state.md (tech stack)

Use template: docs/_templates/02-features/tech-design_template.md
```

---

### Step 5C: Development Tasks

```
Create docs/02-features/[FEATURE_NAME]/dev-tasks.md

Reference: docs/02-features/[FEATURE_NAME]/tech-design.md
Use template: docs/_templates/02-features/dev-tasks_template.md

Break into 5-10 atomic tasks, each completable in 30-60 minutes.
```

---

### Step 5D: Test Plan

```
Create docs/02-features/[FEATURE_NAME]/test-plan.md

Reference:
- docs/02-features/[FEATURE_NAME]/feature-spec.md (acceptance criteria)
- docs/02-features/[FEATURE_NAME]/tech-design.md (components)

Use template: docs/_templates/02-features/test-plan_template.md
```

---

### Step 6: Initialize Logs

```
Initialize all log files for my project:

1. Create docs/03-logs/implementation-log.md
   → Template: docs/_templates/03-logs/implementation-log_template.md
   → Add first entry: "Project Setup - Initial documentation created"

2. Create docs/03-logs/decisions-log.md
   → Template: docs/_templates/03-logs/decisions-log_template.md
   → Add ADR-001 for tech stack decision based on system-state.md

3. Create docs/03-logs/bug-log.md
   → Template: docs/_templates/03-logs/bug-log_template.md
   → Empty, ready for bugs

4. Create docs/03-logs/validation-log.md
   → Template: docs/_templates/03-logs/validation-log_template.md
   → Empty, ready for post-launch

5. Create docs/03-logs/insights.md
   → Template: docs/_templates/03-logs/insights_template.md
   → Empty, ready for learnings
```

---

## Add New Feature (After Initial Setup)

```
I want to add a new feature to my project.

Feature: [FEATURE NAME]
Description: [WHAT IT DOES]

Please create:
1. docs/02-features/[feature-name]/feature-spec.md
   → Template: docs/_templates/02-features/feature-spec_template.md

2. docs/02-features/[feature-name]/tech-design.md
   → Template: docs/_templates/02-features/tech-design_template.md

3. docs/02-features/[feature-name]/dev-tasks.md
   → Template: docs/_templates/02-features/dev-tasks_template.md

4. docs/02-features/[feature-name]/test-plan.md
   → Template: docs/_templates/02-features/test-plan_template.md

Reference existing:
- docs/00-context/vision.md (for consistency)
- docs/00-context/system-state.md (for tech stack)
- docs/01-product/prd.md (for related user stories)
```

---

## Update Existing Document

```
Update docs/[PATH_TO_FILE].md

Change needed: [WHAT TO CHANGE]

Reference the original template if structure guidance needed:
Template: docs/_templates/[CORRESPONDING_TEMPLATE].md

After updating, add an entry to:
- docs/03-logs/implementation-log.md (if code-related)
- docs/03-logs/decisions-log.md (if decision change)
```

---

## Quick Reference: Template Paths

| Document | Template Path |
|----------|---------------|
| vision.md | `docs/_templates/00-context/vision_template.md` |
| assumptions.md | `docs/_templates/00-context/assumptions_template.md` |
| system-state.md | `docs/_templates/00-context/system-state_template.md` |
| prd.md | `docs/_templates/01-product/prd_template.md` |
| feature-spec.md | `docs/_templates/02-features/feature-spec_template.md` |
| tech-design.md | `docs/_templates/02-features/tech-design_template.md` |
| dev-tasks.md | `docs/_templates/02-features/dev-tasks_template.md` |
| test-plan.md | `docs/_templates/02-features/test-plan_template.md` |
| implementation-log.md | `docs/_templates/03-logs/implementation-log_template.md` |
| decisions-log.md | `docs/_templates/03-logs/decisions-log_template.md` |
| bug-log.md | `docs/_templates/03-logs/bug-log_template.md` |
| validation-log.md | `docs/_templates/03-logs/validation-log_template.md` |
| insights.md | `docs/_templates/03-logs/insights_template.md` |

---

## Tips for Best Results

1. **Always fill in the brackets** - `[YOUR IDEA]`, `[FEATURE NAME]`, etc.
2. **AI will read the template** - It contains LLM Instructions for how to fill it
3. **Chain documents together** - Each step references previous outputs
4. **Be specific about your project** - Vague inputs = vague outputs
