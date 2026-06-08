## 2026-06-08 - Concurrent PR state checks
**Learning:** Sequential subprocess calls to the GitHub CLI (like `gh pr view`) for multiple items cause significant N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to execute independent CLI checks concurrently while preserving original order and handling exceptions gracefully.
