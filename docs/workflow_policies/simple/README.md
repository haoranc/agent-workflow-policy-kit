# Simple Workflow Policies

This directory contains **lightweight, single-file policies** for simple workflows.

## When to use
Use a "Simple Policy" when the workflow:
- Is linear or low-complexity.
- Does not require a separate runbook (steps are in the workflow file).
- Needs only a few stable principles or tuning heuristics.

## How to use
1. Copy the template below to `docs/workflow_policies/simple/<workflow>-policy.md`.
2. Rename placeholders inside the file.
3. Point your workflow doc to `docs/workflow_policies/simple/<workflow>-policy.md`.
4. **MUST** enforce the "post-run update loop" (heuristic refinement) at the end of the workflow.

## Naming convention
The policy filename **MUST** strictly match the workflow filename.
- Workflow: `.agent/workflows/<name>.md`
- Policy: `docs/workflow_policies/simple/<name>-policy.md`

## Example
See `docs/workflow_policies/simple/code-review-policy.md` for a filled-in simple policy you can copy and adapt.

## Template

Copy this structure for new files:

```markdown
# Policy: <Workflow Name>

> **Workflow**: [.agent/workflows/<workflow>.md](.agent/workflows/<workflow>.md)

## 1. Core Principles (Invariants)
*Stable rules that rarely change.*
- [ ] Example: "Always squash merge."
- [ ] Example: "Never skip linting."

## 2. Heuristics (Tuning)
*Mutable rules of thumb & configuration.*
- [ ] **H1**: Review depth = "Senior" for critical paths.
- [ ] **H2**: Timeout = 5m for simple PRs.

## 3. Changelog
- **YYYY-MM-DD**: Initial policy creation.
```
