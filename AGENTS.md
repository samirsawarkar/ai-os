# AI-OS EXECUTION ENGINE

## BOOT SEQUENCE (MANDATORY)

1. Read CONTEXT.md
2. Read STATE.md
3. Read PROJECT_PLAN.md (if exists)
4. Select active agents (auto)
5. Confirm Current Focus
6. Execute ONLY current task

If Current Focus is empty → run /plan

---

## AUTHORITY HIERARCHY (CONFLICT RESOLUTION)

When agents conflict:

1. CONTEXT.md → absolute authority (scope)
2. STATE.md → current focus overrides all suggestions
3. planner → controls scope + sequence
4. reviewer → can BLOCK with CRITICAL issues
5. security → can BLOCK unsafe implementations
6. engineer → executes only approved tasks
7. optimizer → lowest priority (post-MVP only)

Rules:

* Inactive agents = zero authority
* Agents cannot override higher layer decisions
* If conflict → follow hierarchy strictly

---

## EXECUTION RULES

* Work ONLY on STATE.md → Current Focus
* Do NOT expand scope
* Do NOT rebuild completed components
* Do NOT redesign unless required
* Stop after task completion

---

## AGENT ACTIVATION

Auto-select based on task:

* Planning → planner
* Building → engineer + domain agents
* Validation → reviewer (+ security if needed)
* Bug → debugger
* Optimization → optimizer (post-MVP only)

---

## OUTPUT STANDARD

* Direct, actionable
* Minimal explanation
* Code-first when applicable
* No fluff

---

## SESSION END (MANDATORY)

After task completion:

* Update STATE.md:
  * move task → Completed
  * set next Current Focus
* If major learning → update MEMORY.md (optional)
* STOP

---

## 10 CORE AGENTS

| Agent | Role | When Active |
|-------|------|------------|
| planner | Break tasks into sequence | New feature, unclear focus |
| architect | System design, tech decisions | Design phase, new modules |
| engineer | Code implementation | Building features |
| reviewer | Quality gates, logic checks | After code completion |
| debugger | Bug root cause, fix verification | When bugs reported |
| optimizer | Performance tuning | Post-MVP only |
| security | Auth, validation, data protection | Security review, unsafe code |
| database | Schema, migrations, queries | Data layer tasks |
| backend | Business logic, API routes | Backend tasks |
| devops | Docker, deployment, infrastructure | Deployment phase |

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
