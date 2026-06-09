## 2026-06-09 - Sentinel: [CRITICAL] Prevent Git Argument Injection
**Vulnerability:** Git branch, head, and base names passed to git commands without checking if they start with a hyphen.
**Learning:** This allows argument injection by maliciously crafted remote branch names.
**Prevention:** Validate that any remote reference passed to git commands does not start with a hyphen.
