# WORKFLOWS.md — Execution Loops
# All workflows read PROJECT_PLAN.md + STATE.md first.
# All workflows use ONLY active agents from PROJECT_PLAN.md Section 3.
# All workflows end with a STATE.md update.

---

## WORKFLOW 1 — Feature Development Loop

**Active agents used:** planner, engineer, [backend/frontend/database/api-designer per task], reviewer, security (if active)

```
START
  │
  ▼
[1] READ
    ├── PROJECT_PLAN.md Section 3 → confirm active agents
    ├── PROJECT_PLAN.md Section 4 → confirm task → agent mapping
    └── STATE.md → Current Phase, Completed, Current Focus
  │
  ▼
[2] Is Current Focus defined in STATE.md?
    ├── NO  → agent: planner
    │         → /plan [next pending item]
    │         → Set Current Focus in STATE.md
    │         → Continue to step 3
    └── YES → Continue to step 3
  │
  ▼
[3] Is Current Focus a completed component?
    ├── YES → Skip. Set next Pending as Current Focus. Return to step 2.
    └── NO  → Continue to step 4
  │
  ▼
[4] ASSIGN agent using PROJECT_PLAN.md Section 4 Task → Agent map
    Examples:
      schema design     → database
      route impl        → api-designer
      business logic    → backend
      UI component      → frontend
      general code      → engineer
  │
  ▼
[5] /build [Current Focus]
    → Assigned agent implements the component
    → Output: complete, runnable code
    → Output: files created/modified
  │
  ▼
[6] /review [component just built]
    → agent: reviewer
    → agent: security (if active AND component handles auth/input/data)
    │
    ├── CRITICAL found?
    │     YES → Assigned agent fixes immediately → Return to step 6
    │     NO  → Continue to step 7
    │
    └── HIGH found?
          YES → Log in STATE.md Notes → Continue to step 7
          NO  → Continue to step 7
  │
  ▼
[7] UPDATE STATE.md
    → Move component to Completed
    → Log any HIGH/LOW issues in Notes
    → Set next Pending item as Current Focus
  │
  ▼
[8] Are all Phase tasks complete?
    ├── NO  → Return to step 4
    └── YES → Continue to step 9
  │
  ▼
[9] PHASE TRANSITION
    → Update STATE.md: Current Phase → next phase
    → Check PROJECT_PLAN.md Section 5 for next phase agent set
    → Activate any newly required agents if not already active
  │
  ▼
END OF PHASE → Return to step 1 for next phase
```

---

## WORKFLOW 2 — Bug Fixing Loop

**Active agents used:** debugger, logger (if active), engineer, reviewer

```
START
  │
  ▼
[1] READ STATE.md
    → Note Current Focus (save it — restore after fix)
    → Note Current Phase
  │
  ▼
[2] CLASSIFY the bug
    ├── CRITICAL → system down, data loss, security breach, auth bypass
    │              → Fix immediately before any other work
    ├── HIGH     → feature broken, no workaround, blocks user flow
    │              → Fix before next /build session
    └── LOW      → cosmetic, edge case, minor inconvenience
                   → Log in STATE.md Notes → Return to Current Focus
  │
  ▼
[3] Is bug CRITICAL or HIGH?
    ├── LOW → Log in STATE.md Notes → END (return to normal workflow)
    └── CRITICAL/HIGH → Continue to step 4
  │
  ▼
[4] INTERRUPT current work
    → STATE.md: add note "Interrupted for bug: [description]"
    → Preserve Current Focus (restore it after fix)
  │
  ▼
[5] /debug [bug description + reproduction steps]
    → agent: debugger
    → Isolate: exact file + function + line
    → Reproduce: minimal case
    → Do NOT refactor surrounding code
  │
  ▼
[6] FIX
    → agent: engineer (implements the fix)
    → Change ONLY what is broken
    → Add comment explaining what was wrong and why this fixes it
  │
  ▼
[7] /review [fixed component]
    → agent: reviewer
    ├── New CRITICAL? → Return to step 5
    ├── New HIGH?     → Log, continue
    └── Clean?        → Continue to step 8
  │
  ▼
[8] UPDATE STATE.md
    → Decisions log: Bug [name] | Root cause | Fix applied | Date
    → Restore Current Focus to pre-interrupt value
  │
  ▼
[9] RESUME normal Feature Development Loop
  │
  ▼
END
```

---

## WORKFLOW 3 — System Design Loop

**Active agents used:** planner, architect, (database if schema is involved)
**When:** New project start, new major component, architectural decision needed.

