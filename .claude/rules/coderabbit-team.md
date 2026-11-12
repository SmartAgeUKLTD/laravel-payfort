# CodeRabbit Team plan (org SmartAgeUKLTD, since 2026-11-12)

Same file in every SmartAgeUKLTD repo and branch. Applies to every PR Claude opens or works on.

- Plan: Team. Limit about 8 PR reviews per hour per author (check `cr usage --agent` or PR comment `@coderabbitai rate limit`). Paid overflow reviews and Deep Scan are OFF: when the limit is hit, wait for the stated time, then `@coderabbitai review`. Never `--use-credits`.
- "Review limit reached" or "Review skipped" = NOT green. Wait or trigger `@coderabbitai review`, then re-check.
- Pre-merge checks: read the checks table in the walkthrough. Fix every failed custom check before asking to merge: "No secrets or personal data", "Rollback for database changes", "Tests for behavior changes", "Production safety notes", "No em or en dashes in human text". Put risk, verification and rollback in the PR description.
- Use Team finishing touches (included, no extra cost), one comment each, first run only:
  - `@coderabbitai generate unit tests` when logic changed and tests are missing. Review the generated tests, run them, keep only correct ones.
  - `@coderabbitai simplify` on large or complex diffs. Accept only behavior-preserving changes.
  - `@coderabbitai resolve merge conflict` on conflicts; verify the result and rerun tests.
  - `@coderabbitai fix-ci` when CI fails; review the stacked fix before merging.
  - `@coderabbitai plan` on a GitHub issue before building a feature.
- Do not reply to or steer those runs with follow-up instructions, and never use `@coderabbitai autofix`, the Slack bot, Coding Agent or Automations: follow-up turns and agents bill per minute.
- Auto approval is OFF: CodeRabbit never approves. Merge only when CodeRabbit is green (Actionable comments 0, checks pass) and tests pass.
- `@coderabbitai configuration` shows the resolved config; `@coderabbitai help` lists commands.
