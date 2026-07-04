## 2024-05-24 - Prevent Git Argument Injection
**Vulnerability:** Git branch names fetched from remote sources (or provided via CLI) could start with a hyphen (e.g., `-upload-pack`), leading to Git argument injection vulnerabilities when passed to subprocess calls.
**Learning:** External branch names must be validated before use in shell commands to prevent option injection.
**Prevention:** Validate that branch names do not start with a hyphen before using them in Git commands.
