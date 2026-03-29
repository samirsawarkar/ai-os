# RULES.md — System Law
# These rules apply to ALL agents, ALL commands, ALL outputs. No exceptions.

---

## PRIME DIRECTIVES

```
1.  Activate minimum agents needed — not maximum possible
2.  Working software over elegant software
3.  MVP before optimization — always
4.  Simple over complex — always
5.  One task at a time — finish it, then move on
6.  Never rebuild completed components
7.  CONTEXT.md and PROJECT_PLAN.md override all agents
8.  CRITICAL issues block everything — no exceptions
9.  Update STATE.md after every action
10. Do not add features that aren't in scope
```

---

## AGENT RULES

```
ACTIVATION
  ✅ Only activate agents listed in PROJECT_PLAN.md Section 3
  ✅ Use minimum agents — if engineer can do it, don't add backend
  ❌ Never activate optimizer or performance before MVP is complete
  ❌ Never activate tester during active development

BEHAVIOR
  ✅ Each agent works only in its own layer
  ✅ Conflicts resolved by authority hierarchy in AGENTS.md
  ✅ Inactive agents are ignored — not fallback options
  ❌ Agents do not override CONTEXT.md product decisions
```

---

## CODING RULES

### Do
```
✅ Flat code — minimize nesting depth (max 3 levels)
✅ Functions under 30 lines
✅ One function = one responsibility
✅ Return early to avoid nested conditionals
✅ Name things for what they do, not how they work
✅ Handle errors explicitly
✅ Use environment variables for all config
✅ Comment WHY, not WHAT
✅ Prefer stdlib over external library when reasonable
```

### Do Not
```
❌ Abstract until you have 3+ real use cases
❌ Add config that isn't needed right now
❌ Use global mutable state
❌ Nest conditionals more than 3 levels
❌ Write tests for code that's about to change
❌ Add a framework if a function will do
❌ Hard-code credentials, URLs, or environment-specific values
```

---

## ARCHITECTURE RULES

```
LAYERS (respect the boundaries)
  Routes     → HTTP only. No business logic. Calls services.
  Services   → All business logic. No HTTP context. Calls models.
  Models     → Data structure only. No logic.
  Utils      → Pure functions. No side effects. No DB calls.

WHAT CROSSES LAYERS
  Routes → Services: function call with validated input
  Services → DB: query via ORM or parameterized SQL
  Services → External: wrapped calls with error handling
  Nothing else crosses layers

FORBIDDEN
  ❌ Business logic in routes
  ❌ DB queries in routes
  ❌ HTTP exceptions in services
  ❌ Circular imports
  ❌ Microservices for MVP
  ❌ Shared mutable state between modules
```

---

## API RULES

```
URL DESIGN
  ✅ /api/v1/resources       → collection
  ✅ /api/v1/resources/{id}  → single resource
  ❌ /api/v1/getResource
  ❌ /api/v1/resource/create

STATUS CODES
  200 → success (GET, PATCH, PUT)
  201 → created (POST)
  204 → deleted (DELETE)
  400 → bad request (client validation error)
  401 → not authenticated
  403 → authenticated, not authorized
  404 → not found
  500 → server error (never expose internals)

ERROR RESPONSE (always this shape)
  { "error": "message", "code": "SNAKE_CASE_CODE", "field": "optional" }
```

---

## SECURITY BASELINE (non-negotiable)

```
✅ Passwords: bcrypt only (never MD5/SHA/plain)
✅ JWTs: must have expiry, secret from env var
✅ SQL: parameterized queries only
✅ Input: validate all user input before processing
✅ CORS: explicit origins (never wildcard in production)
✅ Secrets: env vars only, never in source code
✅ Logs: never log passwords, tokens, or PII
```

---

## WHAT TO AVOID (BY CATEGORY)

| Category       | Avoid                          | Reason                              |
|----------------|--------------------------------|-------------------------------------|
| Architecture   | Microservices                  | Solo dev overhead                   |
| Architecture   | Event-driven pre-scale         | Complexity without benefit          |
| Database       | Raw SQL string interpolation   | SQL injection                       |
| Database       | SELECT *                       | Hides schema, wastes bandwidth      |
| Database       | No migrations                  | Untracked, irreversible changes     |
| Code           | Premature abstraction          | Optimizes for nonexistent problems  |
| Code           | Complex DI frameworks          | Unnecessary for solo MVP            |
| Code           | print() for logging            | Not structured, lost in production  |
| Agents         | Optimizer before MVP           | Wastes time on incomplete system    |
| Agents         | Tester during active dev       | Tests become stale immediately      |
| Infra          | Kubernetes                     | Never for solo MVP                  |
| Infra          | Multi-region before scale      | Solution to a future problem        |

---

## MVP COMPLETE DEFINITION

An MVP is complete when ALL of the following are true:
```
[ ] Core user flow works end-to-end
[ ] No CRITICAL bugs (per reviewer + security)
[ ] App is deployed and accessible by a real user
[ ] Errors are logged and visible
[ ] No hardcoded secrets or credentials
```
Nothing else is required. Ship it.
