# ENABLEMENTS.md — faggpt/root

## GHOST-HOST DOCTRINE (Mauro's orders, Nov 8, 2026 — governs everything below)

**Source of truth is the local VM / GitLab. `faggpt/root` is a scoped
GitHub outpost only — a dumb host, ghost profile.** Files sit there;
no GitHub automation is relied on, no bots fire, no bursts. Nothing in
this stack depends on GitHub automation staying up. All code tools run
locally on the VM (see VM-TOOLS.md).

Why: GitHub's AI flags instantly. Record: JohnDaWalka was locked after
GitHub automation flagged high activity volume as spam; a replacement
account was treated as a ToS violation; Truffflezz was suspended
Nov 7, 2026; GBOSS101 is spam-flagged. `faggpt` is a days-old account —
bulk automated activity is exactly the pattern that gets flagged.
Warm-up rule (Oct 28 record): fresh accounts trip GitHub abuse
detection easily — gradual, human-paced, no bursts.

**Marketplace installs are HELD / research-only** under this doctrine:
never bulk-installed. Each install is a separate, explicit order from
Mauro, done one at a time, spaced out, by Mauro signed in himself.

**Activation rule for anything in `enablements-staging/`:** one
enablement at a time, human-paced, days apart, Mauro's explicit order
each time. The staged workflows are reference-for-local-runs, not a
GitHub automation plan.

## What is ACTIVE in `.github/` (passive only)

