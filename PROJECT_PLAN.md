# PROJECT_PLAN.md — Agent Selection

> Read AGENTS.md EXECUTION ENGINE section for auto-selection rules.
> This file shows which agents are active for your project.

---

## Section 1: Your Project Definition

Fill in CONTEXT.md instead (this is the single source of truth).

Refer to AGENTS.md AUTO-SELECTION RULES to see which agents activate for your project type.

---

## Section 2: Auto-Selected Agents (Derived)

**Your project type determines which agents activate.**

See AGENTS.md for full auto-selection rules by project type:
- REST API
- Full-Stack Web
- CLI Tool
- Data Pipeline
- Microservices

---

## Section 3: Task Routing

Each Current Focus maps to a responsible agent:

| Current Focus | Primary Agent | Support |
|---|---|---|
| Design system architecture | architect | none |
| Implement feature | engineer | none |
| Review code quality | reviewer | security (if auth-related) |
| Debug production issue | debugger | engineer (for fixes) |
| Optimize performance | optimizer | engineer (for implementation) |
| Deploy to production | devops | none |

---

## Section 4: How to Use This File

1. **Read AGENTS.md** → understand auto-selection rules
2. **Define your project type** in CONTEXT.md (REST API, Web app, CLI, etc.)
3. **Agents auto-activate** based on project type
4. **Check STATE.md** for Current Focus
5. **Route to responsible agent** from Section 3 table above
6. **Execute** → agent does the work
7. **Update STATE.md** when done

---

**No manual toggles. No confusion. Just work.**
