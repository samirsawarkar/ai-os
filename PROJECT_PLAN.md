# PROJECT_PLAN.md — Agent Activation Engine
# ✏️ FILL IN SECTION 1. The system will derive everything else.

---

## SECTION 1 — Project Input (YOU FILL THIS)

```yaml
project_name: "[Your project name]"

description: >
  [What are you building? Who is it for? What problem does it solve?
   2–4 sentences is enough.]

features:
  - "[Feature 1]"
  - "[Feature 2]"
  - "[Feature 3]"

constraints:
  - "[Solo developer]"
  - "[Timeline: e.g., 2-week MVP]"
  - "[Budget: e.g., $0 infra initially]"
  - "[Other hard constraints]"

has_frontend:    true   # set false for API-only
has_auth:        true   # set false if no login required
has_database:    true   # set false if no persistence needed
needs_deploy:    true   # set false if local-only for now
external_apis:   false  # set true if calling third-party APIs
```

---

## SECTION 2 — Agent Selection Logic

> The system reads Section 1 and activates the minimum required agents.
> Rules below determine which agents are selected.

### Selection Rules

```
ALWAYS ACTIVE (every project):
  ✅ planner     → every project needs task sequencing
  ✅ engineer    → every project needs implementation
  ✅ reviewer    → every project needs quality checks

CONDITIONAL:
  architect      → activate if: new project OR new major component
  backend        → activate if: has_database OR server-side logic exists
  database       → activate if: has_database = true
  api-designer   → activate if: has_frontend = true OR external consumers exist
  frontend       → activate if: has_frontend = true
  security       → activate if: has_auth = true OR user data is stored
  tester         → activate if: core components are stable (Phase 3+)
  devops         → activate if: needs_deploy = true
  debugger       → activate if: a bug is being investigated
  logger         → activate if: needs_deploy = true OR debugging is difficult
  optimizer      → activate if: MVP is complete AND performance problem measured
  performance    → activate if: MVP is complete AND slowness is observable
```

---

## SECTION 3 — Active Agents (AUTO-DERIVED)

> Replace with your actual derived list after filling Section 1.
> Default below assumes: full-stack web app with auth + deploy.

```
ACTIVE AGENTS FOR THIS PROJECT:
  ✅ planner        — task sequencing, phase management
  ✅ architect      — system design, tech decisions
  ✅ engineer       — implementation
  ✅ reviewer       — code quality, logic errors
  ✅ backend        — service layer, business logic
  ✅ database       — schema, migrations, queries
  ✅ api-designer   — REST contracts, route implementation
  ✅ frontend       — UI components and pages
  ✅ security       — auth hardening, input validation
  ✅ devops         — deployment, Dockerfile, env setup
  ✅ logger         — structured logging, observability

  INACTIVE (not needed for this project):
  ⛔ optimizer      — activates post-MVP only
  ⛔ performance    — activates post-MVP only
  ⛔ tester         — activates Phase 3+
  ⛔ debugger       — activates on-demand for bugs
```

---

## SECTION 4 — Task → Agent Mapping

> Maps every task to the agent(s) responsible.

| Task                          | Primary Agent   | Supporting Agent |
|-------------------------------|-----------------|------------------|
| Define architecture           | `architect`     | `planner`        |
| Design data schema            | `database`      | `architect`      |
| Write migrations              | `database`      | —                |
| Implement auth service        | `backend`       | `security`       |
| Implement auth routes         | `api-designer`  | `backend`        |
| Build core feature logic      | `backend`       | `engineer`       |
| Build core feature routes     | `api-designer`  | —                |
| Build UI pages                | `frontend`      | —                |
| Connect UI to API             | `frontend`      | `api-designer`   |
| Review completed component    | `reviewer`      | `security`       |
| Set up logging                | `logger`        | `devops`         |
| Write Dockerfile              | `devops`        | —                |
| Configure deployment          | `devops`        | —                |
| Fix a reported bug            | `debugger`      | `logger`         |
| Post-MVP optimization         | `optimizer`     | `performance`    |
| Write tests (Phase 3+)        | `tester`        | —                |

---

## SECTION 5 — Phase Plan

```
PHASE 1 — Foundation
  Agents: architect, database, planner
  Goal: system can start without errors
  Tasks:
    [ ] Folder structure + project setup
    [ ] Config + environment variables
    [ ] Database connection + base migration

PHASE 2 — Core Auth
  Agents: backend, api-designer, security, engineer
  Goal: user can register and log in
  Tasks:
    [ ] User model + migration
    [ ] Password hashing + JWT utilities
    [ ] Register + login endpoints
    [ ] Auth middleware for protected routes

PHASE 3 — Core Features
  Agents: backend, api-designer, frontend (if applicable)
  Goal: primary user flow works end-to-end
  Tasks:
    [ ] [Feature 1] — model + service + route
    [ ] [Feature 2] — model + service + route
    [ ] [Feature 3] — model + service + route

PHASE 4 — Hardening
  Agents: reviewer, security, logger, tester
  Goal: no CRITICAL issues, observable in production
  Tasks:
    [ ] Review all components
    [ ] Add structured logging
    [ ] Fix all CRITICAL + HIGH issues
    [ ] Write tests for core flows

PHASE 5 — Launch
  Agents: devops
  Goal: app is live and accessible
  Tasks:
    [ ] Dockerfile + docker-compose
    [ ] Deploy to [Railway / Fly.io / VPS]
    [ ] Smoke test in production
    [ ] Write README
```

---

## SECTION 6 — Agent Coordination Rules

```
1. Read this file before every session
2. Activate ONLY agents listed in Section 3
3. Ignore all other agents — they don't exist for this project
4. Follow Task → Agent Mapping in Section 4
5. Respect phase sequence — don't skip phases
6. Update STATE.md after every task
7. CRITICAL issues from reviewer or security block all forward progress
```
