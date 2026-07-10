## $(date +%Y-%m-%d) - Prevent Git Argument Injection
**Vulnerability:** Untrusted branch and base names could start with a hyphen, causing `git` to interpret them as command-line flags.
**Learning:** Dynamic arguments passed directly to shell or subprocess commands like `git checkout` or `git fetch` can lead to argument injection if they begin with a hyphen.
**Prevention:** Explicitly validate all external inputs acting as git references to ensure they do not start with `-` before passing them to subprocess commands.
