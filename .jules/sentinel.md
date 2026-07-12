## 2024-05-15 - Prevent Git Argument Injection
**Vulnerability:** Git argument injection due to unsanitized branch and base names passed to git commands in `ralph_loop/git_ops.py`. Branch names starting with a hyphen (e.g. `-h`) could be interpreted as options.
**Learning:** External inputs mapped to command-line parameters must always be validated to prevent accidental or malicious flag injection, even in internal automation tools.
**Prevention:** Validate that branch and base names do not start with a hyphen before passing them to git commands using the subprocess module.
