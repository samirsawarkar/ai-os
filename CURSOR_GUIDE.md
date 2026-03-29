# 🎯 Complete Guide: Using AI OS with Cursor

Cursor is the best editor for using AI OS. This guide shows you exactly how to set it up and use it effectively.

---

## Prerequisites

- [Cursor](https://www.cursor.sh) installed (free or paid)
- AI OS files in your project folder
- Your project configured in CONTEXT.md and PROJECT_PLAN.md

---

## Setup (First Time)

### Step 1: Create a New Cursor Project

```bash
mkdir my-awesome-project
cd my-awesome-project

# Option A: Clone AI OS templates
git clone https://github.com/yourusername/ai-os.git .

# Option B: Copy files manually
# Copy all .md files from ai-os into your project folder
```

### Step 2: Configure Your Project

Edit these files in Cursor:

**CONTEXT.md** — Your project definition
```markdown
## Project Name
MyAwesomeAPI

## One-Line Description
A REST API for managing projects with JWT auth and Postgres.

## Features (MVP)
- [ ] Users can register and login
- [ ] Users can create and manage projects
- [ ] Projects are persisted in Postgres

## Tech Stack
| Layer | Choice | Reason |
|---|---|---|
| Language | Python 3.11 | FastAPI + async |
| Framework | FastAPI | Fast, well-documented |
| Database | PostgreSQL | Scalable |
| Auth | JWT | Stateless |
```

**PROJECT_PLAN.md Section 1** — Your flags
```yaml
project_name: MyAwesomeAPI
description: REST API for project management with auth

features:
  - "User registration and login"
  - "Create/read/update/delete projects"
  - "Projects linked to users"

constraints:
  - "Solo developer"
  - "MVP in 1 week"
  - "$0 spend"

has_frontend:    false    # Set to true if you want a web UI
has_auth:        true     # Need login?
has_database:    true     # Need to store data?
needs_deploy:    true     # Deploy to the cloud?
external_apis:   false    # Call external APIs?
```

### Step 3: Open a Cursor Chat Session

1. Open Cursor
2. Create a new file called `AI_OS_SESSION.md` (or similar)
3. Open Cursor's chat panel (⌘K or Ctrl+K, then click "Chat")

---

## Starting Your First Session

### Paste the Boot Sequence

In the Cursor chat, paste this exact prompt:

```
I'm using AI OS, a modular agent system for development.

Read the following files carefully as they define my project setup:

CONTEXT.md — My project definition
PROJECT_PLAN.md — My configuration and active agents
STATE.md — My current project state
AGENTS.md — The master coordinator and boot sequence

Then follow this process:
1. Extract Section 3 from PROJECT_PLAN.md → confirm active agents
2. Extract Section 4 from PROJECT_PLAN.md → confirm task → agent mapping
3. Read STATE.md → confirm current phase and pending components
4. Boot all agents listed in Section 3
5. Run /plan to sequence the work

Important:
- Only use agents listed as ✅ in PROJECT_PLAN.md Section 3
- Inactive agents (⛔) do not exist for this project
- Update STATE.md after every task
- Use Section 4 to route tasks to the right agent

Let's begin. /plan
```

Cursor will:
1. Read all the files in your workspace
2. Understand your project scope
3. Activate the right agents
4. Create a detailed task sequence
5. Show you the first task to work on

---

## Using Commands in Cursor Chat

After the initial `/plan`, use these commands in the chat:

### `/build` — Implement the current task
```
Input to chat:
  /build

Output:
  [Complete, runnable code for the current task]
  [List of files to create/modify]
  [Explanation of what was built]
```

**What to do:**
- Copy the code into your project files
- Run any setup commands (migrations, installs, etc.)
- Test the implementation

### `/review` — Check code quality
```
Input to chat:
  /review

Output:
  [CRITICAL issues (must fix)]
  [HIGH issues (should fix)]
  [LOW issues (nice to fix)]
```

**What to do:**
- If CRITICAL: go back to `/build` and fix it
- If only HIGH/LOW: continue to next task

### `/debug [description]` — Fix a bug
```
Input to chat:
  /debug login endpoint returns 500 error

Output:
  [Root cause analysis]
  [Exact fix needed]
  [How to verify it works]
```

**What to do:**
- Apply the fix to your code
- Test it
- Confirm it works

### `/optimize [target]` — Performance improvements
```
Input to chat:
  /optimize database queries are slow

Output:
  [Problem analysis]
  [Before/after code]
  [Metric improvements]
```

**What to do:**
- Only use after MVP is complete
- Only if you've measured the problem

---

## Complete Workflow Example

### Session 1: Day 1 — Foundation & Auth

**Message 1:**
```
I'm using AI OS. Here are my files:

[paste CONTEXT.md, PROJECT_PLAN.md, STATE.md, AGENTS.md]

Follow boot sequence and run /plan
```

Cursor outputs: Task sequence (15+ tasks laid out)

**Message 2:**
```
/build
```

Cursor outputs: Project scaffolding code

You do: 
- Create folders
- Copy code
- Run `python -m pip install fastapi uvicorn sqlalchemy`

**Message 3:**
```
/review
```

Cursor outputs: "PASS - no issues"

**Message 4:**
```
Update STATE.md:
- Move "Project scaffolding" to Completed
- Set next task as Current Focus

Let's continue. /plan
```

Cursor outputs: Next task sequence

You repeat: `/build` → apply code → `/review` → update STATE.md

---

### Session 2: Day 2 — Continue Building

**Message 1:**
```
Here's my updated project state:

[paste updated STATE.md]

Continue from current focus. /build
```

Cursor outputs: Code for next component

You apply it, test it, review it.

**Keep going** until STATE.md shows all Phase 1 tasks as Completed.

---

### Session N: Deploy Day

**Message:**
```
MVP is complete and in Completed components. 

Activate devops agent in PROJECT_PLAN.md Section 3.

Updated PROJECT_PLAN.md:
[paste updated file with devops activated]

/plan deployment
```

Cursor outputs: Exact Docker setup + deployment instructions

---

## Tips for Using Cursor Effectively

### ✅ Do:

1. **Keep chat context alive**
   - Don't close the chat tab between builds
   - Chat remembers all previous messages
   - Cursor sees your workspace files automatically

2. **Copy/paste complete files to chat**
   - Before each major session: paste updated STATE.md
   - If you make manual changes: paste the updated file
   - Keeps Cursor's understanding accurate

3. **Use @workspace mention**
   ```
   @workspace I've manually edited database.py, here's the update:
   [paste file]
   
   Now run /build
   ```

4. **Reference specific files**
   ```
   /review backend/auth.py
   ```

5. **Ask for specific formats**
   ```
   /build in this format:
   
   [Code block 1: database migration]
   [Code block 2: models]
   [Code block 3: routes]
   
   List files to create.
   ```

6. **Break large tasks into sub-tasks**
   ```
   /plan for user authentication with these steps:
   1. User model + migration
   2. Password hashing setup
   3. Register endpoint
   4. Login endpoint
   ```

### ❌ Don't:

1. **Don't close Cursor without saving STATE.md**
   - Always copy updated STATE.md to your file
   - Cursor doesn't auto-save your workspace files

2. **Don't ask for features outside PROJECT_PLAN.md**
   - Cursor will respect scope
   - Use planner to add features officially

3. **Don't ignore CRITICAL issues from /review**
   - Always fix them before moving on
   - Let Cursor block you until fixed

4. **Don't manually edit code then forget to tell Cursor**
   - If you change a file: paste it to chat
   - Otherwise Cursor has outdated info

5. **Don't activate all agents at once**
   - Activate only what you need for current phase
   - More agents = slower responses, bigger context

---

## Multi-File Development in Cursor

### Scenario: Frontend component needs backend endpoint

**Message:**
```
I'm building a React component that needs a backend endpoint.

Here's the component I'm creating:
[paste frontend/components/TodoList.jsx]

This component needs:
- GET /api/todos/{userId}
- POST /api/todos

Please design and implement these API endpoints.
```

Cursor will:
1. Read your React component
2. Understand the API needs
3. Generate exact backend routes
4. Show you the API specification

**Then:**
```
/review these endpoints for security
```

Cursor checks for:
- Auth validation
- Input sanitization
- Error handling

---

## Debugging in Cursor

### Scenario: Bug reported

**Message:**
```
Bug: Login endpoint returns 500 error

Steps to reproduce:
1. POST /auth/login with correct credentials
2. Server returns 500

Here's my auth endpoint:
[paste backend/routes/auth.py]

/debug
```

Cursor will:
1. Analyze the code
2. Find the root cause
3. Show the exact fix
4. Explain what was wrong

**Then:**
```
Here's my fix applied:
[paste corrected code]

/review
```

---

## Performance Optimization in Cursor

### Scenario: MVP done, but slow

**Message:**
```
MVP is complete and deployed.

Performance issue: Database queries are slow (500ms response times)

Here's my current query:
[paste database code]

/optimize database queries
```

Cursor will:
1. Analyze the query performance
2. Suggest optimizations (indexing, caching, query rewrite)
3. Show before/after code
4. Estimate improvement

---

## Saving Your Session

### End of Each Session:

1. **Copy STATE.md from chat context** (if Cursor shows it)
2. **Or ask Cursor to generate updated STATE.md:**
   ```
   Based on what we've completed today, generate an updated STATE.md
   ```
3. **Save it to your local file**
4. **Copy your code changes to your editor**

### Start of Next Session:

1. **Open a new Cursor chat**
2. **Paste updated STATE.md** at the top
3. **Continue with `/build`**

---

## Example: Complete Todo API Project

### Initial Setup
```
CONTEXT.md: Todo API with JWT + Postgres
PROJECT_PLAN.md: flags all set to true
STATE.md: Phase 1, Current Focus: Project scaffolding
```

### Day 1 Session
```
Chat Message 1:
  Boot sequence + /plan

Cursor: "Phase 1 tasks: scaffolding, config, DB connection"

Chat Message 2: /build
Chat Message 3: /review → PASS
Chat Message 4: Update STATE.md, /plan next

[Repeat 3-4 more times through Phase 1]

End of Session: Copy updated STATE.md
```

### Day 2 Session
```
Chat Message 1: Paste updated STATE.md, continue

Chat Message 2: /build (User model)
Chat Message 3: /review (user model code)
Chat Message 4: Fix if issues found

[Continue through Phase 2: Auth]

[Repeat for Phase 3: Features]

[Repeat for Phase 4: Hardening]

End: All phases complete
```

### Deployment Day
```
Chat Message 1: Activate devops in PROJECT_PLAN.md

Chat Message 2:
  /plan deployment to Railway

Cursor: "Step 1: Create Dockerfile, Step 2: Railway config..."

Chat Message 3: /build
Chat Message 4: Follow deployment instructions
```

---

## Cursor Settings for AI OS

### Recommended `.cursor/rules.json`

Create a file `.cursor/rules.json` in your project:

```json
{
  "system": "You are an AI Development OS running AI OS framework. Read PROJECT_PLAN.md, CONTEXT.md, and STATE.md before every action. Use only agents listed in PROJECT_PLAN.md Section 3. Update STATE.md after every task.",
  "rules": [
    "Always read PROJECT_PLAN.md, CONTEXT.md, and STATE.md first",
    "Only activate agents listed in Section 3 of PROJECT_PLAN.md",
    "Use Section 4 task-to-agent mapping for routing",
    "Update STATE.md after every completed task",
    "Block CRITICAL issues before proceeding",
    "Do not add scope without planner approval",
    "Do not optimize before MVP is complete"
  ]
}
```

Cursor will see this and stay aligned with AI OS principles.

---

## Troubleshooting

### "Cursor says agent X is not active"
→ That's correct. Add agent X to PROJECT_PLAN.md Section 3, then paste the updated file to chat.

### "Chat lost context"
→ Copy updated STATE.md and paste it in your next message. Cursor will re-sync.

### "Code generated doesn't match my existing codebase"
→ Paste your existing file to chat first, show Cursor what's already there, then ask for the next piece.

### "Too much context/chat is slow"
→ Start a new chat session, paste STATE.md at the top. Cursor's chat is independent.

### "I need to show Cursor multiple files"
→ Use @workspace mention or paste files individually:
   ```
   Here are my current files:
   
   [FILE 1: backend/models.py]
   [code]
   
   [FILE 2: backend/routes.py]
   [code]
   
   Now /build [next component]
   ```

---

## Next Steps

1. **Download or clone AI OS** from GitHub
2. **Fill in CONTEXT.md** — your project
3. **Configure PROJECT_PLAN.md** — your flags and agents
4. **Open Cursor** — new chat
5. **Paste boot sequence** — `/plan`
6. **Start building!**

---

**Happy building in Cursor! 🚀**
