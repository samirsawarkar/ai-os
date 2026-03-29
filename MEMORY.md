# MEMORY.md — Decisions, Patterns, Learnings

> Capture decisions and patterns so they're not repeated or forgotten.

---

## Strategic Decisions

### 1. **10 Agents Maximum (Not 15)**
- **Decision:** Reduce from 15 agents to 10 core agents
- **Reasoning:** More agents = slower reasoning, more confusion, overlap
- **Impact:** Faster execution, clearer routing, easier maintenance
- **Pattern:** When agents start overlapping, merge or remove

### 2. **Auto-Selection Over Manual Toggles**
- **Decision:** Eliminate manual agent activation
- **Reasoning:** Manual toggles → errors, maintenance burden, user friction
- **Impact:** Autonomous system, no configuration mistakes
- **Pattern:** Define auto-selection rules by project type once, reuse forever

### 3. **Single README, No Bloat**
- **Decision:** Delete 11 documentation files
- **Reasoning:** Documentation bloat = ignored by AI, confusing for users
- **Impact:** Clear entry point, no cognitive load, faster onboarding
- **Pattern:** One README, reference others only when needed

### 4. **Execution Engine Over Manual Instructions**
- **Decision:** Add AGENTS.md execution engine
- **Reasoning:** Manual "tell AI to do X" = not autonomous, error-prone
- **Impact:** Autonomous workflow, predictable execution
- **Pattern:** Workflows should be self-contained loops

---

## Patterns Learned

### Pattern 1: **Minimal Scope First**
- When tempted to add features: ask "does MVP need this?"
- If no → defer to post-MVP
- **When to use:** Every phase decision
- **Result:** Ships faster, proves value, attracts adoption

### Pattern 2: **Auto-Selection Beats Manual Configuration**
- Configuration friction → users skip it or mess it up
- Auto-selection based on simple rules → always correct
- **When to use:** Agent activation, workflow routing
- **Result:** Zero user errors, faster execution

### Pattern 3: **Boot Sequence Prevents Chaos**
- Without boot sequence: AI makes random decisions
- With boot sequence: predictable, auditable, repeatable
- **When to use:** Every session start
- **Result:** Consistency, trust, reproducibility

### Pattern 4: **State Tracking is Everything**
- Without STATE.md: "what did I do?" → lost work
- With STATE.md: "what's next?" → automatic continuity
- **When to use:** After every major task
- **Result:** Progress visibility, session continuity

---

## Mistakes & Fixes

### Mistake 1: Too Many Agents (15 → 10)
- **Cause:** Tried to cover every possible role
- **Problem:** AI reasoning got slower, agents overlapped, users confused
- **Fix:** Aggressive reduction to 10 core, merged roles (api-designer → backend, etc.)
- **Learning:** "Do one thing well" matters more than comprehensive coverage

### Mistake 2: Manual Agent Toggles
- **Cause:** Tried to give users flexibility
- **Problem:** Toggles weren't set right, got stale, created friction
- **Fix:** Auto-selection based on project type
- **Learning:** Configuration should be automatic, not manual

### Mistake 3: 20+ Documentation Files
- **Cause:** Tried to document everything for every use case
- **Problem:** AI ignored 80% of docs, users got confused, maintenance burden
- **Fix:** Cut to single README, moved specifics to AGENTS.md/WORKFLOWS.md
- **Learning:** Less documentation is more effective than comprehensive documentation

### Mistake 4: No Version Control
- **Cause:** Didn't track why decisions were made
- **Problem:** Six months later: "why did we do this?" → no answer
- **Fix:** Added VERSION.md to track evolution
- **Learning:** Decision history is as important as code

---

## Constraints Learned

### Constraint 1: **Token Budget is Real**
- Large files cost tokens (AI reasoning slower)
- Implication: Keep files focused, remove bloat, never over-document
- Solution: 18 files, 412KB total (was 39 files, 580KB)

### Constraint 2: **AI Reasoning Scales Linearly with Agent Count**
- 15 agents = slower decisions than 10 agents
- Implication: Only activate needed agents, keep count minimal
- Solution: Auto-selection ensures only active agents are in context

### Constraint 3: **State Decay Without Discipline**
- Without STATE.md updates: work gets lost between sessions
- Implication: Force STATE.md updates as mandatory completion step
- Solution: EXECUTION_RULES.md makes updates non-negotiable

### Constraint 4: **Scope Creep Kills MVP Timeline**
- Without QUALITY_GATE: features expand, overengineering happens
- Implication: Gate every task, reject overengineering
- Solution: QUALITY_GATE.md blocks unnecessary work

---

## Rules Extracted

1. **Minimal is Better** — Complexity should earn its place
2. **Automation > Configuration** — Remove friction through automation
3. **Boot Sequence is Law** — Never skip it, always repeatable
4. **State is Sacred** — Update it religiously, never lose it
5. **One Responsibility Per Agent** — No agent overlaps, clear routing
6. **MVP First, Everything Else Later** — Ship before perfecting
7. **Document Decisions, Not Instructions** — Why matters more than how

---

## Future Decisions to Track

When you make a major decision:
1. Note the decision here
2. Explain the reasoning
3. Track the impact
4. Revisit in VERSION.md

Example format:
```
### Decision N: [Title]
- **Decision:** [What did you decide?]
- **Reasoning:** [Why did you decide this?]
- **Impact:** [What improves?]
- **Pattern:** [When to apply this again?]
```

---

*Memory is continuity. Learn from every decision, document patterns, avoid repeated mistakes.*
