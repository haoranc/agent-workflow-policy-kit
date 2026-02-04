# Agent Workflow Policy Kit

Templates for **workflow policies** that help AI agents (and humans) run repeatable processes and avoid repeating mistakes.

Inspired by [@bcherny’s post](https://x.com/bcherny/status/2017742747067945390) and refined through my own workflow practice ([@Haoranchg](https://x.com/Haoranchg)).

## What you get
- **Policy bundle template** (for complex workflows): stable invariants + runbook + living heuristics
- **Simple policy template** (for linear workflows): one file with invariants + heuristics + changelog
- **Process heuristics**: how to maintain policies without creating a “junk drawer”
- **Example bundles**: generic bundles you can copy and adapt
- **Optional workflow wrapper**: a thin “workflow file” that points to your policy bundle

## Repository layout

```
docs/workflow_policies/
  policy_bundle_template/         # Copy this → <workflow_name>/
    README.md
    core_policy.md
    runbook.md
    heuristics.md
    changelog.md

  simple/
    README.md
    simple_policy_template.md     # Copy this → <workflow>-policy.md

  heuristics.md                   # Heuristics for maintaining policies
  examples/
    deployment/                   # Example policy bundle (generic)
    incident_response/            # Example policy bundle (generic)

.agent/
  workflows/
    workflow-template.md          # Optional wrapper template (tool-specific)
```

## Glossary
- **Core policy**: Stable invariants you don’t violate (rarely changes) — `core_policy.md`
- **Runbook**: Step-by-step mechanics for running the workflow (changes often) — `runbook.md`
- **Heuristics**: Tunable rules-of-thumb you refine over time — `heuristics.md`
- **Changelog**: Append-only log of process changes — `changelog.md`

In a “simple policy”, these live together in a single `*-policy.md` file.

## Quickstart

### Option A: Policy bundle (recommended for “real” workflows)
1. Copy `docs/workflow_policies/policy_bundle_template/` → `docs/workflow_policies/<workflow_name>/`
2. Fill in placeholders.
3. Make your workflow wrapper (doc/script/agent command) point to:
   - `docs/workflow_policies/<workflow_name>/core_policy.md`
   - `docs/workflow_policies/<workflow_name>/runbook.md`
   - `docs/workflow_policies/<workflow_name>/heuristics.md`
4. After each real run, update:
   - `heuristics.md` (new learnings)
   - `changelog.md` (process changes)

### Option B: Simple policy (for linear workflows)
1. Copy `docs/workflow_policies/simple/simple_policy_template.md` → `docs/workflow_policies/simple/<workflow>-policy.md`
2. Keep step-by-step mechanics in your workflow doc/script.
3. Enforce the post-run update loop (add or refine heuristics).

## Using with AI tools (Cursor / Claude / Codex / etc.)
The key pattern is the same regardless of tool:
1) Keep the policy bundle in `docs/workflow_policies/<workflow>/`.
2) Create a **thin wrapper** in your tool’s workflow/prompt system that:
   - points to `core_policy.md`, `heuristics.md`, and `runbook.md`
   - enforces the post-run update loop

Starter wrapper skeleton:
```markdown
## Policy (required)
Read:
- `docs/workflow_policies/<workflow>/core_policy.md`
- `docs/workflow_policies/<workflow>/heuristics.md`

Run:
- `docs/workflow_policies/<workflow>/runbook.md`

## Post-run update loop (required)
- Update `docs/workflow_policies/<workflow>/heuristics.md` if something new was learned.
- Append to `docs/workflow_policies/<workflow>/changelog.md` if the process changed.
```

If you use the `.agent/workflows/` convention, start from `.agent/workflows/workflow-template.md`.

## The operating rule (the whole point)
After each run:
1) What surprised us?  
2) What guardrail would have prevented it?  
3) What heuristic do we add/refine (or promote into core policy)?  

## Portability / safety
- Do not put secrets in policies or runbooks.
- Avoid machine-specific paths and hardcoded IPs.
- Prefer repo-relative links and placeholder variables.

## License
MIT

## Contributing
See `CONTRIBUTING.md`.
