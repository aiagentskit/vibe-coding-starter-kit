# AI Prompts for Document Generation

> **Purpose:** Copy-paste prompts to generate all Vibe Coding documentation using AI  
> **For:** New developers starting a project from scratch  
> **Usage:** Follow the sequence from Step 1 to Step 6

---

## 🎯 How to Use This Document

1. **Start with your idea** - just a rough concept is fine
2. **Copy the prompt** for the document you need
3. **Fill in the `[BRACKETS]`** with your information
4. **Paste to your AI assistant** (Claude, GPT-4, Cursor, etc.)
5. **Save the output** to the specified location
6. **Move to the next prompt** - each builds on the previous

---

## 🚀 Quick Start: The One Prompt to Start

If you want to jump right in, use this single prompt to get your project scaffolded:

```markdown
I want to start a new project using the Vibe Coding documentation system.

My project idea: [DESCRIBE YOUR IDEA IN 2-3 SENTENCES]

Please help me create the initial documentation by:
1. First, create a vision.md file that defines the purpose, target users, boundaries, and success metrics
2. Then create an assumptions.md file listing the key assumptions, risks, and unknowns

For the vision, focus on:
- What problem this solves
- Who the target user is (be specific)
- What we're NOT building (boundaries)
- How we'll measure success

For assumptions, identify:
- Product assumptions about user behavior
- Technical assumptions about feasibility
- Key risks and mitigation strategies
- Open questions that need answers

Use markdown formatting with tables and clear sections.
```

---

## Step 1: Create Vision Document

### 1A: Initial Vision (From Scratch)

**Use when:** Starting with just an idea  
**Output:** `docs/00-context/vision.md`

```markdown
Create a vision.md document for my new project.

## My Project Idea
[DESCRIBE YOUR PROJECT - what it does, why it matters, rough scope]

## Who I Think Will Use This
[DESCRIBE YOUR TARGET USER - be as specific as possible]

## Problems I'm Trying to Solve
[LIST 2-3 PROBLEMS your product addresses]

## What I Know I DON'T Want to Build
[LIST things that are OUT OF SCOPE]

---

Please create a vision.md document following this structure:

1. **Purpose** (2-3 paragraphs)
   - The problem being solved
   - Why this product needs to exist
   - Our high-level solution

2. **Target Users** section with:
   - Primary persona (name, age range, profile, pain point, goal, tech comfort)
   - Optional secondary persona

3. **Boundaries** table showing:
   - What we will NOT build
   - Why each is excluded

4. **North Star Metrics** table with:
   - 2-3 measurable metrics
   - Target values
   - Why each matters

5. **Core Principles** (3 guiding rules for decisions)

6. **Future Considerations** (what might come after v1, but is explicitly out for now)

7. **Success Definition for v1.0** (4-5 checkboxes of what "done" looks like)

Use professional markdown formatting with emojis for section headers.
```

---

### 1B: Refine Vision (From Rough Draft)

**Use when:** You have a rough vision and want to improve it  
**Input needed:** Your existing rough vision.md

```markdown
Please review and improve this vision document:

## Current Vision
[PASTE YOUR EXISTING VISION.MD CONTENT]

---

Please improve this by:
1. Making the purpose more compelling and specific
2. Making target users more concrete (give them realistic characteristics)
3. Adding any missing boundaries that should be explicit
4. Ensuring north star metrics are truly measurable
5. Creating core principles that actually help with decisions
6. Making success criteria specific and testable

Output the complete revised vision.md.
```

---

## Step 2: Create Assumptions Document

**Use when:** After creating vision.md  
**Output:** `docs/00-context/assumptions.md`

