## 2026-06-17 - Optimize PR state checks via concurrency
**Learning:** Sequential subprocess calls to GitHub CLI (`gh`) are a significant bottleneck when filtering PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform `gh pr view` checks in parallel, ensuring a guard clause (`if not items:`) prevents `ValueError` when `max_workers` could be 0, and maintaining order using `executor.map`.
