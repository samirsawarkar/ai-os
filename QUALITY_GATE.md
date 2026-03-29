# QUALITY_GATE.md — Approval Checklist

> Every task must pass this gate before marking complete.

---

## Pre-Completion Check

Before ANY task is marked complete, answer these questions:

### 1. Is It Minimal?

```
❌ FAIL: Includes features not in CONTEXT.md
❌ FAIL: Over-abstracted, complex patterns unnecessary
❌ FAIL: "Nice to have" extras added

✅ PASS: Solves Current Focus exactly
✅ PASS: No unnecessary abstraction
✅ PASS: Minimal code that works
```

**Question:** Could we solve this in fewer lines?
- If YES → simplify and resubmit
- If NO → continue

---

### 2. Is It Correct?

```
❌ FAIL: Known edge case not handled
❌ FAIL: Logic error (e.g., off-by-one)
❌ FAIL: Security hole (e.g., SQL injection)

✅ PASS: Happy path works
✅ PASS: Basic error handling
✅ PASS: No obvious bugs
```

**Question:** Does this solve the problem without breaking something?
- If UNCERTAIN → debugger investigates
- If YES → continue

---

### 3. Is It Necessary?

```
❌ FAIL: CONTEXT.md doesn't mention this
❌ FAIL: Feature not in PROJECT_PLAN
❌ FAIL: "Premature optimization"

✅ PASS: Explicitly in CONTEXT.md
✅ PASS: Current Focus matches
✅ PASS: MVP requires this
```

**Question:** Does CONTEXT.md or Current Focus require this?
- If NO → defer to post-MVP, remove from work
- If YES → continue

---

### 4. Is It Scalable Enough?

```
For CURRENT STAGE (MVP vs post-MVP):

MVP STAGE:
❌ FAIL: Over-engineered for scale (premature optimization)
✅ PASS: Works for MVP, easy to extend later

POST-MVP STAGE:
❌ FAIL: Breaks under load
✅ PASS: Handles expected scale

QUESTION: Does this fit the current maturity level?
  - If NO → simplify (MVP) or harden (post-MVP)
  - If YES → continue
```

---

### 5. Does It Follow RULES.md?

```
❌ FAIL: Uses deprecated pattern
❌ FAIL: Violates architecture standard
❌ FAIL: Breaks code style

✅ PASS: Follows established patterns
✅ PASS: Consistent style
✅ PASS: No tech debt
```

**Question:** Does RULES.md approve this approach?
- If NO → refactor to match rules
- If YES → continue

---

### 6. Does It Break Simplicity?

```
❌ FAIL: Introduces complex abstraction
❌ FAIL: Creates hidden dependencies
❌ FAIL: Harder to debug than alternative

✅ PASS: Clear, readable, straightforward
✅ PASS: Easy to debug
✅ PASS: Obvious next step for extending
```

**Question:** Would a new developer understand this in 2 minutes?
- If NO → simplify
- If YES → pass

---

## Quality Gate Decision Tree

```
START
  ↓
Is it minimal? NO → FAIL (Overengineered)
  ↓ YES
Is it correct? NO → FAIL (Bug/Logic error)
  ↓ YES
Is it necessary? NO → FAIL (Out of scope)
  ↓ YES
Is it scalable enough? NO → FAIL (Over/under-engineered)
  ↓ YES
Does it follow RULES.md? NO → FAIL (Pattern violation)
  ↓ YES
Does it preserve simplicity? NO → FAIL (Too complex)
  ↓ YES
✅ PASS → Mark complete → Update STATE.md
```

---

## FAIL Response

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
  - Just continue anyway
```

---

## Common Rejection Reasons

### ❌ "Overengineered"
```
You built: Complex observer pattern with event bus
MVP needs: Simple function that does the thing

Fix: Delete the pattern, write minimal code
```

### ❌ "Out of Scope"
```
You added: User preferences feature
CONTEXT.md needs: Todo CRUD only

Fix: Remove feature, add to Pending for post-MVP
```

### ❌ "Pattern Violation"
```
You used: Global state variable
RULES.md says: Dependency injection only

Fix: Refactor to follow RULES.md
```

### ❌ "Unnecessary Abstraction"
```
You built: Generic utility class for 1 use case
Better approach: Inline function

Fix: Remove abstraction, inline the code
```

### ❌ "Missing Error Handling"
```
You wrote: Function that crashes on bad input
Should: Return error or default value

Fix: Add basic error handling
```

### ❌ "Security Issue"
```
You have: SQL query with string concatenation
Should: Parameterized queries

Fix: Use parameterized queries, validate input
```

---

## PASS Criteria

✅ **Minimal** — solves exactly the problem, nothing more
✅ **Correct** — happy path works, basic errors handled
✅ **Necessary** — explicitly required by CONTEXT.md or Current Focus
✅ **Scalable** — fits current stage (MVP or post-MVP)
✅ **Compliant** — follows RULES.md and patterns
✅ **Simple** — new developer understands it in 2 minutes

All 6 must be YES before PASS.

---

## Special Cases

### Security Review (Required)
If task involves auth, data, or user input:
- security agent MUST review
- Even if quality gate passes
- Security can veto with CRITICAL

### Performance Review (Post-MVP Only)
If task is post-MVP optimization:
- optimizer MUST review
- Verify before/after metrics
- Gate allows perf tradeoffs

### Architecture Review (Rare)
If task involves system redesign:
- architect MUST review
- Verify design aligns with RULES.md
- Gate allows arch changes with approval

---

## Using This Gate

**For Reviewer Agent:**
Use this gate before marking any work APPROVED.

**For Engineer Agent:**
Self-check against this gate before submitting.

**For Quality Assurance:**
If something feels wrong, run it through this gate.

---

*Quality gates prevent technical debt. They're not optional. They're law.*