```markdown
Based on this vision, create an assumptions.md document:

## Vision Summary
[PASTE KEY SECTIONS FROM YOUR VISION.MD - purpose, target users, boundaries]

---

Please create an assumptions.md document that identifies:

### Product Assumptions (things we believe about users)
- At least 3 assumptions about user behavior, needs, or preferences
- Each with: what we assume, risk if wrong, how to validate

### Technical Assumptions (things we believe about technology)
- At least 2 assumptions about our tech choices
- Each with: what we assume, risk if wrong, how to validate

### Business Assumptions (if applicable)
- Assumptions about market, timing, resources

### Known Risks (things that could go wrong)
- At least 2 high-priority risks
- At least 2 medium-priority risks
- Each with: likelihood, impact, mitigation strategy, owner

### Open Questions (unknowns we need to answer)
- At least 2 questions we must answer before v1.0
- At least 2 questions we can answer during development
- Each with: deadline (if required pre-launch) and notes

Include a "Validation Log" section (empty for now) and a "Next Review" placeholder.

Use markdown tables for structured data.
```

---

## Step 3: Create Product Requirements Document

**Use when:** After vision.md and assumptions.md are complete  
**Output:** `docs/01-product/prd.md`

```markdown
Based on this vision and assumptions, create a comprehensive PRD:

## Vision
[PASTE YOUR COMPLETE VISION.MD]

## Key Assumptions
[PASTE THE KEY ASSUMPTIONS FROM ASSUMPTIONS.MD]

---

Please create a prd.md (Product Requirements Document) with:

### Goals for v1.0
- Top 3-5 measurable goals for the MVP
- Each goal should be specific and verifiable

### User Stories (organized by Epic)
Create at least 3 Epics, each with 2-4 user stories.

For each user story:
- Format: "As a [user type], I want to [action] so that [benefit]"
- Acceptance criteria (3-5 testable checkboxes per story)
- Priority: P0 (must have), P1 (should have), or P2 (nice to have)
- Story points estimate (S/M/L)

### Default Data/Settings
- Any seed data, default configurations, or initial content needed

### Non-Functional Requirements
- Performance (specific targets like "page load < 2s")
- Accessibility (WCAG level, specific requirements)
- Browser support (which browsers, minimum versions)
- Security (data handling, authentication requirements)

### Out of Scope for v1.0
- Features explicitly NOT being built
- Why each is deferred

### Release Plan  
- Rough sprint breakdown (Sprint 1 features, Sprint 2 features, etc.)
- Post-MVP roadmap preview

Use markdown tables where appropriate. Make acceptance criteria specific and testable.
```

---

## Step 4: Create System State Document

**Use when:** After PRD is complete, before feature design  
**Output:** `docs/00-context/system-state.md`

```markdown
Based on this project scope, create a system-state.md document:

## Vision Summary
[PASTE 2-3 SENTENCE SUMMARY OF YOUR PRODUCT]

## Non-Functional Requirements
[PASTE THE NON-FUNCTIONAL REQUIREMENTS FROM PRD.MD]

## My Technology Preferences (if any)
[LIST ANY TECH YOU'VE ALREADY DECIDED ON, OR SAY "RECOMMEND BASED ON REQUIREMENTS"]

---

Please create a system-state.md document with:

### Current Tech Stack
Recommend appropriate technologies for:
- Frontend (framework, build tool, styling approach, state management)
- Backend (if needed - runtime, database)
- Infrastructure (hosting, CI/CD)

For each technology:
- Name and version
- Why it's appropriate for this project
- Any notes or alternatives considered

### What's Built vs Planned
Create a table showing:
- All major features from the PRD
- Status: ✅ Complete | 🚧 In Progress | 📋 Planned
- Completion percentage
- Notes

(Initially, everything should be "📋 Planned" at 0%)

### Current File Structure
Propose a sensible project file structure based on the tech stack.

### Database Schema (if applicable)
Define initial data models based on the PRD requirements.

### Deployment Status
Show environments (Local Dev, Staging, Production) with status.

### Development Environment
- Required tools and versions
- Commands to install and run

### Performance Baseline
- Key metrics to track
- Target values (from NFRs)

Mark this as "Status: Initial Setup" with today's date.
```

---

## Step 5: Create Feature Documentation

### 5A: Feature Spec

**Use when:** Starting work on a specific feature  
**Output:** `docs/02-features/[feature-name]/feature-spec.md`

