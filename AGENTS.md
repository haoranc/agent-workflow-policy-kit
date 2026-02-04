# Agent Workflow Policy Kit

This repository is a **template** for creating and maintaining **workflow policies** that help AI agents (and humans) run repeatable processes and avoid repeating mistakes.

## How to use this repo
- For complex workflows, copy `docs/workflow_policies/policy_bundle_template/` → `docs/workflow_policies/<workflow_name>/` and fill in placeholders.
- For simple linear workflows, copy `docs/workflow_policies/simple/simple_policy_template.md` → `docs/workflow_policies/simple/<workflow>-policy.md`.

## Operating rule (the whole point)
After every real run:
1) Capture what surprised you (or what went wrong).
2) Add/adjust a heuristic (or promote it into core policy if it’s an invariant).
3) Append a short entry to the policy changelog if the process changed.

## Safety / portability
- Do not include secrets in policies or runbooks.
- Avoid machine-specific paths (e.g., `file:///Users/...`) and hardcoded IPs.
- Prefer repo-relative links and placeholder variables.
