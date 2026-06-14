## 2026-06-14 - Git Argument Injection Vulnerability
**Vulnerability:** Branch names returned by GitHub API (like `baseRefName` or `headRefName`) can start with a hyphen (`-`). If passed to git commands (e.g., `git checkout <branch>`), git interprets them as options instead of positional arguments, leading to argument injection or command failure.
**Learning:** External data passed as shell command arguments, even indirectly via a wrapper like `gh` JSON output, can lead to injection if not explicitly validated or properly escaped (e.g., using `--`).
**Prevention:** Validate all branch and base names fetched from remote sources to ensure they do not start with a hyphen before passing them to git commands.
