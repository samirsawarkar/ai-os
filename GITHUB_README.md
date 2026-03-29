# AI OS — Modular Agent System for Solo Developers

> A minimal, modular operating system for AI-assisted solo software development. 15 specialized agents. Only the ones you need are active. Zero bloat.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Status](https://img.shields.io/badge/Status-Production%20Ready-brightgreen)
![Python 3.11+](https://img.shields.io/badge/Python-3.11+-blue)

## 🎯 What is AI OS?

AI OS is a **system-of-prompts** framework that turns an AI assistant (Claude, ChatGPT, or any LLM) into a coordinated team of 15 specialized development agents. Instead of asking an AI random questions, you guide it through structured workflows with:

- **Role clarity** — each agent knows its job
- **Scope boundaries** — only agents you activate are used
- **Task sequencing** — work happens in optimal order
- **State tracking** — continuous awareness of what's done/pending
- **Quality gates** — automatic reviews, security checks, and issue blocking

**Result:** You go from "Help me code" → to structured, MVP-focused, production-ready development.

---

## 🚀 Quick Start (5 minutes)

### 1. Clone or Copy the Files
```bash
git clone https://github.com/yourusername/ai-os.git
cd ai-os
```

### 2. Edit Your Project Context
Open `CONTEXT.md` and fill in:
- Project name and description
- What you're building and for whom
- Tech stack (Python, Node.js, etc.)
- Constraints (timeline, budget, team size)

```markdown
## Project Name
MyAwesomeAPI

## One-Line Description
A todo API with JWT auth and Postgres, deployable to Railway.

## Features (MVP)
- [ ] Users can register and login
- [ ] Users can create/read/delete todos
- [ ] Todos are persisted in Postgres
```

### 3. Configure Your Project Plan
Open `PROJECT_PLAN.md` Section 1 and set flags:
```yaml
has_frontend:    false  # API only for now
has_auth:        true   # Need JWT
has_database:    true   # Need Postgres
needs_deploy:    true   # Deploy to Railway
external_apis:   false  # No third-party APIs
```

The system automatically selects the right agents for your project.

### 4. Start Using It
Open your favorite AI editor and paste this into a new chat:

```
Read PROJECT_PLAN.md, CONTEXT.md, and STATE.md carefully.

Activate only the agents listed in PROJECT_PLAN.md Section 3.

You are now an AI Development OS. Your job:
- Follow the boot sequence in AGENTS.md
- Use only active agents
- Update STATE.md after every task
- Run /plan to sequence the work

/plan
```

---

## 🏗️ System Architecture

### File Structure
```
ai-os/
├── CONTEXT.md              ✏️ Your project definition
├── STATE.md                ✏️ Live project state tracker
├── PROJECT_PLAN.md         ✏️ Agent activation engine
│
├── README.md               Documentation
├── AGENTS.md               Master coordinator + boot sequence
├── COMMANDS.md             /plan, /build, /review, /debug, /optimize
├── RULES.md                Coding standards and architecture rules
├── WORKFLOWS.md            5 execution loops
│
└── agents/                 Agent library (15 specialized agents)
    ├── planner.md          → Task sequencing, phase management
    ├── architect.md        → System design, tech decisions
    ├── engineer.md         → Implementation, refactoring
    ├── reviewer.md         → Code quality, logic errors
    ├── debugger.md         → Root cause analysis
    ├── optimizer.md        → Performance optimization
    ├── security.md         → Auth, input validation, data protection
    ├── database.md         → Schema, migrations, queries
    ├── api-designer.md     → REST routes, contracts
    ├── frontend.md         → React/HTML/JS components
    ├── backend.md          → Business logic, services
    ├── devops.md           → Docker, CI/CD, deployment
    ├── tester.md           → Unit tests, integration tests
    ├── performance.md      → Profiling, bottleneck detection
    └── logger.md           → Structured logging, observability
```

### Key Concepts

#### **Boot Sequence** (AGENTS.md)
Every session, the AI assistant:
1. Reads `PROJECT_PLAN.md` → confirms active agents
2. Reads `STATE.md` → understands current phase and focus
3. Activates ONLY agents listed in Section 3
4. Routes tasks to the right agent using Section 4 mapping
5. Updates `STATE.md` after every action

#### **Agent Selection by Project Type**

| Project Type | Agents | Why |
|---|---|---|
| **REST API** | planner, architect, engineer, reviewer, backend, database, api-designer, security, logger | ✅ No UI needed |
| **Full-stack Web** | ↑ + frontend, devops | ✅ Web UI + deployment |
| **CLI Tool** | planner, engineer, reviewer, optimizer | ✅ Minimal scope |
| **Data Pipeline** | planner, architect, engineer, database, performance, logger | ✅ ETL focus |
| **Auth-heavy App** | ↑ + security, tester | ✅ Security-first |

#### **Commands**

| Command | When | Output |
|---|---|---|
| `/plan [feature]` | Start of phase or new feature | Sequenced task list |
| `/build` | Current Focus defined | Complete, runnable code |
| `/review [component]` | After every build | Quality verdict (PASS/BLOCKED) |
| `/debug [bug]` | Bug reported or test fails | Root cause + fix |
| `/optimize [target]` | Post-MVP only | Performance improvements |

#### **Workflows**

1. **Feature Development Loop** — Build → Review → Update State → Next
2. **Bug Fixing Loop** — Classify → Debug → Fix → Review → Resume
3. **System Design Loop** — Architecture → Tech decisions → Schema → Setup
4. **Code Review Loop** — Quality gates → Security checks → Approval
5. **Deployment Loop** — Docker → ENV → Deploy → Monitor

---

## 💡 Use Cases

### Use Case 1: Build a REST API (Fast MVP)
```
1. Fill CONTEXT.md (project scope)
2. Set PROJECT_PLAN.md flags: 
   - has_frontend: false
   - has_database: true
   - has_auth: true
   - needs_deploy: true
3. /plan
4. Follow the agent sequence
5. Deploy in ~3 days
```

### Use Case 2: Full-Stack Web App (MVP + UI)
```
1. Fill CONTEXT.md
2. Set all flags: true
3. /plan
4. System activates all agents
5. Build backend, then frontend, then deploy
```

### Use Case 3: Debug a Production Bug
```
1. Existing project running
2. Bug reported
3. /debug [bug description]
4. debugger + logger agents isolate root cause
5. engineer fixes
6. /review fix
7. Resume normal workflow
```

### Use Case 4: Post-MVP Optimization
```
1. MVP shipped
2. Performance problem identified
3. Activate optimizer + performance agents in PROJECT_PLAN.md
4. /optimize [slow component]
5. Get exact improvements with before/after code
```

---

## 🛠️ Using AI OS in Your Favorite Editor

### **With Cursor (Recommended)**

1. **Create a new Cursor project:**
   ```bash
   mkdir my-project
   cd my-project
   git clone https://github.com/yourusername/ai-os.git ./ai-os-templates
   cp -r ai-os-templates/* .
   ```

2. **Open Cursor and create a new chat:**
   - Click "+" to start a new chat
   - Paste this prompt:
   ```
   I'm using AI OS, a modular agent system for development.
   
   The files PROJECT_PLAN.md, CONTEXT.md, STATE.md, and AGENTS.md 
   define a team of 15 AI agents.
   
   Please read these files and follow the boot sequence in AGENTS.md.
   
   Then run: /plan
   ```

3. **Follow along as Cursor runs the workflow**
   - Cursor will sequence your work
   - You implement, it reviews
   - STATE.md updates automatically
   - Chat stays in context

4. **For subsequent builds:**
   ```
   /build
   ```

5. **For reviews and debugging:**
   ```
   /review [component]
   /debug [bug]
   ```

### **With ChatGPT (Web or API)**

1. **Create a new chat**

2. **Upload or paste your files:**
   - In ChatGPT: use "Attach files" to upload CONTEXT.md, PROJECT_PLAN.md, STATE.md
   - Or: paste the content directly in your message

3. **Paste the boot sequence:**
   ```
   I'm using the AI OS framework for development.
   Here's my project context, plan, and current state:
   
   [paste CONTEXT.md]
   [paste PROJECT_PLAN.md]
   [paste STATE.md]
   
   Follow the boot sequence in AGENTS.md, then run /plan.
   ```

4. **After each session, copy the updated STATE.md** and save it to your local file

### **With Claude (Anthropic)**

1. **Create a new conversation** on claude.ai or use the API

2. **Paste your framework files:**
   ```
   I'm using a system called AI OS. Read these files:
   
   [copy-paste all files starting with CONTEXT.md, PROJECT_PLAN.md, STATE.md, AGENTS.md]
   ```

3. **Start with:**
   ```
   Boot sequence: read PROJECT_PLAN.md, activate agents, run /plan
   ```

4. **Use commands:**
   ```
   /build
   /review
   /debug [issue]
   ```

### **With VS Code + Copilot Chat**

1. **Open VS Code**

2. **Open Copilot Chat** (Cmd+Shift+I or Ctrl+Shift+I)

3. **Paste this:**
   ```
   @workspace I'm using AI OS. Let's start:
   
   Read PROJECT_PLAN.md, CONTEXT.md, STATE.md
   Follow boot sequence in AGENTS.md
   Run /plan
   ```

4. **For each task:**
   ```
   @workspace /build
   @workspace /review [component]
   ```

5. **After each chat, save the updated STATE.md**

### **With Any LLM (Self-Hosted or API)**

The framework works with **any LLM API**. Just:

1. Create a system prompt with your AI OS files
2. Send tasks as user messages
3. Parse the LLM response and update STATE.md manually
4. Feed updated STATE.md to the next prompt

Example system prompt:
```
You are an AI Development OS with 15 specialized agents.

Always:
1. Read PROJECT_PLAN.md and STATE.md first
2. Use only active agents from PROJECT_PLAN.md Section 3
3. Follow the workflow in WORKFLOWS.md
4. Update STATE.md after every response

Files:
[paste all markdown files here]

Boot sequence: start with /plan
```

---

## 📋 Project Setup Example

Here's what a filled-in project looks like:

### CONTEXT.md (Filled)
```markdown
## Project Name
TodoAPI

## One-Line Description
A REST API for task management with JWT auth, Postgres storage, and Railway deployment.

## Features (MVP)
- [ ] User registration and login (JWT)
- [ ] Create, read, update, delete todos
- [ ] Todos linked to authenticated users
- [ ] Todos persisted in Postgres

## Tech Stack
| Layer | Choice | Reason |
|---|---|---|
| Language | Python 3.11 | FastAPI is excellent for APIs |
| Framework | FastAPI | Async, auto-docs, excellent for solo dev |
| Database | PostgreSQL | Scalable, can move from SQLite → Postgres |
| Auth | JWT (PyJWT) | Stateless, easy to verify |
| Deployment | Railway | Easy Postgres + Python + auto-deploys |

## Constraints
- Solo developer
- MVP in 5 days
- $0 spend initially
- PostgreSQL must be compatible
```

### PROJECT_PLAN.md Section 1 (Filled)
```yaml
project_name: TodoAPI
description: >
  REST API for task management. Users register, login, create/manage todos.
  Todos persist in Postgres. Deploy to Railway.

features:
  - "User registration and login"
  - "Create, read, update, delete todos"
  - "Todos linked to authenticated users"

constraints:
  - "Solo developer"
  - "MVP in 5 days"
  - "$0 spend initially"

has_frontend:    false
has_auth:        true
has_database:    true
needs_deploy:    true
external_apis:   false
```

### PROJECT_PLAN.md Section 3 (Auto-Derived)
```
ACTIVE AGENTS FOR THIS PROJECT:
  ✅ planner        — task sequencing
  ✅ architect      — system design
  ✅ engineer       — implementation
  ✅ reviewer       — code quality
  ✅ backend        — business logic
  ✅ database       — schema + migrations
  ✅ api-designer   — REST routes
  ✅ security       — auth + input validation
  ✅ logger         — observability
  ✅ devops         — Docker + deployment

  INACTIVE:
  ⛔ frontend       — no UI needed
  ⛔ optimizer      — post-MVP
  ⛔ performance    — post-MVP
  ⛔ tester         — phase 3+
  ⛔ debugger       — on-demand
```

---

## 🎓 Best Practices

### ✅ Do:
- **Fill CONTEXT.md completely** — it's the source of truth
- **Keep PROJECT_PLAN.md updated** — especially Section 3 (active agents)
- **Update STATE.md after every session** — so next session picks up cleanly
- **Use /review for quality gates** — block CRITICAL issues before moving on
- **Activate agents gradually** — don't turn on everything upfront
- **Ship MVP fast** — defer optimization and polish

### ❌ Don't:
- **Don't ask the AI to add scope** — only Planner can do that
- **Don't skip security reviews** — Security agent must check auth/input/data
- **Don't ignore CRITICAL issues** — fix them before continuing
- **Don't refactor while fixing bugs** — change only what's broken
- **Don't optimize before MVP ships** — wait for phase 5+
- **Don't activate agents you don't need** — keeps prompt focused and fast

---

## 📊 Expected Development Timeline

### Example: REST API with Auth
| Phase | Duration | Tasks | Agents |
|---|---|---|---|
| **1. Foundation** | Day 1 | Project setup, DB connection, migrations | architect, database |
| **2. Auth** | Day 1-2 | User model, register, login, middleware | backend, api-designer, security |
| **3. Core Features** | Day 2-3 | Todo model, CRUD routes, business logic | backend, api-designer |
| **4. Hardening** | Day 4 | Review, security audit, logging setup | reviewer, security, logger |
| **5. Deploy** | Day 4-5 | Docker, env setup, Railway deploy | devops |
| **Post-MVP** | Day 6+ | Optimization, tests, additional features | optimizer, tester, performance |

---

## 🐛 Troubleshooting

### "I'm confused about what to do next"
→ Check STATE.md: Current Focus field. That's your next task. If blank, run `/plan`.

### "The AI is doing work I didn't ask for"
→ Open PROJECT_PLAN.md and check Section 3. An unwanted agent is active. Deactivate it.

### "Work isn't being saved between sessions"
→ Update STATE.md before ending your session. Copy it to your local file. Paste it back at the start of next session.

### "I want to add a new feature"
→ Add it to STATE.md Pending list, then run `/plan [feature name]`.

### "The AI gave me broken code"
→ Run `/review [component]`. Reviewer agent will catch and block CRITICAL issues.

### "I need to fix a bug"
→ Run `/debug [bug description]`. Debugger will isolate root cause, engineer will fix.

---

## 🤝 Contributing

Found a bug? Have an idea for a new agent? Want to improve workflows?

1. Fork the repo
2. Create a feature branch
3. Make your changes (add agent, improve workflow, etc.)
4. Open a pull request

---

## 📄 License

MIT License — use freely, commercially, modify as needed. See LICENSE file.

---

## 🙏 Acknowledgments

Built for solo developers who want:
- **Speed** — get to MVP fast
- **Quality** — automated reviews and gates
- **Clarity** — know who's doing what
- **Scale** — from prototype to production

---

## 💬 Support

- **Questions?** Open an issue on GitHub
- **Ideas?** Start a discussion
- **Found a bug?** Open an issue with details

---

## 🚀 Next Steps

1. **Clone this repo** or copy the files
2. **Fill in CONTEXT.md** with your project
3. **Edit PROJECT_PLAN.md Section 1** with your flags
4. **Open your favorite AI editor** (Cursor recommended)
5. **Paste the boot sequence** and run `/plan`
6. **Follow the agent workflow** and build your MVP

**Happy building! 🎯**

---

*Created by solo developers, for solo developers. Inspired by Unix philosophy: do one thing well.*
