# Contributing

Thanks for helping improve this template repo.

## What to contribute
- Clearer wording or better structure in templates and docs
- Additional generic example bundles
- Heuristics for maintaining policies (what worked / what failed)
- Fixes to broken links or confusing instructions

## Guidelines (please keep it portable)
- **No secrets**: don’t include credentials, tokens, passwords, private URLs, or internal incident details.
- **No machine-specific paths**: avoid absolute paths like `/Users/...` and `file:///...`.
- **Keep examples generic**: prefer placeholders and vendor-neutral language.
- **Preserve separation of concerns**:
  - `runbook.md` = mechanics / steps
  - `core_policy.md` = stable invariants
  - `heuristics.md` = tunable rules-of-thumb
  - `changelog.md` = append-only process changes
- **Small, reviewable diffs**: avoid sweeping rewrites unless necessary.

## Pull request checklist
- [ ] Links are repo-relative and work.
- [ ] New examples include all bundle files (`README.md`, `core_policy.md`, `runbook.md`, `heuristics.md`, `changelog.md`).
- [ ] Dates use `YYYY-MM-DD`.
- [ ] Content is copy/paste friendly for other repos.

