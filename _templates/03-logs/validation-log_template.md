# Template: Validation Log

> **Purpose:** Track post-release observations and user feedback  
> **When to create:** Before first release  
> **Update frequency:** After releases and during production monitoring  
> **Output location:** `03-logs/validation-log.md`

---

## LLM Instructions

When filling this template:
1. Track observations from actual users, not just internal testing
2. Metrics should be compared against targets from vision.md
3. Include both quantitative data and qualitative feedback
4. Document incidents with timeline format
5. Feed insights back into assumptions.md and insights.md

---

## Template

```markdown
# Validation Log

> **Project:** {{PROJECT_NAME}}  
> **Purpose:** Track production observations and user feedback  
> **Update Frequency:** After releases and during monitoring

---

## How to Use This Log

After deploying to production or beta:
1. Document observations from real usage
2. Track metrics against targets
3. Record user feedback themes
4. Log any incidents
5. Feed learnings back into planning

---

## Pre-Release Validation

### Internal Beta (v{{VERSION}}) - {{DATE}}

**Participants:** {{N}} team members for {{DURATION}}  
**Environment:** {{ENVIRONMENT}}

#### Goals

- [ ] {{GOAL_1}}
- [ ] {{GOAL_2}}
- [ ] {{GOAL_3}}

#### Observations

| Day | Observer | Observation | Action |
|-----|----------|-------------|--------|
| {{N}} | {{NAME}} | {{OBSERVATION}} | {{ACTION}} |

#### Summary

**Blockers Found:** {{N}}  
**Bugs Found:** {{N}} (logged in bug-log.md)  
**UX Improvements Suggested:** {{N}}  
**Ready for Next Phase:** Yes/No

---

## Post-Release Validation

### v{{VERSION}} Release - {{DATE}}

#### Launch Metrics (Day 1)

| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| {{METRIC}} | {{TARGET}} | {{ACTUAL}} | ✅/⚠️/❌ |

#### Week 1 Observations

{{KEY_PATTERNS_NOTICED}}

#### User Feedback Themes

| Theme | Frequency | Sentiment | Action |
|-------|-----------|-----------|--------|
| {{THEME}} | {{HOW_OFTEN}} | Positive/Neutral/Negative | {{ACTION}} |

---

## Metrics Tracking

### Key Performance Indicators

| Metric | Target | W1 | W2 | W3 | W4 | Status |
|--------|--------|----|----|----|----|--------|
| {{METRIC}} | {{TARGET}} | - | - | - | - | - |

---

## A/B Test Results

### Test {{N}}: {{TEST_NAME}}

**Status:** 📋 Planned | 🔄 Running | ✅ Complete  
**Hypothesis:** {{HYPOTHESIS}}  
**Variants:**
- A: {{CONTROL}}
- B: {{VARIANT}}  
**Metric:** {{WHAT_WE_MEASURE}}

**Results:** {{OUTCOME}}

---

## Incident Log

### INC-001: {{INCIDENT_TITLE}}

**Date:** {{DATE}}  
**Severity:** Critical | High | Medium  
**Duration:** {{HOURS}}  
**Impact:** {{USERS_AFFECTED}}

#### Timeline

| Time | Event |
|------|-------|
| {{TIME}} | Issue detected |
| {{TIME}} | Investigation started |
| {{TIME}} | Root cause identified |
| {{TIME}} | Fix deployed |
| {{TIME}} | Verified resolved |

#### Root Cause
{{ROOT_CAUSE}}

#### Resolution
{{RESOLUTION}}

#### Prevention
{{PREVENTION_MEASURES}}

---

## User Interview Summary

### Interview {{N}} - {{DATE}}

**Participant:** {{PERSONA}} ({{AGE}}, {{PROFILE}})  
**Duration:** {{MINUTES}} minutes

#### Key Quotes

> "{{QUOTE}}"

#### Observations

- {{OBSERVATION}}

#### Insights

- {{ACTIONABLE_INSIGHT}}

---

## Release Validation Checklist

*Copy for each release:*

```
### v{{VERSION}} Validation

#### Pre-Launch
- [ ] All acceptance criteria verified
- [ ] Cross-browser testing complete
- [ ] Performance benchmarks met
- [ ] Accessibility audit passed

#### Launch
- [ ] Deployment successful
- [ ] Health checks passing
- [ ] No error spikes

#### Post-Launch (Day 1)
- [ ] Core flows working
- [ ] No critical bugs
- [ ] Performance stable

#### Post-Launch (Week 1)
- [ ] User feedback reviewed
- [ ] Metrics meet targets
- [ ] Insights documented
```

---

## 📎 Related Documents

- [Bug Log](./bug-log.md)
- [Insights](./insights.md)
- [Assumptions](../00-context/assumptions.md)
```
