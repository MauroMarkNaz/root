# Contributing

This is Mauro Fanelli's scoped repo for Truffle (Muse) under the
`faggpt` account. Contributions happen on Mauro's direction.

## Ground rules

1. **Checked facts only.** One claim, one source. Verdicts are binary:
   TRUE / FALSE / UNVERIFIED (with the reason). Use the
   *Muse — Fact check / error report* issue template for claim disputes.
2. **No secrets in the repo.** Ever. Tokens and passwords go in the
   Secure Vault, never in code, issues, or PRs. The secret-scan
   workflows (TruffleHog + gitleaks) will flag violations.
3. **Free and open first.** Prefer free / free-for-public-repos,
   open-source tooling. Flag paid-only tools before proposing them.
4. **Dependabot is DISABLED** (Mauro's order, Nov 8, 2026 — GitHub
   is a passive ghost host only). Dependency bumps are manual and
   local. Staged workflow pins are by major version; do not silently
   upgrade pins, and do not activate a staged workflow without
   Mauro's explicit per-item order.

## Workflow

- Branch off `main`, open a PR using the PR template, list the exact
  checks you ran.
- Local checks that mirror CI: `pre-commit run --all-files`,
  `actionlint`, `shellcheck`, `semgrep`, `gitleaks`, `trivy`,
  `osv-scanner` — see VM-TOOLS.md for what is installed on the VM.
- Issues: bug report / feature request / fact-check templates are in
  `.github/ISSUE_TEMPLATE/`.

## License

No license has been chosen yet. That decision is Mauro's; no license
is implied by contributing.
