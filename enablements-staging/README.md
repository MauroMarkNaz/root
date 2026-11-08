# enablements-staging — REFERENCE ONLY, NOT ACTIVE

Everything in this folder is a **staged reference copy** under
Mauro's ghost-host doctrine (see `../ENABLEMENTS.md`):

- GitHub (`faggpt/root`) is a dumb, passive host. Files sit there;
  no GitHub automation is relied on, no bots fire, no bursts.
- The workflow copies in `github/workflows/` are
  **reference-for-local-runs**: each tool (CodeQL, Semgrep,
  TruffleHog, gitleaks, Scorecard, dependency-review, zizmor) is
  run locally on the VM instead (see `../VM-TOOLS.md`).
- Every staged workflow is `workflow_dispatch` (manual) only —
  none triggers on push or pull_request, ever.
- Activation, if Mauro ever orders it, is: **one enablement at a
  time, human-paced, days apart, Mauro's explicit order each time.**
- **Dependabot is DISABLED entirely** by Mauro's order
  (Nov 8, 2026). An earlier staged `dependabot.yml` was removed;
  there is intentionally no dependabot config anywhere in this repo.
