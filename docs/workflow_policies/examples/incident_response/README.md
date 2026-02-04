# Incident Response Workflow Policy Bundle (Example)

This is a **generic** example bundle showing how to structure a coordination-critical workflow.

## Files
- `core_policy.md` — stable invariants (rarely change)
- `runbook.md` — procedural steps used during an incident
- `heuristics.md` — living rules-of-thumb to refine after each run
- `changelog.md` — append-only updates

## File contract (minimum bar)
Every incident response run should:
1) Read:
   - `core_policy.md`
   - `heuristics.md`
2) Maintain:
   - a timestamped timeline of actions/observations
   - a single incident owner (IC) and clear comms owner
3) Update (only if needed):
   - `heuristics.md` when something new is learned
   - `changelog.md` when you change the process itself

## Where artifacts usually live (example)
- Incident reports: `docs/operations/incidents/`
- Runbooks: `docs/operations/`
