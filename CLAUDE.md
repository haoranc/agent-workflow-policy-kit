# Agent Workflow Policy Kit — Agent Notes

This repo is a template for creating and maintaining **workflow policies** that make AI-driven work more repeatable.

## Where things live
- Workflow policy bundles: `docs/workflow_policies/<workflow>/`
- Bundle template: `docs/workflow_policies/policy_bundle_template/`
- Simple policies: `docs/workflow_policies/simple/`
- Examples: `docs/workflow_policies/examples/`

## Core rules (do not violate)
1) **Separation of concerns is strict**
   - `core_policy.md` = stable invariants (“must always be true”)
   - `runbook.md` = mechanics / step-by-step procedures
   - `heuristics.md` = tunable rules-of-thumb (expected to change)
   - `changelog.md` = append-only process changes

2) **Post-run update loop is required**
   - If something new is learned: update `heuristics.md`
   - If the process changes: append to `changelog.md`

3) **Portability**
   - Don’t add secrets.
   - Avoid machine-specific paths (e.g., `/Users/...`, `file:///...`) and hardcoded IPs.
   - Prefer repo-relative references.

## When asked to create a new workflow policy
1) Read:
   - `docs/workflow_policies/policy_bundle_template/README.md`
   - `docs/workflow_policies/simple/README.md`
2) Choose bundle vs. simple policy based on workflow complexity.
3) Copy the relevant template(s), replace placeholders, and keep content in the right file.
4) Ask up to **3** clarifying questions only if needed, then proceed.

