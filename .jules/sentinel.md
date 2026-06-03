## 2026-06-03 - Git Argument Injection Risk in PR Metadata
**Vulnerability:** Branch names from remote PRs (`headRefName`, `baseRefName`) were directly processed. A malicious branch name like `-oProxyCommand=...` could inject options into subsequent git commands when checked out or fetched.
**Learning:** External or remote input used as branch names for CLI commands MUST be validated to ensure they cannot be parsed as flags (e.g. they shouldn't start with hyphens).
**Prevention:** Explicitly check `str.startswith("-")` on branch and base names fetched from GitHub API before passing them into git command execution contexts.
