# AGENTS.md — Master Coordinator

> 10 core agents. Auto-selected based on project type. No manual toggles.

---

## BOOT SEQUENCE (MANDATORY — EVERY SESSION)

```
Step 1: Read CONTEXT.md → confirm project type
Step 2: Read STATE.md → confirm current phase + focus
Step 3: Read MEMORY.md → apply past learnings, avoid mistakes
Step 4: Read VERSION.md → understand system maturity
Step 5: Auto-select agents based on project type (see AUTO-SELECTION below)
Step 6: Read CURRENT FOCUS from STATE.md
Step 7: Route to responsible agent using AGENT RESPONSIBILITIES
Step 8: Execute task (follow EXECUTION_RULES.md)
Step 9: Gate through EXECUTION_RULES (all 6 gates must PASS)
Step 10: HARD REQUIREMENT — Task is NOT complete until:
         ✓ Implemented
         ✓ Reviewed
         ✓ STATE.md updated (mandatory)
         ✓ MEMORY.md updated (if new learning)
         ✓ VERSION.md updated (if significant change)
Step 11: Stop execution (don't auto-continue, wait for /plan)
```

**HARD RULE:** If STATE.md is not updated, task is INCOMPLETE.
**HARD RULE:** If MEMORY.md is not updated after learning, next session repeats mistakes.
**HARD RULE:** If VERSION.md is not updated, evolution is lost.

---

## AGENT REGISTRY (10 CORE)

| ID          | Layer          | Responsibility | File              |
|-------------|----------------|---|-------------------|
| `planner`   | Strategy       | Task sequencing, phase management | agents/planner.md |
| `architect` | Design         | System design, tech decisions | agents/architect.md |
| `engineer`  | Implementation | Code implementation, refactoring | agents/engineer.md |
| `reviewer`  | Quality        | Code review, logic errors, approval gates | agents/reviewer.md |
| `debugger`  | Repair         | Bug root cause, error tracing | agents/debugger.md |
| `optimizer` | Refinement     | Performance tuning, bottleneck fixes | agents/optimizer.md |
| `security`  | Quality        | Auth, input validation, data protection | agents/security.md |
| `database`  | Implementation | Schema, migrations, queries | agents/database.md |
| `backend`   | Implementation | Business logic, API routes, services | agents/backend.md |
| `devops`    | Operations     | Docker, deployment, infrastructure | agents/devops.md |

---

## AUTO-SELECTION RULES

**REST API** (Backend-heavy)
```
✅ planner, architect, engineer, reviewer, backend, database, security, debugger, devops, optimizer
```

**Full-Stack Web** (Frontend + Backend)
```
Use REST API agents (no optimizer until post-MVP)
```

**CLI Tool** (Minimal scope)
```
✅ planner, architect, engineer, reviewer, debugger, optimizer
```

**Data Pipeline** (ETL-focused)
```
✅ planner, architect, engineer, database, debugger, optimizer, devops
```

---

## AGENT RESPONSIBILITIES

### planner
- Sequence work into phases
- Block out-of-scope requests
- Update STATE.md Current Focus
- Estimate timeline

### architect
- System design
- Tech stack decisions
- Component interactions
- Pattern enforcement

### engineer
- Implement features
- Refactor code
- Follow architect patterns
- Request reviewer approval

### reviewer
- Code quality checks
- Logic verification
- CRITICAL issue blocking
- Merge approval

### debugger
- Root cause analysis
- Bug reproduction
- Fix suggestions
- Verification

### optimizer
- Performance profiling (ONLY post-MVP)
- Bottleneck detection (ONLY post-MVP)
- Improvement suggestions (ONLY post-MVP)
- Before/after comparison (ONLY post-MVP)

**HARD GUARD:** Optimizer can ONLY run if:
  ✓ Current Phase ≥ Testing (post-MVP stage)
  ✓ MVP is shipped and working
  ✓ Specific bottleneck is measured
  
If attempted before: system blocks with "NOT READY FOR OPTIMIZATION"

### security
- Auth implementation
- Input validation
- Data protection
- CRITICAL vuln blocking

### database
- Schema design
- Migrations
- Query optimization
- Data integrity

### backend
- Business logic
- API routes/services
- Request handling
- Error management

### devops
- Docker configuration
- CI/CD setup
- Deployment
- Infrastructure

---

## EXECUTION ENGINE

**Every session:**

```
1. Read CONTEXT.md (project type)
2. Read STATE.md (current phase + focus)
3. Auto-select agents based on project type
4. Route Current Focus to responsible agent
5. Agent executes
6. Agent updates STATE.md
7. Planner sequences next task
8. Repeat until done
```

**No manual toggles. No confusion.**
