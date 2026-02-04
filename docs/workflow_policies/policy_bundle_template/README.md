# Workflow Policy Template

This folder is a copyable template for creating a **policy bundle** for a workflow.

## How to use
1. Copy this folder to: `docs/workflow_policies/<workflow_name>/`
2. Rename placeholders inside files.
3. Point your workflow doc to `docs/workflow_policies/<workflow_name>/README.md`
4. Enforce the "post-run update loop" (validations + heuristic refinement).

## Bundle layout
- `README.md` — pointers + file contract (what the workflow must read/write)
- `core_policy.md` — stable principles / invariants (rarely change)
- `runbook.md` — step-by-step operating instructions (procedural)
- `heuristics.md` — tunable rules of thumb (expected to evolve)
- `changelog.md` — short log of policy updates (append-only)

