# Vibe Coding Base Templates

> **Purpose:** Base templates for all documentation files in the Vibe Coding system  
> **For:** LLMs and developers creating new documentation

---

## 🚀 Starting from Just an Idea?

Follow this step-by-step guide to go from "I have an idea" to "I have a complete project plan."

### 🤖 Want AI to Generate Everything?

| Your AI Tool | Use This Guide |
|--------------|----------------|
| **With file access** (Cursor, Claude Desktop, Windsurf) | **[→ quick-prompts.md](./quick-prompts.md)** - Short prompts that reference templates |
| **Web-based** (ChatGPT, Claude.ai, web interfaces) | **[→ prompts-guide.md](./prompts-guide.md)** - Complete prompts with all instructions |

---

## Step-by-Step: From Idea to Ready-to-Build

### 📋 Overview

```
┌────────────────────────────────────────────────────────────────────┐
│                    FROM IDEA TO PROJECT PLAN                        │
├────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   💡 YOUR IDEA                                                      │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 1: vision.md (30 min)                                     │
│      "Why does this need to exist?"                                 │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 2: assumptions.md (20 min)                                │
│      "What am I betting on?"                                        │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 3: prd.md (1-2 hours)                                     │
│      "What exactly should it do?"                                   │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 4: system-state.md (15 min)                               │
│      "What tech will I use?"                                        │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 5: Feature docs (1-2 hours per feature)                   │
│      "How will I build this?"                                       │
│      │                                                              │
│      ▼                                                              │
│   📄 Step 6: Log files (5 min each)                                 │
│      "Set up project memory"                                        │
│      │                                                              │
│      ▼                                                              │
│   🎉 READY TO BUILD!                                                │
│                                                                     │
└────────────────────────────────────────────────────────────────────┘
```

---

## Step 1: Create Your Vision (30 minutes)

**Template:** `00-context/vision_template.md`  
**Output:** `00-context/vision.md`

### What You Need Before Starting
- Your idea (even if rough)
- Who might use this
- Why existing solutions don't work

### Questions to Answer

Answer these in plain language first, then fill the template:

```
1. THE PROBLEM
   What frustrates you or others that this will fix?
   ________________________________________________

2. THE SOLUTION
   In one sentence, what does your product do?
   ________________________________________________

3. THE USER
   Who specifically will use this? Be concrete.
   (Not "everyone" - think of one real person)
   ________________________________________________

4. THE BOUNDARIES
   What will this NOT do? (Very important!)
   1. ___________________________________________
   2. ___________________________________________
   3. ___________________________________________

5. SUCCESS
   How will you know it's working?
   ________________________________________________
```

### Fill the Template

Now open `00-context/vision_template.md` and create `00-context/vision.md`:

| Section | What to Write |
|---------|---------------|
| Purpose | Your answers to #1 and #2 |
| Target Users | Your answer to #3, expanded with details |
| Boundaries | Your answer to #4 as a table |
| North Star Metrics | Your answer to #5, made measurable |
| Core Principles | 3 rules that guide every decision |
| Success for v1.0 | What "done" looks like for MVP |

**✅ Checkpoint:** Can you explain your product in 2 sentences? If not, simplify.

---

## Step 2: Document Your Assumptions (20 minutes)

**Template:** `00-context/assumptions_template.md`  
**Output:** `00-context/assumptions.md`

### Why This Matters
Every project is built on bets. Writing them down:
- Prevents nasty surprises later
- Helps you validate early
- Shows you where to be careful

### Questions to Answer

```
1. PRODUCT ASSUMPTIONS
   What do you believe about your users that might be wrong?
   - I assume users will ___________________________
   - I assume users want ___________________________
   - I assume users have ___________________________

2. TECHNICAL ASSUMPTIONS
   What technical bets are you making?
   - I assume [technology] can handle ______________
   - I assume [approach] will work because _________

3. RISKS
   What could go wrong?
   - If _____________ doesn't work, then ___________
   - The biggest risk is ___________________________

4. UNKNOWNS
   What don't you know yet?
   - I don't know if ______________________________
   - I need to find out ___________________________
```

### Fill the Template

| Section | What to Write |
|---------|---------------|
| Active Assumptions | Your answers above, with validation methods |
| Known Risks | What could fail + how you'll handle it |
| Open Questions | What you need to answer before building |

**✅ Checkpoint:** Do you have at least 3 assumptions and know how to validate them?

---

## Step 3: Write Your Requirements (1-2 hours)

**Template:** `01-product/prd_template.md`  
**Output:** `01-product/prd.md`

