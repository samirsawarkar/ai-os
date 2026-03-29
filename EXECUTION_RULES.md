# EXECUTION_RULES.md — Discipline & Control

> Execution discipline prevents scope creep, overengineering, and chaos.

---

## Mandatory Rules (NEVER BREAK)

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

Exception: If architect identifies CRITICAL flaw
  1. Document the flaw
  2. Get planner approval
  3. Then redesign
  4. Update VERSION.md
```

### Rule 3: **One Agent at a Time**
```
❌ WRONG: Run planner + architect + engineer simultaneously
✅ RIGHT: Planner → architect → engineer (sequential)

Sequential execution:
  - Prevents conflicts
  - Ensures handoff clarity
  - Easier to debug
  - Lower token usage
```

### Rule 4: **Stop After Task Completion**
```
Task is complete ONLY IF:
  1. Implemented ✅
  2. Reviewed ✅
  3. STATE.md updated ✅

After completing:
  → Stop
  → Don't start next task
  → Wait for human confirmation
  → Then /plan for next
```

### Rule 5: **Always Prefer Minimal Solution**
```
When choosing between:
  A) Complex, comprehensive solution
  B) Minimal, focused solution that solves the problem

→ Always choose B

Minimal:
  - Ships faster
  - Easier to test
  - Easier to debug
  - Easier to extend
  - Scales better
```

---

## Task Completion Checklist

Before marking any task as complete, verify:

```
IMPLEMENTATION ✓
  □ Code written
  □ Handles happy path
  □ Basic error handling
  □ Follows RULES.md patterns

REVIEW ✓
  □ Code quality check (reviewer)
  □ Security check (if auth/input)
  □ Logic verification

STATE UPDATE ✓
  □ STATE.md updated
  □ Completed → move to Completed list
  □ MEMORY.md updated (if learning)
  □ VERSION.md updated (if significant)

STOP ✓
  □ Don't start next task
  □ Wait for /plan before proceeding
```

---

## Failure Handling

### If Stuck on a Task

1. **Reduce Scope**
   - What's the minimum viable fix?
   - Can we defer the rest?
   - Implement minimal version

2. **Use Debugger**
   - Run `/debug [specific issue]`
   - Get root cause
   - Engineer fixes only root cause

3. **Ask Architect**
   - If unclear design
   - Get architecture clarity
   - Then implement

4. **Update STATE.md**
   - Blocked → log in STATE.md
   - Document blocker
   - Move to next task temporarily

### If Quality Gate Blocks

```
QUALITY_GATE says: FAIL

→ Don't argue
→ Don't work around it
→ Fix what it flagged
→ Re-submit
→ Repeat until PASS
```

---

## When to Break Rules

Only these exceptions exist:

```
CRITICAL BUG in production
  → Stop all work
  → /debug the bug
  → Engineer fixes
  → Reviewer approves
  → Deploy hotfix
  → Resume normal workflow

SECURITY VULNERABILITY
  → Security agent investigates
  → If CRITICAL → patch immediately
  → Update STATE.md
  → Continue

ARCHITECT VETO
  → Architect says pattern is wrong
  → Stop implementation
  → Redesign per architect
  → Continue

Anything else:
  → Follow rules strictly
```

---

## Anti-Patterns to Avoid

❌ **Scope Creep**
- Started with "add field" → ended with "refactor entire module"
- Fix: STATE.md, /plan, sequential execution

❌ **Overengineering**
- Built with 5 design patterns for a 2-line feature
- Fix: QUALITY_GATE checks for this

❌ **Silent Failures**
- Code runs but returns wrong data
- Fix: Always update STATE.md with results

❌ **Lost Work**
- Session ends, no STATE.md update, work forgotten
- Fix: STATE.md update is mandatory completion step

❌ **Multiple Agents Fighting**
- Planner says do X, engineer ignores and does Y
- Fix: Sequential execution, clear handoffs

---

## State Update Mandatory Fields

After EVERY task, update STATE.md with:

```yaml
Current Phase: [What phase are we in?]
Current Focus: [What are we working on RIGHT NOW?]

Completed:
  - [What just finished?]
  
Pending:
  - [What's left to do?]

Decisions:
  - [What did we decide?]

Known Issues:
  - [What's broken or unclear?]
```

---

## Execution Flow (Strict)

```
START OF SESSION
  ↓
Read CONTEXT.md + STATE.md + MEMORY.md + VERSION.md
  ↓
Boot sequence (AGENTS.md)
  ↓
Auto-select agents
  ↓
Read Current Focus from STATE.md
  ↓
Route to responsible agent
  ↓
EXECUTE (single agent, one task)
  ↓
REVIEW (if needed)
  ↓
UPDATE STATE.md (MANDATORY)
  ↓
UPDATE MEMORY.md (if new learning)
  ↓
UPDATE VERSION.md (if major change)
  ↓
STOP (don't auto-continue)
  ↓
END OF SESSION
```

No deviations. This is the law.

---

*Discipline enables autonomy. Rules prevent chaos. Follow them strictly.*
