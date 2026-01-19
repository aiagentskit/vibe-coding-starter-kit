# LLM Prompts Library

> **Project:** Personal Finance Tracker  
> **Purpose:** Copy-paste prompts optimized for AI-assisted development  
> **Version:** 1.0

---

## Overview

This document contains tested prompts for common development tasks. Each prompt is designed to maximize AI output quality by providing the right structure and context.

**Placeholder Syntax:**
- `{{file.md}}` → Insert content from that file
- `{{DESCRIPTION}}` → Insert your own content for that field
- For AI tools with file access (Cursor, Claude Desktop), reference files directly: `@docs/00-context/vision.md`

---

## Starting a Session

### Prompt: Initialize New Session

Use at the start of each development session to establish context.

```markdown
I'm working on a project called {{PROJECT_NAME}}.

## Project Vision
{{vision.md}}

## What's Currently Built
{{system-state.md}}

## Today's Focus
I want to work on {{FEATURE_OR_COMPONENT_NAME}}.

Here's the task I'm tackling:
{{dev-tasks.md → specific task}}

Let me know when you're ready, and I'll share any additional context needed.
```

---

### Prompt: Continue Previous Work

Use when resuming work from a previous session.

```markdown
I'm continuing work on {{PROJECT_NAME}}.

## Quick Context
{{vision.md → 2-3 sentence summary}}

## Last Session Summary
{{implementation-log.md → most recent entry}}

## What Was Built
{{RELEVANT_CODE_OR_STATE}}

## Today's Task
{{dev-tasks.md → next task}}

Let's pick up from where we left off.
```

---

## Document Generation

### Prompt: Generate vision.md

Use when starting a new project.

```markdown
Help me create a vision document for a new project.

## Project Idea
{{YOUR_PROJECT_DESCRIPTION}}

## Target Users
{{WHO_IS_THIS_FOR}}

## Key Problems to Solve
{{LIST_3_TO_5_PROBLEMS}}

## Known Constraints
{{BUDGET_TIME_TECHNICAL_CONSTRAINTS}}

Please generate a vision.md document with the following sections:
1. Purpose - What this product does and why it matters
2. Target Users - Who uses this and their key characteristics
3. Boundaries - What we explicitly are NOT building
4. Core Principles - 3-4 guiding principles for decisions
5. North Star Metrics - How we measure success
6. Success Definition for v1.0 - What does "done" look like for MVP

Use markdown formatting with tables where appropriate.
```

---

### Prompt: Generate PRD

Use after vision.md is complete.

```markdown
Help me create a Product Requirements Document based on this vision:

## Vision
{{vision.md}}

Please generate a PRD with:

1. **Goals for v1.0** - Top 3-5 measurable goals

2. **User Stories** - For each major feature:
   - Story format: "As a [user], I want [action] so that [benefit]"
   - Acceptance criteria as checklist items
   - Priority (P0 = must have, P1 = should have, P2 = nice to have)

3. **Default Settings/Data** - Any seed data or defaults

4. **Non-Functional Requirements**:
   - Performance targets
   - Accessibility requirements
   - Browser support
   - Security considerations

5. **Out of Scope** - Features explicitly not in v1.0

6. **Release Plan** - Rough sprint breakdown

Format with markdown tables for requirements and checklists for acceptance criteria.
```

---

### Prompt: Generate Feature Spec

Use when starting work on a new feature.

```markdown
Help me create a feature specification document.

## Context
{{prd.md → relevant user stories}}

## Feature
{{FEATURE_NAME_AND_DESCRIPTION}}

Please generate a feature-spec.md with:

1. **Purpose** - Why this feature exists (2-3 sentences)

2. **User Intent** - What the user is trying to accomplish

3. **User Journey** - Step-by-step flow diagram (ASCII art)

4. **Acceptance Criteria** - Detailed checklist including:
   - Core functionality requirements
   - Edge cases and error states
   - Validation rules

5. **UI/UX Requirements**:
   - Layout wireframe (ASCII art)
   - Interaction details
   - Visual design specs

6. **Success Metrics** - How we know this works

7. **Out of Scope** - What this feature doesn't do

8. **Dependencies** - What needs to exist before this works
```

---

### Prompt: Generate Technical Design

Use after feature spec is approved.

