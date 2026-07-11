## 2026-07-11 - Git Argument Injection in Branch Names
**Vulnerability:** The PR branch name and base branch name derived from GitHub PR metadata were being directly passed as command-line arguments to git commands like \`git checkout\` and \`git rebase\` without validation.
**Learning:** Branch names starting with a hyphen (e.g. \`-b\`) can be interpreted as flags by git, allowing an attacker to inject unintended flags (like executing scripts with a malicious configuration) via a pull request.
**Prevention:** Always validate branch names sourced from external entities (like GitHub APIs) to ensure they do not start with a hyphen before using them in git shell commands.
