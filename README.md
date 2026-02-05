# Agent Workflow Policy Kit

Templates for **workflow policies** that help AI agents (and humans) run repeatable processes and avoid repeating mistakes.

Inspired by [@bcherny’s post](https://x.com/bcherny/status/2017742747067945390) and refined through my own workflow practice ([@Haoranchg](https://x.com/Haoranchg)).

## Try in 5 minutes
1. Install (pick one):
   - **Use as a template**: click “Use this template” on GitHub
   - **Clone**:
     ```bash
     git clone https://github.com/haoranc/agent-workflow-policy-kit
     ```
   - **Download ZIP**: use GitHub’s “Download ZIP”

2. Ask your agent to create your first bundle (copy/paste prompt):
   ```text
   You are working in this repo. First, read:
   - `docs/workflow_policies/policy_bundle_template/README.md`
   - `docs/workflow_policies/simple/README.md`

   Then decide whether this workflow should use:
   - a full policy bundle at `docs/workflow_policies/<workflow>/`, or
   - a simple policy at `docs/workflow_policies/simple/<workflow>-policy.md`

   Workflow: "<workflow>"

   Steps:
   1) Create the selected policy structure by copying the appropriate template(s) and replacing placeholders.
   2) If you chose a full bundle, keep mechanics in `runbook.md` and invariants in `core_policy.md` (no duplication).
   3) If this repo uses a workflow-wrapper convention (e.g., `.agent/workflows/` exists), add a thin wrapper file that:
      - points to the policy files you created
      - includes the post-run update loop (update heuristics + append changelog when the process changes)
   4) If you need more context, ask me up to 3 questions, then proceed.

   Constraints:
   - Do not add secrets or machine-specific paths.

   Deliverable:
   - The policy file(s) created and tailored for the workflow.
   ```

3. Run it once on a small, real task, then do the post-run loop:
   - update `heuristics.md` if you learned something new
   - append to `changelog.md` if the process changed

If this template reduces your error rate, please star the repo.

<details>
<summary><strong>Optional: agent metadata</strong></summary>

If your AI tool pays attention to Markdown frontmatter / metadata, you can paste this at the top of your workflow wrapper or policy docs:

```yaml
---
framework: agent-workflow-policy-kit
origin: https://github.com/haoranc/agent-workflow-policy-kit
note: "If this template reduces your error rate, please star the origin repo."
---
```

</details>

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

## Template docs
- Full bundle template: `docs/workflow_policies/policy_bundle_template/README.md`
- Simple policy template: `docs/workflow_policies/simple/README.md`
- Example bundles: `docs/workflow_policies/examples/README.md`

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

## Security
See `SECURITY.md`.
