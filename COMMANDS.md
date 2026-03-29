# COMMANDS.md — Command Interface

> All commands read PROJECT_PLAN.md + STATE.md before executing.
> All commands use ONLY active agents from PROJECT_PLAN.md Section 3.
> All commands update STATE.md after executing.

---

## /plan

**Agents:** `planner` + `architect` (if architecture decision needed)
**When:** Starting a new feature, phase, or when Current Focus is undefined.

```
Input:
  /plan [feature or goal]
  /plan              ← uses STATE.md Pending list automatically

Output:
  ## Plan: [Feature]
  Phase: [current]
  Agent: planner [+ architect if structural]
  
  Tasks (ordered by dependency):
    1. [Task] → Done when: [criteria]
    2. [Task] → Done when: [criteria]
  
  STATE.md update:
    Current Focus → [Task 1]
    Pending → [Task 2, ...]
```

---

## /build

**Agents:** `engineer` + `backend` / `frontend` / `database` / `api-designer` (active ones only)
**When:** Current Focus is defined. No CRITICAL issues blocking.

```
Input:
  /build                    ← builds Current Focus from STATE.md
  /build [specific task]    ← builds named task

Output:
  ## Build: [Component]
  Agent: [primary agent]
  Scope: [what's being built]
  
  [COMPLETE, RUNNABLE CODE]
  
  Files:
    [path/file.ext] ← [purpose]
  
  STATE.md update:
    Completed → [component]
    Current Focus → [next pending]
```

---

## /review

**Agents:** `reviewer` + `security` (if active) + `performance` (if active)
**When:** After any /build. Before any phase transition or deployment.

```
Input:
  /review                   ← reviews Current Focus component
  /review [component name]  ← reviews named component
  /review [code block]      ← reviews pasted code

Output:
  ## Review: [Component]
  Agents: reviewer [+ security] [+ performance]
  
  Issues:
    [CRITICAL] [location] — [description]
               Fix: [exact action]
    [HIGH]     [location] — [description]
               Fix: [exact action]
    [LOW]      [location] — note for STATE.md
  
  Verdict: PASS / BLOCKED (by CRITICAL)
  
  STATE.md update:
    Notes → HIGH/LOW issues
```

---

## /debug

**Agents:** `debugger` + `logger` (if active)
**When:** A bug is reported. A test fails. Production error needs diagnosis.

```
Input:
  /debug [description of bug]
  /debug [error message or stack trace]

Output:
  ## Debug: [Bug]
  Agents: debugger [+ logger]
  
  Root Cause:
    File: [path]
    Function: [name]
    Cause: [explanation]
  
  Fix:
    Before: [broken code]
    After:  [fixed code]
  
  Verify: [how to confirm fix works]
  
  STATE.md update:
    Decisions → Bug: [name] | Fix: [summary]
```

---

## /optimize

**Agents:** `optimizer` + `performance` (if active)
**When:** MVP is complete (marked in STATE.md). Specific problem is measured.

```
Input:
  /optimize [component or area]
  /optimize [specific problem: e.g., "login endpoint is 800ms"]

Output:
  ## Optimize: [Target]
  Agents: optimizer [+ performance]
  
  Problem: [measured issue]
  Baseline: [current metric]
  
  Changes:
    [specific change + before/after code]
  
  Result:
    Removed: [bloat]
    Improved: [metric]
  
  STATE.md update:
    Decisions → Optimization: [summary]
```

---

## /status

**Agents:** None (reads files only)
**When:** Anytime — get a snapshot of where the project is.

```
Input:
  /status

Output:
  ## Status
  
  Phase: [from STATE.md]
  Current Focus: [from STATE.md]
  Active Agents: [from PROJECT_PLAN.md Section 3]
  
  Completed: [N components]
    [list]
  
  Pending: [N components]
    [list]
  
  Open Issues: [from STATE.md]
  Last Decision: [most recent from Decisions log]
```
