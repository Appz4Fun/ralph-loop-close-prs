## 2024-07-08 - Git Argument Injection Vulnerability
**Vulnerability:** Git command argument injection via unvalidated branch names
**Learning:** Branch names fetched from remote sources must be validated to ensure they do not start with a hyphen before being passed to `git` commands.
**Prevention:** Always check if dynamic strings passed to git commands start with `-` and throw an exception if they do.
