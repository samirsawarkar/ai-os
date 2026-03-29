# VERSION.md — Project Evolution

> Track system maturity, decisions, and changes over time.

---

## Current Version

**v0.1.0** — Initial release

- 10 core agents
- Auto-selection engine
- Boot sequence
- Execution workflow
- Clean structure (18 files, 412KB)

---

## Version History

### v0.1.0 (Initial Release)
- **Date:** 2026-03-29
- **What Changed:**
  - 10 core agents established (planner, architect, engineer, reviewer, debugger, optimizer, security, database, backend, devops)
  - Auto-selection engine (no manual toggles)
  - Execution engine in AGENTS.md
  - Cleaned up from 39 files → 18 files (54% reduction)
  - Single README (no documentation bloat)
- **Why:** Aggressive simplification for production use
- **Impact:** System ready for MVP-focused execution without noise

---

## Version Bump Rules

**Patch (v0.1.1):**
- Bug fixes
- Small improvements
- Documentation clarity

**Minor (v0.2.0):**
- New agent added
- New workflow added
- New execution pattern

**Major (v1.0.0):**
- Stable release (used by 10+ projects)
- Proven performance
- Production hardened

---

## How to Update

1. After completing a major feature or fix
2. Increment version in header
3. Add new entry below with:
   - What changed (brief)
   - Why it changed (reasoning)
   - Impact (what improves)
4. Keep history immutable (never delete old entries)

---

## Archive

None yet (first release).

---

*Version control is continuity. Never lose track of why decisions were made.*
