## 2024-10-26 - Fix Git argument injection via branch names
**Vulnerability:** Git argument injection vulnerability where remote branch names starting with a hyphen (e.g., `-b`) could be passed to `git` commands and interpreted as flags instead of positional arguments.
**Learning:** All branch and base names fetched from remote sources must be validated to ensure they do not start with a hyphen before being passed to `git` commands to prevent arbitrary flag injection.
**Prevention:** Explicitly check if branch names start with a hyphen (`-`) and reject them if they do, immediately throwing a `CommandError`.
