# EXECUTION_RULES.md — Discipline, Control & Quality

> Execution discipline prevents scope creep, overengineering, and technical debt.

---

## PART 1: Mandatory Execution Rules (NEVER BREAK)

### Rule 1: **Never Expand Current Focus**
```
❌ WRONG: Start with todo feature, end up building auth system
✅ RIGHT: Complete todo feature, update STATE.md, then plan auth

IF tempted to add scope:
  1. Stop
  2. Add to STATE.md Pending
  3. Update Current Focus
  4. Run /plan for new sequence
```

### Rule 2: **Never Redesign Unless Forced**
```
❌ WRONG: "I could refactor this better" → redesigns working code
✅ RIGHT: Code works → move to next task → optimize post-MVP

Exception: Only if architect identifies CRITICAL flaw
```

### Rule 3: **One Agent at a Time**
```
❌ WRONG: Run planner + architect + engineer simultaneously
✅ RIGHT: Sequential execution (planner → architect → engineer)

Sequential = predictable, debuggable, lower token usage
```

### Rule 4: **Stop After Task Completion**
```
A task is COMPLETE ONLY IF:
  1. Implemented ✓
  2. Reviewed ✓
  3. STATE.md updated ✓
  4. MEMORY.md updated (if learning) ✓
  5. VERSION.md updated (if change) ✓

After completing → STOP (don't auto-continue)
Wait for human /plan before next task
```

### Rule 5: **Always Prefer Minimal Solution**
```
When choosing:
  A) Complex, comprehensive solution
  B) Minimal, focused solution that solves it

→ Choose B (ships faster, easier to test, easier to extend)
```

---

## PART 2: Quality Gate (6-Point Pre-Completion Checklist)

Before marking ANY task complete, verify all 6:

### Gate 1: Is It Minimal?
```
❌ FAIL: Includes features not in CONTEXT.md
❌ FAIL: Over-abstracted, unnecessary complexity
❌ FAIL: "Nice to have" extras added

✅ PASS: Solves Current Focus exactly
✅ PASS: No unnecessary abstraction
✅ PASS: Minimal code that works
```

### Gate 2: Is It Correct?
```
❌ FAIL: Known edge case not handled
❌ FAIL: Logic error (off-by-one, etc.)
❌ FAIL: Security hole (SQL injection, etc.)

✅ PASS: Happy path works
✅ PASS: Basic error handling
✅ PASS: No obvious bugs
```

### Gate 3: Is It Necessary?
```
❌ FAIL: CONTEXT.md doesn't mention this
❌ FAIL: Feature not in PROJECT_PLAN
❌ FAIL: Premature optimization/polish

✅ PASS: Explicitly in CONTEXT.md
✅ PASS: Current Focus matches
✅ PASS: MVP requires this
```

### Gate 4: Is It Scalable Enough?
```
For CURRENT STAGE (MVP vs post-MVP):

MVP:  Works for MVP, easy to extend later
POST: Handles expected scale

❌ FAIL: Over-engineered (MVP) or under-hardened (post-MVP)
✅ PASS: Fits current maturity level
```

### Gate 5: Does It Follow RULES.md?
```
❌ FAIL: Uses deprecated pattern
❌ FAIL: Violates architecture standard
❌ FAIL: Breaks code style

✅ PASS: Follows established patterns
✅ PASS: Consistent style
✅ PASS: No tech debt
```

### Gate 6: Does It Preserve Simplicity?
```
❌ FAIL: Introduces complex abstraction
❌ FAIL: Creates hidden dependencies
❌ FAIL: Harder to debug than alternative

✅ PASS: Clear, readable, straightforward
✅ PASS: Easy to debug
✅ PASS: Obvious next step for extending
```

---

## PART 3: Quality Gate Decision Tree

```
START (Before marking ANY task complete)
  ↓
Gate 1: Is it minimal? NO → FAIL (Overengineered)
  ↓ YES
Gate 2: Is it correct? NO → FAIL (Bug/Logic error)
  ↓ YES
Gate 3: Is it necessary? NO → FAIL (Out of scope)
  ↓ YES
Gate 4: Is it scalable enough? NO → FAIL (Over/under-engineered)
  ↓ YES
Gate 5: Does it follow RULES.md? NO → FAIL (Pattern violation)
  ↓ YES
Gate 6: Does it preserve simplicity? NO → FAIL (Too complex)
  ↓ YES
✅ PASS → Mark complete → Update STATE.md + MEMORY.md + VERSION.md
```

---

## PART 4: FAIL Response Protocol

If quality gate rejects:

```
GATE: FAIL [reason]

Response:
1. Read the reason
2. Fix the issue
3. Resubmit
4. Repeat until PASS

DO NOT:
  - Argue with the gate
  - Work around it
  - Skip this task
  - Continue anyway
```

---

## PART 5: Common Rejection Reasons

### ❌ "Overengineered"
```
You built: Complex observer pattern with event bus
MVP needs: Simple function that does the thing
Fix: Delete pattern, write minimal code
```

### ❌ "Out of Scope"
```
You added: User preferences feature
CONTEXT.md needs: Todo CRUD only
Fix: Remove feature, add to Pending
```

### ❌ "Pattern Violation"
```
You used: Global state variable
RULES.md says: Dependency injection only
Fix: Refactor to follow RULES.md
```

### ❌ "Missing Error Handling"
```
You wrote: Function crashes on bad input
Should: Return error or default
Fix: Add basic error handling
```

### ❌ "Security Issue"
```
You have: SQL with string concat
Should: Parameterized queries
Fix: Use parameterized queries
```

---

## PART 6: Mandatory Completion Ritual

Before EVERY task is marked complete:

```
[1] Pass Quality Gate (all 6 gates)
    └─ If FAIL: fix and resubmit

[2] Update STATE.md
    ├── Move to Completed list
    ├── Set Current Focus to next Pending
    ├── Log decisions
    └── Log blockers

[3] Update MEMORY.md (if new learning)
    ├── Extract decision
    ├── Extract pattern
    ├── Extract mistake (if any)
    └── Add constraint learned

[4] Update VERSION.md (if significant change)
    ├── Patch bump (bug fix)
    ├── Minor bump (new feature)
    └── Major bump (stable release)

[5] STOP execution
    ├── Do NOT auto-start next task
    └── Wait for /plan command
```

---

## PART 7: When to Break Rules

ONLY these exceptions exist:

```
CRITICAL BUG in production
  → Stop all work
  → /debug the bug
  → Fix + test
  → Deploy hotfix
  → Resume

SECURITY VULNERABILITY
  → Security agent investigates
  → If CRITICAL → patch now
  → Resume

ARCHITECT VETO (pattern is wrong)
  → Stop implementation
  → Redesign per architect
  → Continue

Anything else:
  → Follow rules strictly
```

---

## PART 8: Anti-Patterns to Avoid

❌ **Scope Creep** → Use STATE.md + /plan
❌ **Overengineering** → Quality gate blocks this
❌ **Silent Failures** → Always update STATE.md
❌ **Lost Work** → STATE.md update is mandatory
❌ **Multiple Agents Fighting** → Sequential execution
❌ **Premature Optimization** → Only post-MVP
❌ **Skipping Reviews** → Reviewer is mandatory

---

*Discipline enables autonomy. Rules prevent chaos. Follow them strictly.*
