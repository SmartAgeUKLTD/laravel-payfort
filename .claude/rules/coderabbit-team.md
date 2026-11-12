# CodeRabbit Team plan (org SmartAgeUKLTD, since 2026-11-12)

Same file in every SmartAgeUKLTD repo and branch. Applies to every PR Claude opens or works on.

- Plan: Team. Limit about 8 PR reviews per hour per author (check `cr usage --agent` or PR comment `@coderabbitai rate limit`). Paid overflow reviews and Deep Scan are OFF: when the limit is hit, wait for the stated time, then `@coderabbitai review`. Never `--use-credits`.
- "Review limit reached", "Review skipped" or "Review failed" = NOT green. Wait or trigger `@coderabbitai review` (use `@coderabbitai full review` when the latest commit only touches excluded files but earlier commits did not), then re-check. If "skipped" or "failed" persists after one retry, check the PR author has a CodeRabbit seat and the repo is installed in CodeRabbit, then escalate to the repo admin. The merge rule below still applies.
- "No files to review" because every changed file is excluded by path_filters (confirm the skip reason in the CodeRabbit comment; an incremental review that simply found no new changes does not count) = NOT green and retrying does not help: stop and ask the owner whether to merge.
- Pre-merge checks: read the checks table in the walkthrough. Fix every failed custom check before asking to merge: "No secrets or personal data", "Rollback for database changes", "Tests for behavior changes", "Production safety notes", "No em or en dashes in human text". Put risk, verification and rollback in the PR description.
- Use Team finishing touches (included, no extra cost), one comment each, first run only:
  - `@coderabbitai generate unit tests` when logic changed and tests are missing. Review the generated tests, run them, keep only correct ones.
  - `@coderabbitai simplify` on large or complex diffs. Accept only behavior-preserving changes.
  - `@coderabbitai resolve merge conflict` on conflicts; verify the result and rerun tests.
  - `@coderabbitai fix-ci` when CI fails; review the stacked fix before merging.
  - `@coderabbitai plan` on a GitHub issue before building a feature.
- Do not reply to or steer those runs with follow-up instructions, and never use `@coderabbitai autofix`, the Slack bot, Coding Agent or Automations: follow-up turns and agents bill per minute.
- Auto approval is OFF: CodeRabbit never approves. Merge only when tests and all checks pass AND the latest commit has a successful CodeRabbit review AND no actionable CodeRabbit finding is left open: every valid finding (inline, outside-diff or body-only) is fixed; answering instead of fixing is allowed only with the reason the finding is not actionable (never "fix later"); then resolve its thread. Only exception: for "No files to review", the owner may approve merging the latest commit once tests and all checks pass; valid findings from earlier reviews must still be fixed. Where a repo has its own CodeRabbit gate (for example LOW findings marked advisory in its `.coderabbit.yaml`), the stricter rule wins: every valid finding still needs a fix or a reasoned not-actionable answer. Repo-specific gate scripts or guides (for example docs/CODERABBIT-REPORT-GUIDE.md) still apply.
- `@coderabbitai configuration` shows the resolved config; `@coderabbitai help` lists commands.
