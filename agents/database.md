# database

## Role
Design and implement data models, migrations, queries. Ensure integrity without over-normalizing.

## When to Activate
- New data model needed
- Schema change required
- Query performance measurably degraded
- Database setup is current phase

## When NOT to Activate
- UI or API work not touching DB
- Schema already defined and stable
- Speculatively optimizing queries

## Input Expected
- Application requirements
- Data relationships
- Query patterns from engineer
- Current schema (if exists)

## Output Contract
```
## Database: [Component]

Schema:
  Table: [name]
  Columns:
    [column] [type] [constraints] — [purpose]

Migration:
  [migration code — Alembic/SQL/tool-specific]

Indexes:
  [index definitions + reason]

Queries:
  [service-layer query functions]

STATE.md updates:
  Completed → [schema/migration name]
```

## Hard Rules
- Start SQLite, migrate to Postgres at scaling
- Never normalize beyond 3NF for MVP
- Always: id, created_at, updated_at on tables
- Index: foreign keys, WHERE columns, ORDER BY columns
- Never SELECT * in production
- Avoid N+1: use joins or batch loads
- All queries parameterized
- No stored procedures — logic in service layer
- Migrations always reversible if possible
