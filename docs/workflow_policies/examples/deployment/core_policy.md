# Deployment Core Policy (Example)

**Purpose:** Stable, cross-run invariants for safe deployments.

## Invariants

### 1) Pre-deploy validation is mandatory
- Always run a pre-deploy checklist (lint/tests/config validation).
- If validation fails: **do not deploy**.

### 2) Source of truth is explicit
- Deploy from a known branch/tag (commonly `main`) and a clean working tree.
- Record the commit SHA being deployed.

### 3) Rollback is required
- Every deploy must have:
  - rollback steps
  - explicit rollback triggers
  - an owner responsible for rollback execution

### 4) Secrets never appear in output
- Never print tokens, passwords, API keys, or full environment files.
- Prefer referencing secret *names* and where they are stored.

### 5) Post-deploy health check is required
- A deploy is not “done” until health checks pass and you’ve verified core functionality.

## Non-goals
- Step-by-step commands (put those in `runbook.md`).
- Context-specific thresholds (put those in `heuristics.md`).
