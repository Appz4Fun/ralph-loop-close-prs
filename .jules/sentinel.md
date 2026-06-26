## 2024-06-26 - Add Bandit nosec pragmas for safe subprocess execution
**Vulnerability:** Bandit reported several potential command injection risks (B603, B606) due to the use of `subprocess.Popen` and `os.execv` without shell escaping, but these were already using safe array formats (not `shell=True`).
**Learning:** Even when `subprocess.Popen` or `os.execv` is used safely (passing a list of arguments rather than a single string with `shell=True`), Bandit will still flag them as potential issues under B603 and B606.
**Prevention:** Always use argument arrays for `subprocess.Popen`, `subprocess.run`, and `os.execv`. Add inline `# nosec B603` or `# nosec B606` to silence Bandit when the arguments are explicitly known to be safe and `shell=True` is not used.
