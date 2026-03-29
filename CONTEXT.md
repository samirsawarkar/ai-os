# CONTEXT.md — Project Definition
# ✏️ FILL THIS IN ONCE. Do not edit during active development.
# This file is the source of truth for product decisions.

---

## Project Name
[Your project name]

## One-Line Description
[What does this build? Who is it for? What does it replace or solve?]

---

## Problem
[What is broken or missing in the world that this fixes?
 Be specific. 2–4 sentences.]

---

## Goals (MVP only)
- [ ] [The one thing that must work for this to be useful]
- [ ] [Second most important outcome]
- [ ] [Third — only if truly required for MVP]

## Non-Goals (explicit — helps prevent scope creep)
- [This system will NOT do X]
- [This system will NOT support Y]
- [This is post-MVP at earliest]

---

## Users
| Type        | Core Need                         | Volume Expectation |
|-------------|-----------------------------------|--------------------|
| [User type] | [What they need to accomplish]    | [small/medium/high]|

---

## Core Features (MVP)
1. [Feature] — [one sentence: what user can do, not how it works]
2. [Feature] — [one sentence]
3. [Feature] — [one sentence]

## Post-MVP Features
- [Feature] — [why it's deferred]
- [Feature] — [why it's deferred]

---

## Tech Stack
| Layer      | Choice                    | Reason                            |
|------------|---------------------------|-----------------------------------|
| Language   | Python 3.11               | [default — change if needed]      |
| Framework  | FastAPI                   | [async, auto-docs, fast]          |
| Database   | SQLite → Postgres         | [SQLite for dev, Postgres for prod]|
| Auth       | JWT (PyJWT)               | [stateless, simple]               |
| Frontend   | [HTML / React / None]     | [choose based on complexity]      |
| Hosting    | [Railway / Fly.io / VPS]  | [choose based on budget]          |

---

## Constraints
- Solo developer
- [Timeline]
- [Budget]
- [Platform requirement]
- [Any hard technical constraints]

---

## Success Criteria
An MVP is successful when:
- [ ] [Measurable outcome — e.g., "a user can sign up and use feature X"]
- [ ] [Measurable outcome]
- [ ] [Measurable outcome]

---

## Architecture Notes
[Any known constraints on how this must be built.
 Leave blank and let the architect agent define it.]
