# Template: Technical Design

> **Purpose:** Define HOW a feature will be implemented  
> **When to create:** After feature-spec is approved  
> **Update frequency:** During design phase, then as architecture changes  
> **Output location:** `02-features/{{feature-name}}/tech-design.md`

---

## LLM Instructions

When filling this template:
1. ASCII diagrams are preferred - they work everywhere and are AI-readable
2. Data models should include all fields including timestamps
3. Component specs should include props interface in TypeScript/JSDoc format
4. File structure should match your project's conventions
5. Include implementation phases - this helps break down into dev-tasks

---

## Template

```markdown
# Technical Design: {{FEATURE_NAME}}

> **Feature:** {{FEATURE_NAME}}  
> **Status:** Draft | Approved  
> **Last Updated:** {{DATE}}  
> **Author:** {{AUTHOR}}

---

## 📐 Architecture Overview

### Component Hierarchy

```
{{PARENT_COMPONENT}}
├── {{CHILD_1}}
│   └── {{SUB_COMPONENT}}
├── {{CHILD_2}}
└── {{CHILD_3}}
```

### Data Flow

```
┌──────────────────────────────────────────────────┐
│                  USER ACTION                      │
└──────────────────────────────────────────────────┘
                         │
                         ▼
┌──────────────────────────────────────────────────┐
│                  UI COMPONENT                     │
└──────────────────────────────────────────────────┘
                         │
                         ▼
┌──────────────────────────────────────────────────┐
│                  STATE/STORE                      │
└──────────────────────────────────────────────────┘
                         │
                         ▼
┌──────────────────────────────────────────────────┐
│                  DATA LAYER                       │
└──────────────────────────────────────────────────┘
```

---

## 📦 Data Models

### {{MODEL_NAME}}

```typescript
interface {{MODEL_NAME}} {
  id: number | string;
  {{FIELD_1}}: {{TYPE}};
  {{FIELD_2}}: {{TYPE}};
  {{FIELD_3}}?: {{TYPE}};  // Optional
  createdAt: string;       // ISO 8601
  updatedAt: string;       // ISO 8601
}
```

### Validation Schema

```typescript
const {{modelName}}Schema = z.object({
  {{FIELD_1}}: z.{{VALIDATOR}}(),
  {{FIELD_2}}: z.{{VALIDATOR}}(),
});
```

---

## 🧩 Component Specifications

### {{COMPONENT_NAME}}

```typescript
interface {{COMPONENT_NAME}}Props {
  {{PROP_1}}: {{TYPE}};
  {{PROP_2}}?: {{TYPE}};
  on{{EVENT}}: ({{PARAMS}}) => void;
}
```

**Behavior:**
- {{BEHAVIOR_1}}
- {{BEHAVIOR_2}}

**Implementation Notes:**
- {{NOTE_1}}

---

## 🛠️ Implementation Approach

### Phase 1: {{PHASE_NAME}} ({{DURATION}})
1. {{TASK_1}}
2. {{TASK_2}}

### Phase 2: {{PHASE_NAME}} ({{DURATION}})
1. {{TASK_1}}
2. {{TASK_2}}

### Phase 3: {{PHASE_NAME}} ({{DURATION}})
1. {{TASK_1}}
2. {{TASK_2}}

---

## 📁 File Structure

```
src/
├── components/
│   └── {{feature}}/
│       ├── {{Component}}/
│       │   ├── {{Component}}.jsx
│       │   ├── {{Component}}.module.css
│       │   └── index.js
├── stores/
│   └── {{store}}.js
├── hooks/
│   └── use{{Hook}}.js
└── utils/
    └── {{utility}}.js
```

---

## ⚡ Performance Considerations

| Concern | Mitigation |
|---------|------------|
| {{CONCERN}} | {{APPROACH}} |

---

## 🔒 Security Considerations

| Risk | Mitigation |
|------|------------|
| {{RISK}} | {{APPROACH}} |

---

## 🧪 Testing Strategy

*See [test-plan.md](./test-plan.md) for details.*

- **Unit tests:** {{WHAT_TO_TEST}}
- **Integration tests:** {{WHAT_TO_TEST}}
- **Manual testing:** {{WHAT_TO_TEST}}

---

## 📎 Related Documents

- [Feature Spec](./feature-spec.md)
- [Dev Tasks](./dev-tasks.md)
- [Test Plan](./test-plan.md)
```
