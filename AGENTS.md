# AGENTS.md — Master Coordinator

---

## BOOT SEQUENCE (MANDATORY — EVERY SESSION)

```
Step 1: Read PROJECT_PLAN.md
        → Extract Section 3: Active Agents list
        → Extract Section 4: Task → Agent mapping
        → Extract Section 5: Current phase

Step 2: Read STATE.md
        → Confirm Current Phase
        → Confirm Completed Components (never rebuild)
        → Identify Current Focus

Step 3: Activate ONLY agents listed in PROJECT_PLAN.md Section 3
        → All other agents are INACTIVE — treat them as non-existent

Step 4: Assign active agent to Current Focus using Section 4 mapping

Step 5: Execute
```

---

## AGENT REGISTRY

| ID             | Layer          | File                        |
|----------------|----------------|-----------------------------|
| `planner`      | Strategy       | agents/planner.md           |
| `architect`    | Strategy       | agents/architect.md         |
| `engineer`     | Implementation | agents/engineer.md          |
| `reviewer`     | Quality        | agents/reviewer.md          |
| `debugger`     | Repair         | agents/debugger.md          |
| `optimizer`    | Refinement     | agents/optimizer.md         |
| `security`     | Quality        | agents/security.md          |
| `database`     | Implementation | agents/database.md          |
| `api-designer` | Design         | agents/api-designer.md      |
| `frontend`     | Implementation | agents/frontend.md          |
| `backend`      | Implementation | agents/backend.md           |
| `devops`       | Operations     | agents/devops.md            |
| `tester`       | Quality        | agents/tester.md            |
| `performance`  | Refinement     | agents/performance.md       |
| `logger`       | Observability  | agents/logger.md            |

---

## ACTIVATION RULES

```
RULE 1: Only agents listed as ✅ in PROJECT_PLAN.md Section 3 are active.
RULE 2: Inactive agents are ignored — not referenced, not invoked.
RULE 3: Agent count must be minimum viable for the project type.
RULE 4: New agents can be activated by updating PROJECT_PLAN.md Section 3.
RULE 5: Always use Section 4 to determine which agent handles each task.
```

---

## AGENT INTERACTION PROTOCOL

### Authority Hierarchy
```
PROJECT_PLAN.md → overrides everything (scope, agent selection)
CONTEXT.md      → overrides all agents on product decisions
architect       → overrides engineer on structure decisions
reviewer        → can block engineer with CRITICAL issues
security        → can block devops with CRITICAL findings
planner         → overrides engineer on scope decisions
```

### Conflict Resolution
```
Engineer wants to add a feature not in scope → planner overrides: don't build it
Reviewer flags CRITICAL → engineer must fix before proceeding
Security flags CRITICAL → devops cannot deploy
Architect sets a pattern → engineer must follow it
Optimizer wants to refactor working MVP code → blocked until MVP ships
```

### Handoff Pattern
```
Task arrives
  → planner: is this scoped and sequenced? YES
  → [primary agent per Section 4]: implement
  → reviewer: any issues? 
      CRITICAL → back to primary agent
      NONE     → STATE.md update → next task
```

---

## INACTIVE AGENT HANDLING

If a command or task maps to an inactive agent:
```
Response: "Agent [X] is not active for this project.
           See PROJECT_PLAN.md Section 3.
           To activate: add [X] to Section 3 with rationale."
```

Do NOT attempt to use an inactive agent's capabilities. Wait for it to be activated in PROJECT_PLAN.md.

---

## STATE.md UPDATE RULES

Every agent must update STATE.md when:
- A component is completed → move to Completed
- A new task is discovered → add to Pending
- A decision is made → log in Decisions
- A bug is found and fixed → log in Decisions
- A phase ends → update Current Phase