```markdown
Create a feature specification for this feature:

## Project Vision
[PASTE KEY POINTS FROM VISION.MD - 3-4 sentences]

## User Stories for This Feature
[PASTE THE RELEVANT USER STORIES FROM PRD.MD]

## Feature Name
[NAME OF THIS FEATURE, e.g., "User Authentication", "Expense Entry", "Dashboard"]

---

Please create a feature-spec.md document with:

### Purpose
- 2-3 sentences explaining why this feature exists
- What user problem it solves

### User Intent
- Who: specific user type
- What: what they're trying to accomplish
- When: what triggers this action
- Why: underlying motivation

### User Journey
- ASCII diagram showing step-by-step flow
- From trigger to success state

### Acceptance Criteria
- Core functionality (P0 items - must work)
- Enhanced functionality (P1 items - should work)
- Each with unique ID (AC-01, AC-02, etc.)

### Edge Cases
- Error scenarios
- Boundary conditions
- Each with expected behavior

### UI/UX Requirements
- ASCII wireframe of the layout
- Interaction details table (element → behavior)
- Key visual requirements

### Success Metrics
- How we measure if this feature is successful
- Specific target values

### Out of Scope
- What this feature explicitly doesn't do

### Dependencies
- Technical dependencies (other features, libraries)
- Data dependencies
- External dependencies

Use ASCII art for diagrams and wireframes. Be specific and testable.
```

---

### 5B: Technical Design

**Use when:** After feature-spec.md is approved  
**Output:** `docs/02-features/[feature-name]/tech-design.md`

```markdown
Create a technical design for this feature:

## Feature Spec
[PASTE YOUR COMPLETE FEATURE-SPEC.MD]

## System State (Tech Stack)
[PASTE THE RELEVANT TECH STACK SECTIONS FROM SYSTEM-STATE.MD]

---

Please create a tech-design.md document with:

### Architecture Overview
- Component hierarchy (ASCII diagram)
- Data flow diagram (ASCII)
- How this feature integrates with existing system

### Data Models
- TypeScript/JavaScript interfaces for all data structures
- Include all fields with types
- Validation schema using Zod (or similar)

### Component Specifications
For each component needed:
- Name and purpose
- Props interface (TypeScript)
- Key behaviors
- Implementation notes

### Implementation Approach
Break into phases:
- Phase 1: Foundation (what to build first)
- Phase 2: Core Logic
- Phase 3: Integration  
- Phase 4: Polish

For each phase, list specific tasks.

### File Structure
- Where each new file should go
- Follow project conventions from system-state.md

### Performance Considerations
- What could be slow?
- How to optimize?

### Security Considerations
- What could be vulnerable?
- How to mitigate?

### Testing Strategy Summary
- What to unit test
- What to integration test
- What to manually test

Use TypeScript code blocks for interfaces. Use ASCII for diagrams.
```

---

### 5C: Development Tasks

**Use when:** After tech-design.md is complete  
**Output:** `docs/02-features/[feature-name]/dev-tasks.md`

```markdown
Break this technical design into atomic development tasks:

## Technical Design
[PASTE YOUR COMPLETE TECH-DESIGN.MD]

---

Please create a dev-tasks.md document with:

### Overview
- Total number of tasks
- Estimated total time
- How to use this document

### Tasks (organized by phase)

Create 5-10 tasks, each with:

1. **Task ID** (TASK-001, TASK-002, etc.)

2. **Task Title** (clear, action-oriented)

3. **Status** (all start as ⬜ Not Started)

4. **Priority** (P0, P1, or P2)

5. **Estimated Time** (30-60 minutes ideal)

6. **Dependencies** (which tasks must be done first)

7. **Context Files to Include**
   - Which docs should be shared with AI when doing this task
   - Include specific sections

8. **Task Description**
   - Detailed instructions
   - Files to create/modify
   - Specific requirements
   - Expected behavior

9. **Acceptance Criteria**
   - 3-5 testable checkboxes per task
   - Specific and verifiable

### Progress Tracker Table
- All tasks with status
- Columns: Task, Title, Status, Assigned, Completed Date

Order tasks by dependency - foundation first, integration later, polish last.
Make each task completable in a single AI coding session.
```