### This Builds On
- vision.md (what we're building)
- assumptions.md (what we're betting on)

### Questions to Answer

```
1. MVP GOALS
   What are the top 3 things v1.0 MUST achieve?
   1. ___________________________________________
   2. ___________________________________________
   3. ___________________________________________

2. USER STORIES (repeat for each feature)
   As a [who], I want [what] so that [why].

   Feature 1: As a _______, I want to _____________
              so that ___________________________

   Feature 2: As a _______, I want to _____________
              so that ___________________________

   Feature 3: As a _______, I want to _____________
              so that ___________________________

3. ACCEPTANCE CRITERIA (for each story)
   How do we know Feature 1 is done?
   - [ ] ________________________________________
   - [ ] ________________________________________

4. OUT OF SCOPE
   What features are you explicitly NOT building in v1?
   - ____________________________________________
   - ____________________________________________
```

### Fill the Template

| Section | What to Write |
|---------|---------------|
| Goals | Your top 3 goals, made specific |
| User Stories | Each feature as a user story with criteria |
| Out of Scope | What v1 doesn't include |
| Non-Functional Requirements | Performance, accessibility, security needs |

**✅ Checkpoint:** Does each user story have clear acceptance criteria that can be tested?

---

## Step 4: Initialize System State (15 minutes)

**Template:** `00-context/system-state_template.md`  
**Output:** `00-context/system-state.md`

### This Builds On
- PRD (what we need to build influences tech choices)

### Questions to Answer

```
1. TECH STACK
   What technologies will you use?

   Frontend Framework: _____________________________
   Styling:          _____________________________
   State Management: _____________________________
   Database:         _____________________________
   Hosting:          _____________________________

2. WHY THESE CHOICES?
   (Document in decisions-log.md later)

3. CURRENT STATUS
   What exists right now? (Usually: nothing yet!)
```

### Fill the Template

| Section | What to Write |
|---------|---------------|
| Current Tech Stack | Your chosen technologies + versions |
| What's Built vs Planned | Mark everything as "📋 Planned" for now |
| File Structure | Your intended project structure |
| Development Environment | How to run the project locally |

**✅ Checkpoint:** Could a developer clone your repo and run the project with this info?

---

## Step 5: Plan Your First Feature (1-2 hours)

Now pick your MOST IMPORTANT feature from the PRD and create full documentation for it.

### 5A: Feature Spec (30 min)

**Template:** `02-features/feature-spec_template.md`  
**Output:** `02-features/{{feature-name}}/feature-spec.md`

```
Questions to answer:
- What is the user trying to do?
- What's the step-by-step journey?
- What are all the edge cases?
- How do we know it worked?
```

### 5B: Technical Design (45 min)

**Template:** `02-features/tech-design_template.md`  
**Output:** `02-features/{{feature-name}}/tech-design.md`

```
Questions to answer:
- What components do I need?
- How does data flow through them?
- What's the data model?
- What files will I create?
```

### 5C: Development Tasks (30 min)

**Template:** `02-features/dev-tasks_template.md`  
**Output:** `02-features/{{feature-name}}/dev-tasks.md`

```
Questions to answer:
- How can I break this into 30-60 minute chunks?
- What's the order of dependencies?
- What context does each task need?
```

### 5D: Test Plan (15 min)

**Template:** `02-features/test-plan_template.md`  
**Output:** `02-features/{{feature-name}}/test-plan.md`

```
Questions to answer:
- How will I test each acceptance criterion?
- What are the edge cases to test?
- How do I check accessibility?
```

**✅ Checkpoint:** Do you have 5+ atomic tasks ready to hand to an AI assistant?

---

## Step 6: Initialize Your Logs (15 minutes total)

Create empty log files to track progress as you build.

### 6A: Implementation Log (3 min)

**Template:** `03-logs/implementation-log_template.md`  
**Output:** `03-logs/implementation-log.md`

Just create the file with headers. You'll add entries as you code.

### 6B: Decisions Log (3 min)

**Template:** `03-logs/decisions-log_template.md`  
**Output:** `03-logs/decisions-log.md`

Add your first decision: "Why I chose [tech stack]"

### 6C: Bug Log (3 min)

**Template:** `03-logs/bug-log_template.md`  
**Output:** `03-logs/bug-log.md`

Just create the file with headers. Empty is good!

### 6D: Validation Log (3 min)

**Template:** `03-logs/validation-log_template.md`  
**Output:** `03-logs/validation-log.md`

Just create the file with headers. Used after launch.

### 6E: Insights (3 min)

**Template:** `03-logs/insights_template.md`  
**Output:** `03-logs/insights.md`

Just create the file with headers. Add learnings as you go.

---

## 🎉 You're Ready to Build!

### What You Now Have

```
docs/
├── 00-context/
│   ├── vision.md              ✅ WHY you're building
│   ├── assumptions.md         ✅ What you're betting on
│   └── system-state.md        ✅ What tech you're using
│
├── 01-product/
│   └── prd.md                 ✅ WHAT you're building
│
├── 02-features/
│   └── {{first-feature}}/
│       ├── feature-spec.md    ✅ User perspective
│       ├── tech-design.md     ✅ Technical perspective
│       ├── dev-tasks.md       ✅ Tasks for AI
│       └── test-plan.md       ✅ How to validate
│
└── 03-logs/
    ├── implementation-log.md  ✅ Track changes
    ├── decisions-log.md       ✅ Track decisions
    ├── bug-log.md             ✅ Track bugs
    ├── validation-log.md      ✅ Track feedback
    └── insights.md            ✅ Track learnings
```

### Next Steps

1. **Open `dev-tasks.md`** for your first feature
2. **Pick TASK-001**
3. **Start an AI session** with:
   ```
   I'm building {{project}}. Here's the context:
   
   ## Vision
   {{vision.md content}}
   
   ## Task
   {{TASK-001 from dev-tasks.md}}
   
   Please implement this task.
   ```
4. **After completing each task**, update:
   - dev-tasks.md (mark complete)
   - implementation-log.md (what changed)
5. **Repeat until feature is done!**

---

## 📊 Time Investment Summary

| Document | Time | Creates |
|----------|------|---------|
| vision.md | 30 min | Project purpose |
| assumptions.md | 20 min | Risk awareness |
| prd.md | 1-2 hrs | Requirements |
| system-state.md | 15 min | Tech decisions |
| Feature docs (×4) | 2 hrs | Build-ready specs |
| Log files (×5) | 15 min | Project memory |
| **TOTAL** | **4-5 hours** | Complete project plan |

**ROI:** This 4-5 hour investment saves 10-20+ hours of confusion, rework, and context-switching during development.

---

## Template Index (Quick Reference)

### 00-context/ - Project Context

| Template | Creates | Time |
|----------|---------|------|
| `vision_template.md` | `00-context/vision.md` | 30 min |
| `assumptions_template.md` | `00-context/assumptions.md` | 20 min |
| `system-state_template.md` | `00-context/system-state.md` | 15 min |

### 01-product/ - Product Requirements

| Template | Creates | Time |
|----------|---------|------|
| `prd_template.md` | `01-product/prd.md` | 1-2 hrs |

### 02-features/ - Feature Documentation

| Template | Creates | Time |
|----------|---------|------|
| `feature-spec_template.md` | `02-features/{{name}}/feature-spec.md` | 30 min |
| `tech-design_template.md` | `02-features/{{name}}/tech-design.md` | 45 min |
| `dev-tasks_template.md` | `02-features/{{name}}/dev-tasks.md` | 30 min |
| `test-plan_template.md` | `02-features/{{name}}/test-plan.md` | 15 min |

### 03-logs/ - Project Memory

| Template | Creates | Time |
|----------|---------|------|
| `implementation-log_template.md` | `03-logs/implementation-log.md` | 3 min |
| `decisions-log_template.md` | `03-logs/decisions-log.md` | 3 min |
| `bug-log_template.md` | `03-logs/bug-log.md` | 3 min |
| `validation-log_template.md` | `03-logs/validation-log.md` | 3 min |
| `insights_template.md` | `03-logs/insights.md` | 3 min |

---

## Placeholder Syntax

All templates use this placeholder syntax:

- `{{PLACEHOLDER}}` - Replace with your content
- `{{OPTIONAL}}` - Optional field, can be removed
- `{{file.md}}` - Reference to content from another file
- `{{DATE}}` - Current date in YYYY-MM-DD format

---

## For LLMs: How to Use These Templates

When asked to create a new document:

1. **Identify the correct template** from the index above
2. **Read the template file** to understand structure and LLM instructions
3. **Follow the "LLM Instructions" section** in the template
4. **Replace all `{{PLACEHOLDER}}` values** with actual content
5. **Save to the correct output location**

Example:
```
User: "Create a vision document for a task management app"

LLM Actions:
1. Read _templates/00-context/vision_template.md
2. Follow LLM Instructions
3. Create 00-context/vision.md with filled content
```