| File | What it does |
|---|---|
| `.github/ISSUE_TEMPLATE/muse-fact-check.md` | Fact-check / error-report template (seeded from Mauro's draft) |
| `.github/ISSUE_TEMPLATE/bug_report.md` | Bug report template |
| `.github/ISSUE_TEMPLATE/feature_request.md` | Feature request template |
| `.github/ISSUE_TEMPLATE/config.yml` | Template chooser config + private security contact link |
| `.github/pull_request_template.md` | PR checklist |
| `.github/CODEOWNERS` | `@faggpt` owns everything |

There is **no `.github/workflows/`** in the active repo. Nothing fires.

Also in the repo root (passive documents, not automation):
`README.md`, `SECURITY.md`, `CONTRIBUTING.md`, `.gitignore`,
`.pre-commit-config.yaml` (local-only hooks, run on the VM),
`VM-TOOLS.md`, this file.

**License: none chosen.** License selection is Mauro's choice and is
intentionally left open; no license file was invented.

## Dependabot — DISABLED

**Dependabot is DISABLED entirely, by Mauro's order (Nov 8, 2026):
"I'm gonna disable Dependabot so we can just use them like a host as
ghosty."**

- An early draft `dependabot.yml` was written during the initial
  build, then **removed** when the correction landed — there is no
  dependabot config anywhere in this repo, active or staged.
- Reason: GitHub is a passive ghost host only; a bot opening weekly
  PRs is the opposite of ghost. Dependency bumps are manual and local.

## Staged reference copies — `enablements-staging/`

Manual-dispatch (`workflow_dispatch`) only. None triggers on push or
pull_request. Each is the reference shape for running the same tool
locally on the VM:

| Staged file | Tool | Local equivalent |
|---|---|---|
| `github/workflows/codeql.yml` | CodeQL Advanced, multi-language matrix | CodeQL CLI (install failed — see VM-TOOLS.md) |
| `github/workflows/dependency-review.yml` | Dependency review (severity ≥ high fails) | osv-scanner + trivy locally |
| `github/workflows/scorecard.yml` | OpenSSF Scorecard (SARIF, publish off) | scorecard CLI locally if ever wanted |
| `github/workflows/zizmor.yml` | zizmor workflow-security scan | `zizmor` 1.32.0 on the VM |
| `github/workflows/semgrep.yml` | Semgrep (p/default) | `semgrep` 1.184.0 on the VM |
| `github/workflows/secret-scan.yml` | TruffleHog (verified-only) + gitleaks | `gitleaks` 8.30.1 on the VM |

Known local finding: running the VM's zizmor 1.32.0 over these staged
workflows reports 44 findings (21 suppressed), mostly
`unpinned-uses` — pins here are major-version pins; full SHA pinning
is the stricter standard and is a decision for activation time, if
activation is ever ordered at all.

## Action version verification (Nov 8, 2026)

Verification budget was deliberately tiny under the ghost doctrine.
Unauthenticated GitHub API reads hit the rate limit (remaining: 0 at
check time) and **all API checks were stopped at that point**, per
Mauro's rule — unverified versions are recorded as UNVERIFIED rather
than hammering the API.

| Action | Pin used | Status |
|---|---|---|
| `semgrep/semgrep-action` | `@v1` | **VERIFIED** — releases/latest returned `v1` |
| `actions/dependency-review-action` | `@v5` | **VERIFIED** — tags API returned latest tag `v5.0.0` |
| `github/codeql-action` | `@v4` | UNVERIFIED — API rate-limited before confirmation; verify before any activation |
| `actions/checkout` | `@v4` | UNVERIFIED — API rate-limited; verify before any activation |
| `ossf/scorecard-action` | `@v2` | UNVERIFIED — API rate-limited; verify before any activation |
| `zizmorcore/zizmor-action` | `@v0` | UNVERIFIED — API rate-limited; verify before any activation |
| `trufflesecurity/trufflehog` | `@v3` | UNVERIFIED — API rate-limited; verify before any activation |
| `gitleaks/gitleaks-action` | `@v2` | UNVERIFIED — API rate-limited; verify before any activation |

(VM tool versions were verified without the API, via each project's
`releases/latest` redirect and by running `--version` — see
VM-TOOLS.md.)

## Repo Settings toggles — ONLY with faggpt auth, ONLY on Mauro's order

None of these have been enabled. Each is a separate, explicit,
one-at-a-time order from Mauro, signed in as faggpt. They are listed
so the queue is known, not as a plan to bulk-enable:

1. **Private vulnerability reporting** (Settings → Code security) —
   makes the SECURITY.md reporting path live.
2. **Secret scanning + push protection** (Settings → Code security) —
   note the local gitleaks scan already covers this repo without it.
3. **Branch protection on `main`** (Settings → Branches) — require PR,
   require status checks (only meaningful if workflows ever activate).
4. **Actions permissions** (Settings → Actions) — currently moot:
   no active workflows. If anything is ever staged in, set to
   "Allow specified actions" rather than all.
5. **Dependabot alerts** — **NOT queued. Dependabot is DISABLED**
   (see above). Listed only so nobody re-enables it by reflex.

## Marketplace queue — HELD / research-only

**Nothing below is installed. Nothing below is a bulk-install plan.**
Each entry is what the app *would* add. Any install is a separate
explicit order from Mauro, one at a time, spaced out, Mauro signed in.

Priority order = value to a public repo if the ghost doctrine ever
relaxes for that one item.

### AI code review
1. **CodeRabbit** — https://github.com/marketplace/coderabbitai —
   AI PR reviews with line-by-line comments; free for public/open-source repos.
2. **Qodo Merge (formerly Codium PR-Agent)** — https://github.com/marketplace/qodo-merge —
   AI PR review, describe, and suggestion tool; free tier exists, full features paid — **paid tiers flagged**.
3. **Sourcery** — https://github.com/marketplace/sourcery-ai —
   AI review + automatic refactoring suggestions; free for public repos, paid for private.

### Security / secrets scanning
4. **Socket** — https://github.com/marketplace/socket-security —
   Supply-chain / dependency risk scanning on PRs; free for public repos.
5. **GitGuardian** — https://github.com/marketplace/gitguardian —
   Secrets detection in PRs and history; free tier for small/public use, paid beyond — **paid tiers flagged**.
6. **Semgrep (AppSec Platform)** — https://github.com/marketplace/semgrep —
   Cloud Semgrep results/triage on top of the OSS scanner; free tier exists (local OSS semgrep already covers the scanning itself).
7. **Snyk** — https://github.com/marketplace/snyk —
   Dependency + code vulnerability scanning; limited free tier, effectively **paid-leaning — flagged**.

### Code quality / coverage
8. **Codecov** — https://github.com/marketplace/codecov —
   Coverage reporting on PRs; free for public/open-source repos.
9. **SonarQube Cloud (SonarCloud)** — https://github.com/marketplace/sonarqube-cloud —
   Code quality + security analysis; free for public repos.
10. **Coveralls** — https://github.com/marketplace/coveralls —
    Coverage history and PR comments; free for open-source repos.
11. **DeepSource** — https://github.com/marketplace/deepsource-autofix —
    Static analysis + autofix; free for public repos, paid for private.
12. **Codacy** — https://github.com/marketplace/codacy —
    Automated code quality review; **paid-leaning — flagged**.

### Dependency management
13. **Renovate (Mend)** — https://github.com/marketplace/renovate —
    Automated dependency-update PRs, highly configurable; free.
    **Note:** a bot that opens PRs conflicts with the ghost doctrine
    and with Dependabot being disabled — research-only, do not queue
    for activation without Mauro re-opening the automation question.
14. **Dependabot** — native, not Marketplace — **DISABLED by Mauro's
    order.** Listed to close the category, not to enable.