---

### 5D: Test Plan

**Use when:** Alongside or after dev-tasks.md  
**Output:** `docs/02-features/[feature-name]/test-plan.md`

```markdown
Create a test plan for this feature:

## Feature Spec
[PASTE THE ACCEPTANCE CRITERIA AND EDGE CASES FROM FEATURE-SPEC.MD]

## Technical Design
[PASTE THE COMPONENT SPECIFICATIONS FROM TECH-DESIGN.MD]

---

Please create a test-plan.md document with:

### Overview
- Testing priorities (what's most critical)
- Test coverage goals

### Unit Tests
For each component:
- Test ID (UT-001, etc.)
- What to test
- Expected result
- Example test code structure

### Integration Tests
For each user flow:
- Test ID (INT-001, etc.)
- Description
- Steps
- Expected result

### Manual Testing Checklists
Tables for:
- Happy path testing (step-by-step with checkboxes)
- Edge cases testing
- Error handling testing

### Accessibility Testing
- Keyboard navigation tests
- Screen reader tests
- Visual accessibility tests (contrast, zoom)

### Cross-Browser Testing
Matrix of browsers × devices to test

### Performance Testing
- Metrics to measure
- Target values
- How to measure

### Sign-off Section
- Developer, QA, Product approval rows

Include example test code snippets for unit tests.
```

---

## Step 6: Initialize Log Files

### 6A: Implementation Log

**Output:** `docs/03-logs/implementation-log.md`

```markdown
Create an initial implementation-log.md file for my project:

## Project Name
[YOUR PROJECT NAME]

---

Create a clean implementation-log.md with:

1. Header with project name and purpose
2. "How to Use This Log" section explaining when to add entries
3. First entry: "Session 1: Project Setup"
   - Date: today
   - What was implemented: "Initial project documentation"
   - Files changed: list the docs we created
   - Notes: "Ready to begin development"
4. Entry template section for future entries
5. Related documents links

This is the start of our project memory.
```

---

### 6B: Decisions Log (with first ADR)

**Output:** `docs/03-logs/decisions-log.md`

```markdown
Create a decisions-log.md with our first architectural decision:

## Tech Stack Decision
[PASTE THE TECH STACK FROM SYSTEM-STATE.MD]

---

Create a decisions-log.md with:

1. Header explaining ADR format
2. "How to Use This Log" section

3. First decision (ADR-001): Tech Stack Selection
   - Document why we chose each major technology
   - Options we considered
   - Why we chose what we chose
   - Consequences (positive and negative)

4. ADR template section for future decisions

5. Related documents links

Format using the standard ADR (Architecture Decision Record) structure.
```

---

### 6C: Bug Log (Empty)

**Output:** `docs/03-logs/bug-log.md`

```markdown
Create an empty bug-log.md template for my project:

## Project Name
[YOUR PROJECT NAME]

---

Create a bug-log.md with:

1. Header with project name
2. "How to Use This Log" instructions
3. Summary section (showing 0 bugs currently)
4. Empty "Open Bugs" section
5. Empty "In Progress" section
6. Empty "Fixed Bugs" section
7. Bug entry template for future use
8. Related documents links

The file should be ready to receive bug reports as development progresses.
```

---

### 6D: Validation Log (Empty)

**Output:** `docs/03-logs/validation-log.md`

```markdown
Create an empty validation-log.md template for my project:

## Project Name
[YOUR PROJECT NAME]

---

Create a validation-log.md with:

1. Header with project name
2. "How to Use This Log" instructions
3. Empty "Pre-Release Validation" section (placeholder for beta testing)
4. Empty "Post-Release Validation" section (placeholder for launch metrics)
5. Empty "User Feedback" section
6. Empty "Incident Log" section
7. Release validation checklist template
8. Related documents links

This will be populated once we start testing and releasing.
```

