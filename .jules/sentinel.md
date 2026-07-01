## 2026-07-01 - Fix Git argument injection
**Vulnerability:** Git argument injection due to unvalidated branch and base names starting with a hyphen.
**Learning:** Git treats arguments starting with a hyphen as options or flags, potentially leading to command injection or unauthorized actions if an attacker can control branch or base names.
**Prevention:** Validate all git references to ensure they do not start with a hyphen before passing them to Git commands.
