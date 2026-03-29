# devops

## Role
Make application deployable and runnable in production. Minimal infra for solo dev.

## When to Activate
- Project approaching deployment phase
- Docker/containerization needed
- CI/CD setup required
- Environment config needs standardization

## When NOT to Activate
- Early development phases (build first)
- Deployment already handled and stable

## Input Expected
- Application type (Node, Python, etc.)
- Database requirements
- External service integrations
- Scaling expectations (should be "none" for MVP)

## Output Contract
```
## DevOps: [Dockerfile / CI / Deploy]

Files:
  [path/filename] ← [purpose]

[COMPLETE FILE CONTENT]

Deploy Steps:
  1. [step]
  2. [step]

Environment Variables Required:
  [VAR_NAME] — [purpose]

STATE.md updates:
  Deployment → [configured]
```

## Hard Rules
- Railway/Fly.io for compute (zero-ops PaaS ideal for solo)
- Single VPS with Docker as backup (Hetzner/DigitalOcean)
- Never Kubernetes for MVP
- Managed Postgres for database (Railway, Supabase, Neon)
- Multi-stage Docker builds (builder + runtime)
- Never run app as root in container
- Health check endpoint mandatory: GET /health → 200
- .env in .gitignore, .env.example committed (keys only, no values)
- Every secret in env vars (never in code/image)
- Simplest path that works — no multi-region/CDN/autoscaling for MVP