---

### 6E: Insights (Initial)

**Output:** `docs/03-logs/insights.md`

```markdown
Create an insights.md file for my project:

## Project Name
[YOUR PROJECT NAME]

## Tech Stack
[LIST YOUR MAIN TECHNOLOGIES]

---

Create an insights.md with:

1. Header with project name
2. "How to Use This Document" section

3. "Technical Insights" section with subsections:
   - What Worked Well (empty, ready for entries)
   - What Didn't Work (empty, ready for entries)

4. "Process Insights" section (empty)

5. "Feature Ideas for Future" section with two tables:
   - Near-term (next version)
   - Long-term (future versions)
   (Can pre-populate with "Out of Scope" items from vision/PRD)

6. "Retrospective Notes" section (empty)

7. "Knowledge Base" section with:
   - Useful Code Patterns (empty)
   - External Resources (link to any docs for chosen tech stack)

8. Entry template for new insights

9. Related documents links
```

---

## 🎉 Complete Project Setup Prompt (All-in-One)

For AI tools that support long conversations, here's a complete prompt to generate everything:

```markdown
I want to set up a complete project using the Vibe Coding documentation system.

## My Project Idea
[DESCRIBE YOUR PROJECT IN 3-5 SENTENCES]

## Target User
[DESCRIBE WHO WILL USE THIS]

## Key Features I Want
1. [FEATURE 1]
2. [FEATURE 2]
3. [FEATURE 3]

## What I DON'T Want to Build (for v1)
1. [EXCLUDED 1]
2. [EXCLUDED 2]

## Tech Preferences (optional)
[LIST ANY TECH YOU PREFER, OR SAY "RECOMMEND"]

---

Please create the following documents in sequence:

1. **docs/00-context/vision.md**
   - Purpose, target users, boundaries, metrics, principles, success definition

2. **docs/00-context/assumptions.md**
   - Product assumptions, technical assumptions, risks, open questions

3. **docs/01-product/prd.md**
   - Goals, user stories with acceptance criteria, NFRs, release plan

4. **docs/00-context/system-state.md**
   - Recommended tech stack, initial file structure, dev environment

5. **docs/02-features/[first-feature]/feature-spec.md**
   - Spec for the most important feature

6. **docs/02-features/[first-feature]/tech-design.md**
   - Technical design for that feature

7. **docs/02-features/[first-feature]/dev-tasks.md**
   - Atomic tasks breakdown

8. **docs/03-logs/implementation-log.md**
   - Initial entry documenting project setup

9. **docs/03-logs/decisions-log.md**
   - First ADR for tech stack decision

Create each document with full content, proper markdown formatting, and section headers.
After creating all documents, provide a summary of what was created and next steps.
```

---

## 💡 Pro Tips

### For Better Results

1. **Be specific about your idea** - vague ideas produce vague docs
2. **Include constraints** - budget, timeline, team size, tech limitations
3. **Mention similar products** - "like X but for Y" helps AI understand scope
4. **Iterate** - ask AI to revise sections that don't feel right

### Chaining Prompts

Each document builds on the previous. For best results:
1. Complete each document before moving to the next
2. Paste relevant sections from previous docs into new prompts
3. Ask AI to maintain consistency with earlier decisions

### If Documents Feel Wrong

```markdown
This doesn't quite match what I had in mind.

The problem is: [WHAT'S WRONG]

What I actually want is: [WHAT YOU WANT]

Please revise the [SECTION] to reflect this.
```

---

## 📋 Quick Reference: Which Prompt When

| I want to... | Use prompt |
|--------------|------------|
| Start from just an idea | Step 1A: Initial Vision |
| Improve a rough vision | Step 1B: Refine Vision |
| Document my assumptions | Step 2: Assumptions |
| Define what to build | Step 3: PRD |
| Choose tech stack | Step 4: System State |
| Plan a feature | Step 5A-5D: Feature Docs |
| Set up project memory | Step 6A-6E: Log Files |
| Do everything at once | Complete Project Setup |
