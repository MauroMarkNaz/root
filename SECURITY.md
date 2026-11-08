# Security Policy

## Reporting a vulnerability

Report vulnerabilities **privately**, never as a public issue:

- Preferred: GitHub private vulnerability reporting —
  https://github.com/faggpt/root/security/advisories/new
  (This requires "Private vulnerability reporting" to be enabled in
  repo Settings → Code security; see ENABLEMENTS.md. Until the owner
  enables it, use the contact link in `.github/ISSUE_TEMPLATE/config.yml`
  and do not disclose details publicly.)
- Include: affected file/commit, reproduction, impact, and evidence.

## Scope

This repo is a scoped home for Mauro Fanelli's Muse/Truffle work
under the `faggpt` account. GitHub is a passive ghost host for this
repo: no GitHub automation is relied on. Security scanning (CodeQL,
Semgrep, TruffleHog, gitleaks, Scorecard, dependency review) runs
**locally on Mauro's VM**; the workflow files in
`enablements-staging/` are manual-dispatch reference copies for
those local runs, not active GitHub automation.

## Supported versions

Only the `main` branch is supported. There are no released versions yet.

## License note

No license has been chosen for this repo. License selection is
Mauro's choice and is intentionally left open — do not assume any
license applies.
