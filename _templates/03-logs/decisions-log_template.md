# Template: Decisions Log

> **Purpose:** Record architectural and product decisions with rationale  
> **When to create:** At project start  
> **Update frequency:** When significant decisions are made  
> **Output location:** `03-logs/decisions-log.md`

---

## LLM Instructions

When filling this template:
1. Use ADR (Architecture Decision Record) format
2. Context is critical - explain what prompted the decision
3. List ALL options considered, not just the chosen one
4. Include consequences - both positive and negative
5. Decisions can be superseded - update status when this happens
6. This prevents re-litigating the same decisions

---

## Template

```markdown
# Decisions Log

> **Project:** {{PROJECT_NAME}}  
> **Purpose:** Record architectural and product decisions with rationale  
> **Format:** ADR (Architecture Decision Record)

---

## How to Use This Log

When making a significant decision:
1. Create a new ADR entry
2. Document context, options, and chosen approach
3. Explain consequences (positive and negative)
4. Update status as decisions are implemented or superseded

---

## Active Decisions

### ADR-001: {{DECISION_TITLE}}

**Date:** {{DATE}}  
**Status:** ✅ Accepted | 🟡 Proposed | ⏸️ Superseded  
**Decision Makers:** {{WHO_DECIDED}}

#### Context

*What prompted this decision?*

{{CONTEXT}}

#### Options Considered

1. **{{OPTION_1}}**
   - Pros: {{PROS}}
   - Cons: {{CONS}}

2. **{{OPTION_2}}**
   - Pros: {{PROS}}
   - Cons: {{CONS}}

3. **{{OPTION_3}}**
   - Pros: {{PROS}}
   - Cons: {{CONS}}

#### Decision

We chose **{{CHOSEN_OPTION}}**.

#### Rationale

{{WHY_THIS_OPTION}}

| Criteria | {{OPTION_1}} | {{OPTION_2}} | {{OPTION_3}} |
|----------|--------------|--------------|--------------|
| {{CRITERION}} | {{SCORE}} | {{SCORE}} | {{SCORE}} |

#### Consequences

**Positive:**
- {{POSITIVE_1}}
- {{POSITIVE_2}}

**Negative:**
- {{NEGATIVE_1}}

**Mitigations:**
- {{MITIGATION}}

---

### ADR-002: {{DECISION_TITLE}}

**Date:** {{DATE}}  
**Status:** ✅ Accepted  
**Decision Makers:** {{WHO}}

#### Context
{{CONTEXT}}

#### Decision
{{DECISION}}

#### Rationale
{{WHY}}

#### Consequences
{{CONSEQUENCES}}

---

## Proposed Decisions

### ADR-XXX: {{DECISION_TITLE}}

**Date:** {{DATE}}  
**Status:** 🟡 Proposed  

#### Context
{{CONTEXT}}

#### Options
{{OPTIONS}}

#### Recommendation
{{LEANING_TOWARD}}

#### Open Questions
- {{QUESTION}}

---

## Superseded Decisions

*Decisions that were made but later changed.*

### ADR-XXX: {{TITLE}} (Superseded by ADR-YYY)

{{BRIEF_SUMMARY}}

---

## ADR Template

*Copy this for new decisions:*

```
### ADR-XXX: [Title]

**Date:** YYYY-MM-DD
**Status:** ✅ Accepted | 🟡 Proposed
**Decision Makers:** [Names]

#### Context
[What prompted this decision?]

#### Options Considered
1. [Option 1]
2. [Option 2]

#### Decision
We chose [option].

#### Rationale
[Why this option over others?]

#### Consequences
**Positive:** [Benefits]
**Negative:** [Drawbacks]
**Mitigations:** [How we'll handle negatives]
```

---

## 📎 Related Documents

- [Implementation Log](./implementation-log.md)
- [Assumptions](../00-context/assumptions.md)
- [Technical Designs](../02-features/)
```
