# Template: System State

> **Purpose:** Document what is currently built and running  
> **When to create:** After initial project setup, or when adopting existing project  
> **Update frequency:** After each major change or deployment  
> **Output location:** `00-context/system-state.md`

---

## LLM Instructions

When filling this template:
1. Be specific about versions - "React" is not enough, use "React 18.2.0"
2. Keep file structure current - outdated structure misleads AI
3. Document what's built vs planned vs in-progress clearly
4. Include known issues and tech debt - AI needs to know constraints
5. This is the "snapshot" of reality - keep it honest and current

---

## Template

```markdown
# System State

> **Last Updated:** {{DATE}}  
> **Environment:** Development | Staging | Production  
> **Version:** {{VERSION}}

---

## 🏗️ Current Tech Stack

### Frontend

| Component | Technology | Version | Notes |
|-----------|------------|---------|-------|
| Framework | {{FRAMEWORK}} | {{VERSION}} | {{NOTES}} |
| Build Tool | {{BUILD_TOOL}} | {{VERSION}} | {{NOTES}} |
| Styling | {{STYLING}} | {{VERSION}} | {{NOTES}} |
| State Management | {{STATE_LIB}} | {{VERSION}} | {{NOTES}} |

### Backend (if applicable)

| Component | Technology | Version | Notes |
|-----------|------------|---------|-------|
| Runtime | {{RUNTIME}} | {{VERSION}} | {{NOTES}} |
| Framework | {{FRAMEWORK}} | {{VERSION}} | {{NOTES}} |
| Database | {{DATABASE}} | {{VERSION}} | {{NOTES}} |

### Infrastructure

| Component | Technology | Notes |
|-----------|------------|-------|
| Hosting | {{HOSTING}} | {{NOTES}} |
| CI/CD | {{CI_CD}} | {{NOTES}} |
| Monitoring | {{MONITORING}} | {{NOTES}} |

---

## 📊 What's Built vs Planned

### Core Features

| Feature | Status | Completion | Notes |
|---------|--------|------------|-------|
| {{FEATURE_1}} | ✅ Complete | 100% | {{NOTES}} |
| {{FEATURE_2}} | 🚧 In Progress | {{PERCENT}}% | {{NOTES}} |
| {{FEATURE_3}} | 📋 Planned | 0% | {{NOTES}} |

### Infrastructure

| Component | Status | Notes |
|-----------|--------|-------|
| {{COMPONENT}} | ✅ Complete / 🚧 In Progress / 📋 Planned | {{NOTES}} |

---

## 📁 Current File Structure

```
/{{PROJECT_NAME}}
├── {{FOLDER_1}}/
│   └── {{DESCRIPTION}}
├── {{FOLDER_2}}/
│   └── {{DESCRIPTION}}
├── src/
│   ├── components/
│   ├── pages/
│   ├── stores/
│   ├── utils/
│   └── ...
├── docs/
│   └── (this documentation)
└── {{CONFIG_FILES}}
```

---

## 🗄️ Database Schema (if applicable)

### {{TABLE_NAME}}

```
{
  id: {{TYPE}},
  {{FIELD_1}}: {{TYPE}},
  {{FIELD_2}}: {{TYPE}},
  createdAt: {{TYPE}},
  updatedAt: {{TYPE}}
}
```

### Indexes

- {{INDEX_DESCRIPTION}}

---

## 🌐 Deployment Status

| Environment | URL | Status | Last Deploy |
|-------------|-----|--------|-------------|
| Local Dev | localhost:{{PORT}} | ✅ Active | - |
| Staging | {{URL}} | ✅ Active / 🔴 Not Setup | {{DATE}} |
| Production | {{URL}} | ✅ Active / 🔴 Not Setup | {{DATE}} |

---

## ⚡ Known Issues

### Active Bugs

| ID | Description | Severity | Status |
|----|-------------|----------|--------|
| BUG-{{N}} | {{DESCRIPTION}} | Low/Medium/High | Open |

### Technical Debt

| ID | Description | Priority | Notes |
|----|-------------|----------|-------|
| TD-{{N}} | {{DESCRIPTION}} | Low/Medium/High | {{NOTES}} |

---

## 🔧 Development Environment

### Required

- {{REQUIREMENT_1}} {{VERSION}}
- {{REQUIREMENT_2}} {{VERSION}}

### Local Commands

```bash
# Install dependencies
{{INSTALL_COMMAND}}

# Start development server
{{DEV_COMMAND}}

# Run tests
{{TEST_COMMAND}}

# Build for production
{{BUILD_COMMAND}}
```

---

## 📈 Performance Baseline

| Metric | Current | Target | Notes |
|--------|---------|--------|-------|
| {{METRIC}} | {{CURRENT}} | {{TARGET}} | {{NOTES}} |

---

## 📅 Last Major Changes

| Date | Change | Impact |
|------|--------|--------|
| {{DATE}} | {{CHANGE}} | {{IMPACT}} |

---

## 📎 Related Documents

- [Vision](./vision.md)
- [Assumptions](./assumptions.md)
- [Implementation Log](../03-logs/implementation-log.md)
```
