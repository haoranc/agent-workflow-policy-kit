---
description: Template workflow wrapper pointing to a policy bundle
---

# Workflow: <workflow>

## Policy (required)
Read:
- `docs/workflow_policies/<workflow>/core_policy.md`
- `docs/workflow_policies/<workflow>/heuristics.md`

Run:
- `docs/workflow_policies/<workflow>/runbook.md`

## Post-run update loop (required)
- Update `docs/workflow_policies/<workflow>/heuristics.md` if something new was learned.
- Append to `docs/workflow_policies/<workflow>/changelog.md` if the process itself changed.
