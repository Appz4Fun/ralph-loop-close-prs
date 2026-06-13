## 2024-05-30 - Fix Git argument injection in branch names
**Vulnerability:** Git commands executed via `subprocess.run` are vulnerable to argument injection if user-provided input (like branch names) starts with a hyphen (e.g., `-o`). Even with `shell=False`, `git` parses strings starting with `-` as command-line options.
**Learning:** Even safe subprocess usage (`shell=False`) does not protect against tools that interpret positional arguments as options if they start with hyphens.
**Prevention:** Explicitly validate that all inputs passed as branch names, refs, or other arguments do not start with a hyphen before passing them to CLI tools.
