# Template: Insights & Learnings

> **Purpose:** Capture lessons learned and ideas for improvement  
> **When to create:** At project start  
> **Update frequency:** Ongoing, especially after sprints and releases  
> **Output location:** `03-logs/insights.md`

---

## LLM Instructions

When filling this template:
1. Document patterns to REPEAT and patterns to AVOID
2. Include code patterns that worked well (with examples)
3. Feature ideas should include rough value/effort estimates
4. Retrospective notes should lead to actionable improvements
5. This is the team's learning journal - encourage honest reflection

---

## Template

```markdown
# Insights & Learnings

> **Project:** {{PROJECT_NAME}}  
> **Purpose:** Capture lessons learned and ideas for improvement  
> **Update Frequency:** Ongoing

---

## How to Use This Document

This is your project's learning journal. Capture:
- What worked well (patterns to repeat)
- What didn't work (mistakes to avoid)
- Ideas for the future
- Technical discoveries

Review during retrospectives and when starting similar projects.

---

## Technical Insights

### What Worked Well

#### 🟢 {{TECHNIQUE_OR_PATTERN}}

**Context:** {{WHY_WE_DID_THIS}}  
**Learning:** {{WHAT_WE_LEARNED}}

**Pattern to Repeat:**
```{{LANGUAGE}}
{{CODE_EXAMPLE}}
```

**When to Use Again:**
- {{SITUATION_1}}
- {{SITUATION_2}}

---

#### 🟢 {{TECHNIQUE_OR_PATTERN}}

**Context:** {{CONTEXT}}  
**Learning:** {{LEARNING}}

---

### What Didn't Work

#### 🔴 {{PROBLEM}}

**Context:** {{WHAT_WE_TRIED}}  
**Problem:** {{WHAT_WENT_WRONG}}  
**Solution:** {{HOW_WE_FIXED_IT}}

**Lesson:** {{TAKEAWAY}}

**Time Lost:** {{ESTIMATE}}

---

#### 🔴 {{PROBLEM}}

**Context:** {{CONTEXT}}  
**Problem:** {{PROBLEM}}  
**Lesson:** {{LESSON}}

---

## Process Insights

### What Worked Well

#### 🟢 {{PROCESS_OR_PRACTICE}}

**Learning:** {{INSIGHT}}

---

### What Didn't Work

#### 🔴 {{PROCESS_PROBLEM}}

**Problem:** {{DESCRIPTION}}  
**Solution:** {{FIX}}

---

## Feature Ideas for Future

### Near-term (Next Version)

| Idea | Value | Effort | Notes |
|------|-------|--------|-------|
| {{IDEA}} | High/Medium/Low | High/Medium/Low | {{NOTES}} |

### Long-term (Future Versions)

| Idea | Value | Effort | Notes |
|------|-------|--------|-------|
| {{IDEA}} | High/Medium/Low | High/Medium/Low | {{NOTES}} |

---

## Retrospective Notes

### Sprint {{N}} Retro ({{DATE}})

**What went well:**
- {{POSITIVE}}

**What to improve:**
- {{IMPROVEMENT}}

**Action items:**
- [ ] {{ACTION}}

---

## Knowledge Base

### Useful Code Patterns

#### {{PATTERN_NAME}}
```{{LANGUAGE}}
{{CODE}}
```

### External Resources

- [{{TITLE}}]({{URL}})
- [{{TITLE}}]({{URL}})

---

## Quotes & Testimonials

> "{{QUOTE}}"  
> — {{SOURCE}}

---

## Entry Template

*Copy this for new insights:*

```
#### 🟢/🔴 [Title]

**Context:** [Why we did this]
**Learning:** [What we learned]

**Pattern/Lesson:** [Takeaway]
```

---

## 📎 Related Documents

- [Assumptions](../00-context/assumptions.md)
- [Decisions Log](./decisions-log.md)
- [Validation Log](./validation-log.md)
```
