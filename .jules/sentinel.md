## 2026-06-17 - Prevent Git argument injection vulnerabilities
**Vulnerability:** Git branch names fetched from remote sources might start with a hyphen (e.g., `-foo`). Passing these unvalidated names directly into commands like `git checkout` or `git fetch` can lead to Git argument injection, allowing attackers to manipulate Git arguments.
**Learning:** External branch names are not guaranteed to be safe and can introduce command injection risks even when using parameterized subprocess commands without shell execution.
**Prevention:** Always validate branch and base names fetched from remote sources to ensure they do not start with a hyphen before being passed to `git` commands.
