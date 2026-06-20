## 2024-05-18 - Git Argument Injection Prevention
**Vulnerability:** Git commands executed via `subprocess` are vulnerable to argument injection if user-controlled branch or ref names start with a hyphen (e.g., `-b` or `--version`). This causes Git to interpret the branch name as a command-line option.
**Learning:** Even when using `subprocess` with `shell=False` and array arguments, values passed to the CLI that begin with a hyphen can alter the command's behavior and potentially lead to arbitrary command execution or application crashes.
**Prevention:** Always validate branch and ref names fetched from remote sources to ensure they do not start with a hyphen before passing them to git commands.
