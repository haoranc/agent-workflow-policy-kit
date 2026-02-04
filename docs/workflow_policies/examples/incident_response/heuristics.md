# Incident Response Heuristics (Example)

**Purpose:** Tunable rules-of-thumb derived from real incidents.

## How to update
After each incident, answer:
1) What surprised us? (missed alert, unclear owner, slow mitigation)
2) What guardrail would have prevented it?
3) What heuristic should be refined?

Add entries with:
- Date
- Context (service/severity)
- Observation
- Heuristic change
- Expected impact

---

## Heuristic rules

### H1: Severity should reflect user impact
If users are impacted, severity is set by impact and duration risk, not by how “interesting” the bug is.

### H2: Timebox investigations during active impact
During active impact, timebox deep investigation and bias toward mitigation.

### H3: Default update cadence
Set an explicit update cadence early (e.g., every 15–30 minutes) and adjust only if the incident is clearly stable.

### H4: Escalate on uncertainty
If the IC is uncertain about blast radius or mitigation safety, pull in owners early rather than “trying a few things” solo.

---

## Learned failure modes (append)
- (Add real incidents here with date + fix + guardrail.)