```markdown
Create a technical design document for this feature:

## Feature Spec
{{feature-spec.md}}

## Current System State
{{system-state.md → relevant sections}}

## Tech Stack
{{YOUR_TECH_STACK}}

Please generate a tech-design.md with:

1. **Architecture Overview**:
   - Component hierarchy diagram (ASCII art)
   - Data flow diagram (ASCII art)

2. **Data Models**:
   - TypeScript/JavaScript interfaces
   - Database schema (if applicable)
   - Validation schema (Zod or similar)

3. **Component Specifications**:
   - For each component:
     - Props interface
     - Key behavior notes
     - Implementation notes

4. **Implementation Approach**:
   - Phased breakdown (what to build first)
   - Estimated time per phase

5. **File Structure**:
   - Where each file should go
   - Naming conventions

6. **Performance Considerations**

7. **Security Considerations**

8. **Testing Strategy** - Summary of what to test

Use code blocks for interfaces and schemas.
```

---

### Prompt: Generate Dev Tasks

Use to break down technical design into executable work.

```markdown
Break down this technical design into atomic development tasks:

## Technical Design
{{tech-design.md}}

## Context
Each task should be:
- Completable in 30-60 minutes
- Specific enough for an AI assistant to implement
- Include clear acceptance criteria
- Reference the relevant design section

Please generate a dev-tasks.md with:

For each task:
1. **Task ID** (TASK-001, etc.)
2. **Title** (clear, action-oriented)
3. **Status** (Not Started/In Progress/Complete)
4. **Priority** (P0/P1/P2)
5. **Estimated Time**
6. **Dependencies** (other task IDs if any)
7. **Context Files** - Which docs to share with AI
8. **Task Description** - Detailed implementation instructions
9. **Acceptance Criteria** - Checkboxes

Group tasks logically (Foundation, Integration, Polish).
Include a progress tracker table at the end.
```

---

## Code Generation

### Prompt: Implement Component

Standard prompt for creating a new component.

```markdown
Create a React component based on these specifications:

## Component: {{COMPONENT_NAME}}

## Purpose
{{WHAT_IT_DOES}}

## Props
{{tech-design.md → props interface}}

## Behavior
{{KEY_INTERACTIONS_AND_STATES}}

## Styling Approach
{{CSS_MODULES_OR_OTHER}}

## Existing Patterns
{{SIMILAR_COMPONENT_CODE_IF_EXISTS}}

Please provide:
1. Component file ({{COMPONENT_NAME}}.jsx)
2. Styles file ({{COMPONENT_NAME}}.module.css)
3. Index file (index.js)

Follow these conventions:
- Functional components with hooks
- Destructure props
- Handle loading/error/empty states
- Include PropTypes or JSDoc types
- Basic accessibility (semantic HTML, ARIA)
```

---

### Prompt: Implement Feature

Comprehensive prompt for a larger piece of work.

```markdown
Implement this feature:

## Task
{{dev-tasks.md → specific task}}

## Technical Design
{{tech-design.md → relevant sections}}

## Current Code
{{EXISTING_RELATED_CODE}}

## What Already Exists
{{system-state.md → relevant parts}}

Please implement this with:
1. All necessary files
2. Following existing patterns in the codebase
3. Proper error handling
4. Loading states where appropriate
5. TypeScript types or JSDoc comments

After implementation, explain:
- Any deviations from the design
- Any decisions you made that I should document
- Any follow-up work needed
```

---

### Prompt: Fix Bug

Structured prompt for debugging.

```markdown
I need help fixing a bug.

## Bug Description
{{bug-log.md → bug entry OR describe the issue}}

## Reproduction Steps
1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}

## Expected Behavior
{{EXPECTED}}

## Actual Behavior
{{ACTUAL}}

## Error Messages
{{ERROR_OUTPUT}}

## Relevant Code
{{CODE_FILES}}

## What I've Tried
{{ATTEMPTED_SOLUTIONS}}

Please:
1. Identify the root cause
2. Provide a fix
3. Explain why the bug occurred
4. Suggest how to prevent similar bugs
```

---

### Prompt: Add Tests

Prompt for generating test code.

```markdown
Write tests for this component/function:

## Code to Test
{{CODE}}

## Test Plan Reference
{{test-plan.md → relevant section}}

## Testing Framework
{{JEST_VITEST_RTL_ETC}}

## Test Coverage Goals
- Unit tests for: {{FUNCTIONS_METHODS}}
- Integration tests for: {{USER_FLOWS}}
- Edge cases: {{EDGE_CASES}}

Please provide:
1. Test file with proper naming ([Component].test.js)
2. Descriptive test cases
3. Setup/teardown if needed
4. Mock any external dependencies
5. Comments explaining complex test scenarios
```

