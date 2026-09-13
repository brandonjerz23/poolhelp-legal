Public legal pages for the PoolHelp app, served via GitHub Pages.
Source of truth lives in the app repo (PRIVACY.md / TERMS.md / SAFETY.md and
src/constants/legal.ts) — copy changes here when those change.

## Issue autofix

`.github/workflows/issue-autofix.yml` runs Claude Code unattended whenever you
or a collaborator opens an issue (or anyone adds the `autofix` label to one).
A typo, broken link or formatting defect becomes a **draft PR** whose body
starts with `Fixes #<n>`; anything that changes what a policy says gets a
triage comment pointing at the app repo (the source of truth) and the
`needs-human` label. Nothing merges itself.

- **Setup**: one *repository* secret (Settings → Secrets and variables →
  Actions), either `CLAUDE_CODE_OAUTH_TOKEN` (from `claude setup-token`, bills
  against your subscription) or `ANTHROPIC_API_KEY` (bills per token). The
  workflow declares no environment, so an environment secret is not visible to
  it. It takes effect once merged to the default branch.
- **Model**: Fable 5.1 (`--model fable`). With an API key, Fable bills per
  token at twice Opus 5, capped at 15 USD per run. With a subscription token
  it draws on your plan limits, except on plans where Fable bills to usage
  credits: headless runs never ask first, so keep usage credits off in
  claude.ai → Settings → Usage unless you want that. Fall back with
  `--model opus`.
- **Guardrails** (`scripts/issue-autofix-prompt.md`): issue text is untrusted
  input; the agent may not touch `.github/`, `scripts/`, or add plugins,
  layouts or a `Gemfile`; 150 turns, 15 USD and 45 minutes per run, one run
  per issue at a time.
- **Re-run**: add the `autofix` label, or Actions → Issue autofix → Run
  workflow with the issue number. An issue that already has an
  `autofix/issue-<n>` branch is skipped.
