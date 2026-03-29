# AI OS — Execution Engine for Solo Developers

> A minimal, modular operating system for AI-assisted software development. 10 core agents. Auto-selected by project type. Zero bloat.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Agents](https://img.shields.io/badge/Agents-10%20Core-blue)

---

## 🎯 What is AI OS?

AI OS turns your AI assistant into a coordinated team of 10 specialized agents that execute sequentially, stay focused, and track progress automatically.

**Result:** MVP-focused, production-ready development without chaos.

---

## ⚡ Quick Start (2 minutes)

### 1. Clone
```bash
git clone https://github.com/samirsawarkar/ai-os.git
cd ai-os
```

### 2. Fill CONTEXT.md
```markdown
## Project Name
TodoAPI

## One-Line Description
REST API with JWT auth and Postgres.

## Features (MVP only)
- User register/login
- Create/read/delete todos
- Persist to Postgres
```

### 3. Fill STATE.md
```yaml
Current Phase: 1. Foundation
Current Focus: Database schema + user model
Completed: []
Pending:
  - Database schema
  - User model (register/login)
  - Todo CRUD
  - Review + Deploy
```

### 4. Open your AI editor and paste:
```
Read CONTEXT.md and STATE.md.

You are AI OS. Follow execution engine in AGENTS.md:
1. Read CONTEXT.md → project type
2. Auto-select agents (10 core for REST API)
3. Read STATE.md → current focus
4. Route to responsible agent
5. Execute

/plan
```

That's it. Your AI is now a coordinated team.

---

## 📂 File Structure

```
ai-os/
├── CONTEXT.md        ← Your project (FILL THIS)
├── STATE.md          ← Progress tracker (UPDATE EACH SESSION)
├── PROJECT_PLAN.md   ← Agent selection (AUTO-POPULATED)
│
├── AGENTS.md         ← 10 agents + execution engine
├── COMMANDS.md       ← Command reference
├── RULES.md          ← Architecture standards
├── WORKFLOWS.md      ← Execution loops
│
└── agents/           ← 10 core agents
    ├── planner, architect, engineer, reviewer
    ├── debugger, optimizer, security, database
    ├── backend, devops
```

---

## 🤖 How It Works

### Boot Sequence (Every Session)

```
1. Read CONTEXT.md → confirm project type
2. Read STATE.md → confirm current phase + focus
3. Auto-select agents → based on project type
4. Route Current Focus → to responsible agent
5. Agent executes → does the work
6. Update STATE.md → next task
```

### 10 Core Agents

| Agent | Job |
|---|---|
| **planner** | Sequence work, block scope creep |
| **architect** | System design, tech stack |
| **engineer** | Code implementation |
| **reviewer** | Quality gates, approval |
| **debugger** | Root cause analysis |
| **optimizer** | Performance tuning |
| **security** | Auth, validation, protection |
| **database** | Schema, migrations |
| **backend** | APIs, services, logic |
| **devops** | Docker, deployment |

### Auto-Selection by Project Type

**REST API (Backend-heavy):**
```
✅ planner, architect, engineer, reviewer, backend, database, security, debugger, devops, optimizer
```

**Full-Stack Web:**
```
Same as REST API (remove optimizer until post-MVP)
```

**CLI Tool:**
```
planner, architect, engineer, reviewer, debugger, optimizer
```

**Data Pipeline:**
```
planner, architect, engineer, database, debugger, optimizer, devops
```

---

## 📊 Execution Flow

### /plan
Planner sequences work into executable tasks.

### /build
Engineer implements current task.

### /review
Reviewer gates quality before merge.

### /debug
Debugger finds root cause, engineer fixes.

### /optimize
Optimizer tunes performance (post-MVP only).

---

## 🎓 Best Practices

**✅ DO:**
- Fill CONTEXT.md completely (source of truth)
- Update STATE.md after each session
- Use /review before merging code
- Ship MVP first, optimize later
- Let agents stay focused

**❌ DON'T:**
- Add scope without updating CONTEXT.md
- Skip security reviews
- Ignore CRITICAL issues from reviewer
- Refactor before MVP ships
- Activate unnecessary agents

---

## 📈 Example Timeline: REST API in 5 Days

**Day 1:** architect + database design
**Day 2-3:** backend (user model, todo CRUD)
**Day 4:** reviewer + security audit
**Day 5:** devops (Docker, Railway deploy)

---

## 🐛 Troubleshooting

**"I don't know what to do next"**
→ Check STATE.md: Current Focus field.

**"AI is doing work I didn't ask for"**
→ Update CONTEXT.md constraints/features.

**"Lost work between sessions"**
→ Update STATE.md before ending session.

**"AI gave me broken code"**
→ Run `/review [component]`.

**"Need to fix a bug"**
→ Run `/debug [bug]`.

---

## 📄 License

MIT License — use freely, commercially, modify as needed.

---

## 🚀 Next Steps

1. Clone this repo
2. Fill CONTEXT.md with your project
3. Fill STATE.md with your first phase
4. Open Cursor, ChatGPT, or Claude
5. Paste the boot sequence
6. Run `/plan`
7. Build your MVP

**That's it. Go build.** 🎯

---

*Built for solo developers who want speed, clarity, and quality. Inspired by Unix philosophy: do one thing well.*
