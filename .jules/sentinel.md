## 2025-05-15 - [Git Argument Injection via Branch Names]
**Vulnerability:** Branch names from external sources (like GitHub PRs) were passed directly to git commands without validation. If an attacker created a branch named like an argument (e.g., `-O`), it could be injected into the `git checkout` or `git fetch` command, potentially causing unexpected behavior or command execution.
**Learning:** External inputs that populate command arguments, even indirectly via API responses like branch names, can lead to argument injection if they start with a hyphen.
**Prevention:** Validate that branch names or base names fetched from remote sources do not start with a hyphen before passing them to git commands.
