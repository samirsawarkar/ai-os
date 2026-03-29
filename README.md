# AI Development OS — Modular Agent System

A minimal, modular AI operating system for solo software development.
15 specialized agents. Only the ones you need are active. Zero bloat.

---

## Quick Start

### 1. Fill in your project
Edit `CONTEXT.md` — project description, features, tech stack, constraints.

### 2. Select your agents
Edit `PROJECT_PLAN.md` Section 1 (toggle flags) and Section 3 (active agent list).

### 3. Initialize STATE.md
Update `STATE.md` with your actual Pending Components list.

### 4. Start building
Tell your AI assistant:
> "Read PROJECT_PLAN.md, CONTEXT.md, and STATE.md.
>  Activate only the agents listed in Section 3.
>  Run /plan to start."

---

## File Map

```
ai-system/
│
├── CONTEXT.md          ✏️ YOU EDIT — project definition, goals, stack
├── STATE.md            ✏️ YOU EDIT — live tracker (phase, tasks, decisions)
│
├── PROJECT_PLAN.md     ✏️ YOU EDIT Section 1 — agent activation engine
├── AGENTS.md           🔒 FIXED — master coordinator, boot sequence
├── COMMANDS.md         🔒 FIXED — /plan /build /review /debug /optimize
├── RULES.md            🔒 FIXED — coding law, architecture rules
├── WORKFLOWS.md        🔒 FIXED — 5 execution loops
│
└── agents/             🔒 FIXED — agent library (activate via PROJECT_PLAN.md)
    ├── planner.md
    ├── architect.md
    ├── engineer.md
    ├── reviewer.md
    ├── debugger.md
    ├── optimizer.md
    ├── security.md
    ├── database.md
    ├── api-designer.md
    ├── frontend.md
    ├── backend.md
    ├── devops.md
    ├── tester.md
    ├── performance.md
    └── logger.md
```

---

## Agent Selection by Project Type

| Project Type          | Activate These Agents                                                    |
|-----------------------|--------------------------------------------------------------------------|
| API only (no UI)      | planner, architect, engineer, reviewer, backend, database, api-designer, security, logger |
| Full-stack web app    | All of the above + frontend, devops                                      |
| CLI tool              | planner, engineer, reviewer, optimizer                                   |
| Data pipeline         | planner, architect, engineer, reviewer, database, performance, logger    |
| Auth-heavy app        | Add security (mandatory), tester (Phase 3+)                             |
| Post-MVP optimization | Add optimizer, performance (never before MVP ships)                      |

---

## Commands

| Command              | Agents Used                          | When                        |
|----------------------|--------------------------------------|-----------------------------|
| `/plan [feature]`    | planner + architect                  | Start of phase or feature   |
| `/build`             | engineer + layer agents              | Current Focus is defined    |
| `/review`            | reviewer + security                  | After every build           |
| `/debug [bug]`       | debugger + logger                    | Bug reported                |
| `/optimize [target]` | optimizer + performance              | Post-MVP only               |
| `/status`            | (reads files only)                   | Anytime                     |

---

## Core Principle

> Activate the minimum agents needed.
> Build the minimum features required.
> Ship. Then improve.