```
START
  │
  ▼
[1] READ CONTEXT.md fully
    → Extract: Goals, Users, Features (MVP only), Constraints, Tech Stack
  │
  ▼
[2] READ PROJECT_PLAN.md
    → Confirm agent selection logic in Section 2
    → Derive active agent list for Section 3
    → Fill in Task → Agent map in Section 4
  │
  ▼
[3] DEFINE MVP SCOPE
    → agent: planner
    → List only features required for the core user flow
    → Everything else → Post-MVP Backlog in STATE.md
    → Rule: if removing it breaks the core flow → it's MVP
             if removing it doesn't → it's post-MVP
  │
  ▼
[4] DESIGN ARCHITECTURE
    → agent: architect
    → Define: folder structure, tech stack, data flow, layer boundaries
    → Define: what each layer is NOT allowed to do
    → Output: architecture diagram (text), folder tree, decisions list
  │
  ▼
[5] DESIGN DATA MODEL (if has_database = true)
    → agent: database
    → Define tables, columns, relationships, indexes
    → Do not over-normalize — MVP schema first
    → Output: schema definition, migration plan
  │
  ▼
[6] /review architecture
    → agent: reviewer
    → Check for overengineering
    → Check for missing fundamentals (auth, error handling, config)
    → Check each component has a clear, singular purpose
    ├── Issues? → Return to step 4 with specific corrections
    └── Clean?  → Continue to step 7
  │
  ▼
[7] INITIALIZE STATE.md
    → Current Phase: Phase 1 — Foundation
    → Completed: []
    → Pending: [ordered component list from architect output]
    → Current Focus: [first component]
    → Decisions: [all architectural decisions from architect]
  │
  ▼
[8] LOCK ARCHITECTURE
    → Do not change architecture without strong, explicit reason
    → All architectural changes: log in STATE.md Decisions with rationale
    → Any change that breaks an existing completed component → escalate to architect
  │
  ▼
[9] BEGIN Feature Development Loop (Workflow 1)
  │
  ▼
END
```

---

## WORKFLOW 4 — Pre-Deploy Hardening Loop

**Active agents used:** reviewer, security, logger, tester (if active), devops
**When:** MVP features are complete. Preparing for first deployment.

```
START
  │
  ▼
[1] VERIFY MVP completeness
    → All Phase 3 components in STATE.md Completed list?
    ├── NO  → Return to Feature Development Loop
    └── YES → Continue
  │
  ▼
[2] FULL REVIEW PASS
    → agent: reviewer + security
    → Review every completed component
    → Collect all CRITICAL + HIGH findings
  │
  ▼
[3] Fix all CRITICAL issues
    → Use Bug Fixing Loop for each CRITICAL
    → No deployment until zero CRITICAL issues remain
  │
  ▼
[4] SET UP LOGGING
    → agent: logger (if active)
    → Structured logging in place
    → Request ID tracing configured
    → No sensitive data in logs confirmed
  │
  ▼
[5] RUN TESTS (if tester is active)
    → agent: tester
    → Auth flows tested
    → Core business logic tested
    → API contracts tested
    → All tests pass
  │
  ▼
[6] DEPLOYMENT SETUP
    → agent: devops
    → Dockerfile + docker-compose written
    → .env.example committed
    → Health check endpoint: GET /health → 200
    → Deploy to target platform
  │
  ▼
[7] SMOKE TEST IN PRODUCTION
    → Core user flow works on live URL
    → Auth works
    → Data persists
    → Errors return correct shapes
  │
  ▼
[8] UPDATE STATE.md
    → Current Phase → Phase 5: Launched
    → Note: MVP live at [URL]
    → Note: deploy date
  │
  ▼
END → System is live. Post-MVP backlog begins.
```

---

## WORKFLOW 5 — Post-MVP Optimization Loop

**Active agents used:** optimizer, performance (both must be active)
**Trigger:** MVP is live. A specific, measurable problem exists.

```
START
  │
  ▼
[1] CONFIRM MVP is live (STATE.md Phase = Launched)
    → If not launched → STOP. Do not optimize unreleased software.
  │
  ▼
[2] IDENTIFY the problem (must be measurable)
    → "endpoint X is 800ms" ← valid
    → "code looks messy" ← not valid, use optimizer only after measuring
  │
  ▼
[3] /optimize [component + measured problem]
    → agent: optimizer (complexity/bloat) or performance (speed/resource)
    → Baseline metric recorded
    → One change at a time
  │
  ▼
[4] /review [optimized component]
    → agent: reviewer
    → Confirm no regressions introduced
    → Confirm correctness unchanged
  │
  ▼
[5] MEASURE result
    → Compare to baseline from step 2
    → If no improvement → revert change
    → If improved → keep and log
  │
  ▼
[6] UPDATE STATE.md
    → Decisions: Optimization [target] | Before [metric] | After [metric]
  │
  ▼
END → Repeat for next measurable problem
```
