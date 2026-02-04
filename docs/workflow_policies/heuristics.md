# Workflow Policy Heuristics

**Purpose:** Capture learnings and rules-of-thumb for the *practice* of creating and maintaining workflow policies.

## How to use
When migrating a workflow to a policy or iterating on an existing one, check this file for guidance on structure, content, and common pitfalls.

## Heuristics

### 1. Separation of Concerns
- **Rule:** Separation between `runbook.md` (mechanics) and `core_policy.md` (rules/invariants) must be strict.
- **Why:** Runbooks change often (tooling updates); Policies change rarely (business logic).
- **Test:** If a step says "Run command X", it belongs in the Runbook. If it says "Ensure X is true before proceeding", it belongs in the Policy.

### 2. Heuristics vs. Policy
- **Rule:** If a rule is "hard" (inviolable invariant), it goes in `core_policy.md`. If it is "soft" (tunable, context-dependent), it goes in `heuristics.md`.
- **Example:** "Do not trade on Sundays" is a Policy. "Reduce size by 50% if spread > 10bps" is a Heuristic.

### 3. Workflow Wrappers (Full Bundles)
- **Rule:** The `.agent/workflows/*.md` file should become a thin wrapper around the Policy Runbook.
- **Content:** It should strictly contain:
    1. The trigger slash command.
    2. A pointer to `docs/workflow_policies/<name>/runbook.md`.
    3. (Optional) High-level "Turbo" steps if they are purely mechanical setup.

### 4. Simple Policies (Lightweight)
- **Rule:** For linear workflows, use the `simple/` single-file structure instead of a full bundle.
- **Location:** `docs/workflow_policies/simple/<workflow>-policy.md` (Strict 1:1 naming).
- **Content:** Principles + Heuristics + Changelog.
- **Workflow Link:** The workflow file remains the "Runbook" but **MUST** link to the policy file in the header.

### 5. Naming Conventions
- **Rule:** Policy bundles (full structure) should be named after the *domain concept*, not just the verb. Simple Policies follow the workflow filename strictly.
- **Bad:** `update_trackers`
- **Good:** `performance_tracking`

### 6. Preserve Proven Flows (1:1 Migration)
- **Rule:** When migrating a critical workflow to a policy bundle, port the runbook content **1:1** initially.
- **Why:** Critical workflows (e.g., deployment) have battle-tested procedures. Restructuring during migration risks breaking what works.
- **Process:** 
    1. Copy original workflow content to `runbook.md` verbatim.
    2. Simplify the workflow file to a thin wrapper.
    3. Iterate on structure *after* migration is validated.

### 7. Avoid Machine-Specific Links
- **Rule:** Don’t use absolute `file:///...` links (or other machine-specific paths) in committed workflow/policy docs.
- **Why:** They break portability for teammates, CI, and different repo locations.
- **Preferred:** Use repo-relative references (e.g., `docs/workflow_policies/<bundle>/runbook.md`) or relative markdown links.

### 8. Large Workflows: Bundle First
- **Rule:** If a workflow is “too large”, move the bulk into a policy bundle `runbook.md` and keep `.agent/workflows/<name>.md` as a thin wrapper.
- **If previously split:** When a workflow was split for size (e.g., `<name>-finalize`), consolidate back into a single runbook and keep at most one wrapper (optional alias wrappers are OK, but must be pointer-only).
- **Why:** Prevents drift/duplication and keeps a single source of truth.

## Common Pitfalls
- **Duplication:** Copying the same "Week Calculation" bash script into multiple places. -> *Action: Centralize in a script or define as a reusable snippet in the Runbook.*
- **Hardcoded Lists:** Loops like `for SYMBOL in btc eth sol` in runbooks become stale when new symbols launch. -> *Action: Use dynamic discovery (e.g., `ls`) or add a "Check for new symbols" step.*
- **Over-Restructuring:** Reorganizing proven flows during migration introduces risk. -> *Action: Port 1:1 first, iterate later.*
- **Machine-Specific Links:** `file:///Users/...` and absolute paths make docs non-portable. -> *Action: Use repo-relative references/links.*
- **Split Workflow Drift:** Maintaining multiple workflow files for one flow causes divergence. -> *Action: Consolidate into one `runbook.md`; wrappers are pointers only.*
