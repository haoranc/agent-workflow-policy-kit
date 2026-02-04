# Deployment Heuristics (Example)

**Purpose:** Tunable rules-of-thumb derived from real deployments.

## How to update
After each deployment, answer:
1) What surprised us? (failed health check, missing config, slow startup)
2) What guardrail would have prevented it?
3) What heuristic should be refined?

Add entries with:
- Date
- Context (service/environment)
- Observation
- Heuristic change
- Expected impact

---

## Heuristic rules

### H1: Warmup window for health checks
Wait a short warmup period after restart before declaring a service unhealthy.

### H2: Config changes require a full restart/recreate
If environment variables or runtime config changed, prefer recreate over restart (depending on your stack).

### H3: Verify the “control plane” too
If you rely on external systems (queues, DB, cloud functions), verify them explicitly—don’t assume “service logs look fine” means the pipeline works.

---

## Learned failure modes (append)
- (Add real incidents here with date + fix + guardrail.)