---

### Prompt: Code Review

Get AI to review code changes.

```markdown
Please review this code:

## Context
{{WHAT_THIS_CODE_DOES}}

## The Code
{{CODE}}

## Pattern Reference
{{tech-design.md → relevant patterns}}

Please review for:
1. **Correctness** - Does it do what it should?
2. **Performance** - Any obvious issues?
3. **Maintainability** - Is it readable and well-structured?
4. **Edge Cases** - What could break?
5. **Security** - Any vulnerabilities?
6. **Accessibility** - Any issues?

For each issue found:
- Severity (High/Medium/Low)
- Location
- Problem
- Suggested fix
```

---

## Documentation Updates

### Prompt: Update Implementation Log

Use at the end of a session.

```markdown
Help me write an implementation log entry.

## What I Worked On
{{BULLET_POINTS_OF_WORK}}

## Key Decisions Made
{{NOTABLE_DECISIONS}}

## Files Changed
{{FILE_LIST}}

## Any Issues Encountered
{{PROBLEMS_AND_SOLUTIONS}}

Please format this as an entry for implementation-log.md with:
- Date header
- Task reference
- Duration
- What was implemented
- Key decisions (with rationale)
- Deviations from plan
- Files changed
- Notes for future sessions
```

---

### Prompt: Create ADR

Use when making significant decisions.

```markdown
Help me document this architectural decision.

## The Decision
{{WHAT_WE_DECIDED}}

## Context
{{WHAT_PROMPTED_THIS}}

## Options Considered
1. {{OPTION_1}}
2. {{OPTION_2}}
3. {{OPTION_3}}

## Our Choice
{{WHICH_OPTION_AND_WHY}}

Please format as an ADR (Architecture Decision Record) with:
- Title (ADR-XXX: Decision Name)
- Date and status
- Context section
- Decision statement
- Rationale (with comparison table if relevant)
- Consequences (positive and negative)
- Related decisions (if any)
```

---

## Specialized Tasks

### Prompt: Accessibility Audit

```markdown
Audit this component for accessibility:

## Component
{{CODE}}

## Current HTML Output
{{RENDERED_HTML_IF_DIFFERENT}}

Check for:
1. Semantic HTML usage
2. ARIA attributes (correct usage or needed additions)
3. Keyboard navigation
4. Focus management
5. Color contrast considerations
6. Screen reader compatibility
7. Error message associations

For each issue:
- Severity (Critical/Major/Minor)
- WCAG guideline reference
- Current code
- Suggested fix
```

---

### Prompt: Performance Optimization

```markdown
Optimize this code for performance:

## Code
{{CODE}}

## Current Issues
{{KNOWN_PERFORMANCE_PROBLEMS}}

## Constraints
{{LIMITATIONS}}

Please analyze:
1. Unnecessary re-renders
2. Heavy computations that could be memoized
3. Bundle size opportunities
4. Network request optimization
5. Memory leaks

For each optimization:
- Impact (High/Medium/Low)
- Current code
- Optimized code
- Explanation of improvement
```

---

### Prompt: Refactoring

```markdown
Help me refactor this code:

## Current Code
{{CODE}}

## Problems with Current Code
{{ISSUES}}

## Goals
{{REFACTORING_GOALS}}

## Constraints
- Must maintain same external interface
- No new dependencies
- {{OTHER_CONSTRAINTS}}

Please provide:
1. Refactored code
2. Changes explanation
3. Before/after comparison for key parts
4. Any follow-up refactoring to consider
```

---

## Tips for Better AI Interactions

### DO ✅

- **Provide complete context** - More is better than less
- **Be specific** - "Add error handling for network failures" not "make it better"
- **Include examples** - Of existing code patterns to follow
- **Reference documents** - "See tech-design.md section X"
- **Ask for explanations** - "Explain why this approach over alternatives"
- **Iterate** - "That's close, but change X to Y"

### DON'T ❌

- **Ask for entire apps** - Too large, quality drops
- **Accept blindly** - Always review and test
- **Skip context** - Every session needs grounding
- **Be vague** - "Fix the bug" without details
- **Forget to log** - Document what AI helped create

---

## 📎 Related Documents

- [Dev Workflow](./dev-workflow.md)
- [Definition of Done](./definition-of-done.md)
- [Technical Design](../02-features/expense-entry/tech-design.md)
