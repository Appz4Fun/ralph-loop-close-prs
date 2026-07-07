## 2024-07-07 - Command line injection vulnerability
**Vulnerability:** The `git checkout` command uses string formatting for a branch name that might be provided by a user without validation against hyphen prefixes.
**Learning:** Branch names starting with `-` can be interpreted as flags by `git`.
**Prevention:** Use early input validation to reject invalid branch names.
