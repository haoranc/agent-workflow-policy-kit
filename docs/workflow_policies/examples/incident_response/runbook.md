# Incident Response Runbook (Example)

**Purpose:** Step-by-step procedure for handling incidents with clear ownership and documentation.

> Policy: read `core_policy.md` before starting | update `heuristics.md` if you learned something

## Inputs
- Affected service/system
- Observed symptoms and impact
- Access to logs/metrics/alerts (as applicable)
- On-call / escalation access (as applicable)

## Procedure
1) Load the policy
   - Read `core_policy.md`
   - Read `heuristics.md`

2) Declare the incident
   - Assign Incident Commander (IC) and comms owner (and scribe if available)
   - Set a severity level (use your local rubric)
   - Create an incident channel/bridge and an incident doc
   - Start a timestamped timeline (even if rough)

3) Triage (timebox as needed)
   - Identify the user/customer impact and current blast radius
   - Check recent changes (deploys/config/feature flags) relevant to the system
   - Gather quick signals (key dashboards, error rates, saturation, logs)

4) Mitigate (stabilize)
   - Prefer low-risk, reversible actions:
     - rollback recent changes
     - disable/limit a feature
     - reduce traffic or shed load
     - fail open/closed according to your safety posture
   - Validate mitigation via health checks and end-to-end behavior

5) Communicate
   - Post periodic updates with: impact, current status, next check-in time, owner
   - Escalate/pull in owners of dependent systems as needed

6) Resolve and close
   - Confirm systems are stable and monitoring is green
   - Document the resolution, contributing factors, and remaining risks
   - Capture follow-ups (tickets/tasks) with owners and deadlines

7) Post-run update loop (required)
   - Update `heuristics.md` if anything surprised you (new failure mode, missing signal, unclear severity)
   - Update `changelog.md` if you changed the process itself (new step, new role, new checklist)
