# <WORKFLOW> Runbook

**Purpose:** Step-by-step instructions to run this workflow consistently.

## Inputs
- [ ] Where the workflow reads data from
- [ ] Required reports / artifacts
- [ ] Required templates (proposal, decision, etc.)

## Procedure
1. Load policy bundle (`README.md` pointers).
2. Identify evaluation window milestone.
3. Produce required tables / charts.
4. Draft proposal using template.
5. User review loop (iterate).
6. Approval → decision doc → config diff.
7. Deploy + monitor.
8. Record validation and refine heuristics if needed.

## Outputs (file contract)
- `docs/<domain>/proposals/...`
- `docs/<domain>/decisions/...`
- `docs/<domain>/validations/...`
- Update `docs/workflow_policies/<workflow>/heuristics.md` if new learnings.

