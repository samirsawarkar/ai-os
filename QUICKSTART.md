# Quick Start Template

This file shows a minimal example to get started.

```bash
# 1. Create project
mkdir my-awesome-api
cd my-awesome-api

# 2. Initialize git
git init

# 3. Copy AI OS framework files
# (Download from GitHub or copy from this directory)

# 4. Edit CONTEXT.md
# Fill in: project name, features, tech stack

# 5. Edit PROJECT_PLAN.md Section 1
# Set your flags: has_frontend, has_auth, etc.

# 6. Initialize Git
git add .
git commit -m "Initial: AI OS framework setup"

# 7. Open Cursor
cursor .

# 8. In Cursor chat:
# Paste the boot sequence from this template
```

---

## Boot Sequence (Copy This to Cursor Chat)

```
I'm using AI OS, a modular agent system for development.

These files define my project setup:

**CONTEXT.md** — Project definition
**PROJECT_PLAN.md** — Agent configuration  
**STATE.md** — Current state
**AGENTS.md** — Boot sequence and master coordinator

Please follow this process:

1. Read all four files carefully
2. Extract Section 3 from PROJECT_PLAN.md → List of active agents
3. Extract Section 4 from PROJECT_PLAN.md → Task to agent mapping
4. Read STATE.md → Confirm current phase and pending components
5. Boot and activate ALL agents listed in Section 3 (ignore others)
6. Use Section 4 to route each task to the correct agent
7. After every action, update STATE.md accordingly

Important constraints:
- Only use agents marked ✅ in PROJECT_PLAN.md Section 3
- Ignore all agents marked ⛔ (inactive for this project)
- Follow RULES.md for coding standards
- Follow WORKFLOWS.md for execution flow
- Use COMMANDS.md for available commands

Let's begin the boot sequence. /plan
```

---

## Project File Templates

### CONTEXT.md Minimal Example

```markdown
# CONTEXT.md — Project Definition

## Project Name
TodoAPI

## One-Line Description
A REST API for todo management with JWT auth and PostgreSQL.

## Problem
Users need a way to manage their tasks with persistent storage.

## Goals (MVP only)
- [ ] User registration and login
- [ ] Create, read, update, delete todos
- [ ] Todos persisted in PostgreSQL

## Tech Stack
| Layer | Choice | Reason |
|---|---|---|
| Language | Python 3.11 | Excellent for API dev |
| Framework | FastAPI | Async, auto-docs, fast |
| Database | PostgreSQL | Scalable, production-ready |
| Auth | JWT | Stateless authentication |

## Constraints
- Solo developer
- MVP in 1 week
- $0 initial budget

## Success Criteria
- [ ] User can register and login
- [ ] User can CRUD todos
- [ ] System is deployable to production
```

### PROJECT_PLAN.md Minimal Example

```markdown
# PROJECT_PLAN.md

## SECTION 1 — Project Input

```yaml
project_name: TodoAPI
description: >
  REST API for task management. Users register, login, 
  create/manage todos. Deploy to Railway.

has_frontend:    false
has_auth:        true
has_database:    true
needs_deploy:    true
external_apis:   false
```

## SECTION 3 — Active Agents

```
ACTIVE AGENTS:
  ✅ planner        — task sequencing
  ✅ architect      — system design
  ✅ engineer       — implementation
  ✅ reviewer       — code quality
  ✅ backend        — business logic
  ✅ database       — schema + migrations
  ✅ api-designer   — REST routes
  ✅ security       — auth validation
  ✅ logger         — structured logging
  ✅ devops         — Docker + deployment

INACTIVE:
  ⛔ frontend       — no UI needed
  ⛔ optimizer      — post-MVP only
  ⛔ performance    — post-MVP only
  ⛔ tester         — phase 3+
  ⛔ debugger       — on-demand
```
```

### STATE.md Minimal Example

```markdown
# STATE.md — Current State

## Current Phase
Phase 1 — Foundation

## Completed Components
(none yet)

## Pending Components
[ ] 1. Project scaffolding
[ ] 2. Database connection + migrations
[ ] 3. User model + authentication
[ ] 4. REST API structure
[ ] 5. Todo model + CRUD endpoints
[ ] 6. Input validation + error handling
[ ] 7. Logging setup
[ ] 8. Code review
[ ] 9. Docker + deployment
[ ] 10. Deploy to Railway

## Current Focus
Project scaffolding

## Last Updated
2024-03-29
```

---

## First Session Checklist

- [ ] Copy AI OS framework files to project
- [ ] Fill in CONTEXT.md completely
- [ ] Update PROJECT_PLAN.md Section 1 flags
- [ ] Initialize git: `git init && git add . && git commit -m "Initial: AI OS setup"`
- [ ] Open Cursor (or your chosen editor)
- [ ] Paste boot sequence from above
- [ ] Follow /plan output
- [ ] Build first component with /build
- [ ] Review with /review
- [ ] Commit progress: `git add . && git commit -m "feat: Phase 1 foundation"`

---

## Commands Cheat Sheet

```
/plan               Start phase, sequence tasks
/build              Implement current task
/review             Check code quality
/debug [error]      Find and fix bug
/optimize [target]  Performance improvement (post-MVP)
/status             Show current state (any time)
```

---

## Next Steps

1. Copy files to your project
2. Fill in CONTEXT.md and PROJECT_PLAN.md
3. Paste boot sequence in your editor
4. Follow the /plan output
5. Execute tasks with /build → /review → commit
6. Update STATE.md after each session
7. Ship your MVP! 🚀

---

**Happy building! Questions? Open an issue on GitHub.**
