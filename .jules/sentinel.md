## 2026-07-03 - Git Argument Injection Risk
**Vulnerability:** Git commands like checkout, fetch, rebase, and reset take user-controlled branch or ref names. A branch name starting with a hyphen (e.g. "-b") can be injected as a malicious flag.
**Learning:** Git treats hyphens in refs as command arguments. These strings can be supplied from external sources, making them untrusted input.
**Prevention:** Always validate git refs to ensure they do not start with a hyphen before passing them into git subprocess calls.
