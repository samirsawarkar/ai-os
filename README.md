# AI OS — Turn AI Into a Real Dev Team

> **AI that executes, not just responds.**

Most AI tools give you answers.

This gives you **execution**.

AI OS is a modular agent system that forces AI to:
- ✅ **Stay focused** — one task at a time, no scope creep
- ✅ **Follow workflows** — predictable, repeatable execution
- ✅ **Track progress** — never lose work between sessions
- ✅ **Ship MVPs faster** — from idea to deployed in days

**Built for solo developers who want speed without chaos.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Agents](https://img.shields.io/badge/Agents-10%20Core-blue)

---

## 🤔 Why This Exists

AI is powerful but inconsistent.

**The problem:**
- ❌ It forgets context between messages
- ❌ It over-engineers simple problems
- ❌ It goes off track (scope creep)
- ❌ You lose work if you don't copy/paste carefully

**The solution:**
AI OS fixes this by turning AI into a **structured system**:
- ✅ Boot sequence reads state every session
- ✅ Quality gates prevent overengineering
- ✅ Execution rules enforce discipline
- ✅ Version + memory track everything

**Result: AI that actually ships MVPs.**

---

## 🚀 What You Can Build

| What | Timeline | With AI OS |
|---|---|---|
| REST API (JWT + Postgres) | 5 days | ✅ Proven |
| Full-stack web app | 2-3 weeks | ✅ Proven |
| Large system without chaos | Scalable | ✅ Proven |

**Tested on real projects.** Not theory.

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

## 🤖 How It Works (The Discipline)

### Boot Sequence (Every Session)

**AI that executes follows this:**

```
1. Read CONTEXT.md → confirm project type
2. Read STATE.md → confirm current phase + focus
3. Read MEMORY.md → apply past learnings
4. Read VERSION.md → understand system maturity
5. Auto-select agents → based on project type
6. Route Current Focus → to responsible agent
7. Execute task → follow EXECUTION_RULES
8. Pass quality gate → 6-point checklist
9. Update STATE.md, MEMORY.md, VERSION.md → track everything
10. STOP execution → wait for /plan, don't auto-continue
```

**Result: AI that stays focused and ships code.**

### 10 Core Agents

| Agent | Does |
|---|---|
| **planner** | Sequences work, blocks scope creep |
| **architect** | System design, tech decisions |
| **engineer** | Implementation, follows patterns |
| **reviewer** | Quality gates, approvals |
| **debugger** | Root cause analysis |
| **optimizer** | Post-MVP performance (blocked until ready) |
| **security** | Auth, validation, protection |
| **database** | Schema, migrations, queries |
| **backend** | APIs, business logic, services |
| **devops** | Docker, deployment, infrastructure |

**Each agent has ONE job. No overlap. Clear authority.**
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

## 💡 Why This Is Different

**Most AI projects fail because:**
- AI rambles (no scope enforcement)
- Every session starts over (no institutional memory)
- Quality gets skipped (no real gates)
- Scope explodes (no priority system)
- Optimization kills momentum (too early)

**AI OS fixes this:**
- CONTEXT.md enforces scope (AI can't add features)
- MEMORY.md enforces learning (patterns + decisions stick)
- EXECUTION_RULES.md enforces quality (6-point gate, not recommendations)
- STATE.md enforces focus (HIGH/MEDIUM/LOW priorities)
- Optimizer guard enforces discipline (no premature optimization)

**Result:** AI becomes a real dev team, not a chatbot.

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

## 🚀 Start Now (2 Minutes)

```bash
git clone https://github.com/samirsawarkar/ai-os.git
cd ai-os
# Fill CONTEXT.md (your project brief)
# Fill STATE.md (current phase + focus)
# Copy AGENTS.md boot sequence → Cursor/ChatGPT/Claude
# Paste. Run /plan. Go.
```

**That's it.**

Your AI now:
- ✅ Understands scope (won't ramble)
- ✅ Remembers decisions (won't repeat)
- ✅ Gates quality (won't ship broken code)
- ✅ Focuses work (won't distract)
- ✅ Respects your timeline (won't overengineer)

**Stop wasting time waiting for AI. Start executing.**

---

*Built for solo developers. Inspired by Unix: do one thing well. Now deploy it.*
