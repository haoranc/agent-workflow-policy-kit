# Deployment Runbook (Example)

**Purpose:** Step-by-step procedure for running deployments consistently.

> Policy: read `core_policy.md` before every deploy | update `heuristics.md` if you learned something

## Inputs
- Target environment (prod/staging)
- Release artifact (image tag, build output, commit SHA)
- Monitoring access (logs/metrics/alerts)

## Procedure
1) Load the policy
   - Read `core_policy.md`
   - Read `heuristics.md`

2) Pre-flight
   - Run your pre-deploy checklist (lint/tests/config validation)
   - Confirm the deploy target + commit SHA/artifact
   - Write down rollback steps + triggers

3) Execute deploy
   - Deploy the artifact (replace with your platform steps)

4) Post-deploy verification
   - Check service health
   - Verify end-to-end behavior (a real “smoke test”)
   - Watch logs/alerts during the initial window

5) Post-run update loop (required)
   - Update `heuristics.md` if anything surprised you
   - Update `changelog.md` if you changed the process itself
