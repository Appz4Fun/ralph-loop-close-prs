## 2024-05-24 - Git Argument Injection in Branch Names
**Vulnerability:** Git branch names fetched from GitHub API were passed directly to git commands without validation. If a branch started with a hyphen, it could inject arguments.
**Learning:** Always validate branch names and base references fetched from remote sources to prevent them from being interpreted as options by git commands.
**Prevention:** Reject branch names starting with a hyphen early in the PR metadata validation stage.