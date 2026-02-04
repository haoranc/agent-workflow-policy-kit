# Policy: Code Review (Example)

> This is a filled-in **simple policy** example. Copy it and rename it to match your workflow.
>
> **Workflow**: Your code review / PR review runbook (e.g., `workflows/code-review.md`)

## 1) Core Principles (Invariants)
*Stable rules that rarely change.*
- [ ] **Quality bar is explicit**: Don’t merge if the change would break core behavior or materially degrade reliability/perf.
- [ ] **Tests are required**: If tests can reasonably be added/updated, they must be. If not, record why and how risk is mitigated.
- [ ] **Security and privacy first**: No secrets in code/logs; validate authn/authz boundaries; avoid leaking sensitive data.
- [ ] **Risk is owned**: Higher-risk changes require a clear rollback/mitigation plan (or an explicit reason it’s not applicable).
- [ ] **Review requires understanding**: Don’t approve what you can’t explain at a high level; ask for context or a smaller diff.

## 2) Heuristics (Tuning)
*Mutable rules of thumb & configuration.*
- [ ] **H1 — Review depth scales with risk**: Spend more time on changes touching auth, billing, data integrity, and infra/config.
- [ ] **H2 — Large diffs need a “tour”**: If the PR is big, request a short overview (what changed, why, and how to test).
- [ ] **H3 — Prefer small PRs**: If it’s hard to review, ask to split it (or review in staged slices with clear boundaries).
- [ ] **H4 — Follow-ups must be tracked**: “Fix later” is OK only if it’s non-critical and has an owner + tracking item.
- [ ] **H5 — Default response time**: Acknowledge within 1 business day; if urgent, explicitly escalate/ping.

## 3) Changelog
- **2026-02-04**: Initial example policy creation.

