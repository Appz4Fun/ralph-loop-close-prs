## 2026-06-12 - Prevent Git Argument Injection
**Vulnerability:** Git argument injection risk where PR branch names starting with hyphens could be evaluated as command line flags when passed to `git` commands.
**Learning:** External or remote references like GitHub branch names should never be passed unvalidated to shell commands, as attackers can craft branch names (e.g., `-q`, `--exec`) to alter command behavior.
**Prevention:** Always validate branch and base names fetched from remote sources to ensure they do not start with a hyphen before passing them to subprocesses.
