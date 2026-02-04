# Incident Response Core Policy (Example)

**Purpose:** Stable, cross-run invariants for handling incidents safely and consistently.

## Invariants

### 1) Declare an owner and roles
- Every incident has a single Incident Commander (IC).
- Assign a comms owner and a scribe/timekeeper when possible.
- If roles are unfilled, the IC covers them explicitly.

### 2) Stabilize first; prefer reversible actions
- Prioritize mitigation and user impact reduction over root-cause discovery.
- Prefer reversible actions (rollback, disable feature, reduce blast radius) over risky changes.

### 3) Maintain a single source-of-truth timeline
- Record timestamps for key events, actions taken, and observations.
- Ensure decisions have an owner and a rationale captured.

### 4) Communication is part of the response
- Stakeholders receive updates on a predictable cadence.
- External/customer-facing comms are coordinated and reviewed.

### 5) Preserve evidence when possible
- Avoid destructive actions (e.g., deleting data/logs) unless required to stabilize.
- Capture enough context (logs/metrics/config/version) to support later analysis.

### 6) Secrets never appear in output
- Never paste tokens, passwords, API keys, or private customer data into incident docs/chats.
- Prefer referencing secret *names* and where they are stored.

### 7) Close the loop after resolution
- Schedule a post-incident review if impact warranted it.
- Convert learnings into guardrails (update `heuristics.md` and/or the runbook).

## Non-goals
- Tool-specific commands (put those in `runbook.md` and keep them environment-specific).
- Organization-specific escalation paths (keep this example generic).
