# VM-TOOLS.md — code tools installed locally on the VM

All tools run **locally** — none of this depends on GitHub's systems
(ghost-host doctrine, see ENABLEMENTS.md). Installed Nov 8, 2026.

Locations: release binaries in `~/workspace/tools/bin/`;
Python tools in the venv `~/workspace/tools/code-venv/`
(symlinked from `~/workspace/tools/bin/`).

## Installed — verified by running `--version`

| Tool | Version | How verified | Source |
|---|---|---|---|
| semgrep | 1.184.0 | `semgrep --version` → `1.184.0` | pip, venv `~/workspace/tools/code-venv` |
| zizmor | 1.32.0 | `zizmor --version` → `zizmor 1.32.0` | pip, same venv |
| pre-commit | 4.7.0 | `pre-commit --version` → `pre-commit 4.7.0` | pip, same venv |
| gitleaks | 8.30.1 | `gitleaks version` → `8.30.1` | GitHub release binary → `~/workspace/tools/bin/gitleaks` |
| trivy | 0.76.2 | `trivy --version` → `Version: 0.76.2` | GitHub release binary → `~/workspace/tools/bin/trivy` |
| actionlint | 1.7.12 | `actionlint --version` → `1.7.12` | GitHub release binary → `~/workspace/tools/bin/actionlint` |
| osv-scanner | 2.7.0 | `osv-scanner --version` → `osv-scanner version: 2.7.0` | GitHub release binary → `~/workspace/tools/bin/osv-scanner` |
| shellcheck | 0.11.0 | `shellcheck --version` → `version: 0.11.0` | GitHub release binary → `~/workspace/tools/bin/shellcheck` |

Tool release tags were confirmed via each project's public
`releases/latest` redirect (not the GitHub API, which was
rate-limited and stopped per Mauro's rule).

Proof they work locally: `actionlint` over the staged workflows
exits clean; `zizmor --offline` over the staged workflows runs and
reports 44 findings (mostly unpinned-uses — see ENABLEMENTS.md);
`gitleaks detect` was run over this repo before its first push
(result recorded in the commit/push report).

## Failed / partial

| Tool | Result |
|---|---|
| CodeQL CLI bundle | **FAILED.** Latest release is v2.27.4 (via `releases/latest` redirect), but the bundle asset could not be fetched: both `…/download/v2.27.4/codeql-bundle-linux64.tar.gz` and `…/download/codeql-bundle-latest/codeql-bundle-linux64.tar.gz` returned **404**, and enumerating the release's real asset names needs the GitHub API, which was rate-limited (remaining 0) and stopped per Mauro's no-hammering rule. Size check therefore never got a live asset to measure. Retry path: one API read after the rate-limit window resets, then a single download if the bundle is < 1 GB. |
| `gh extension install github/gh-codeql` | **PARTIAL / unverified.** The extension cloned without gh auth into `~/.local/share/gh/extensions/gh-codeql` (files on disk), but `gh` on this VM is **not logged into any GitHub host** (`gh auth status`: "You are not logged into any GitHub hosts"), and `gh extension list` refuses to run until `gh auth login` or a `GH_TOKEN` exists. No auth was attempted. Treat the extension as not usable until Mauro decides on gh auth. |
| trufflehog (CLI binary) | Not in the original install list (only its staged workflow reference exists); not installed. gitleaks covers local secret scanning. |
