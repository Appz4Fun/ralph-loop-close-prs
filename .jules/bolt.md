## 2025-02-24 - Concurrency in subprocess-bound operations
**Learning:** Sequential calls to GitHub CLI (`gh`) for checking PR states (e.g., via `_pr_is_still_open`) create significant performance bottlenecks when processing multiple PRs. Sequential N+1 execution delays fan-out spawn.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to parallelize `gh` CLI checks when processing lists of PRs, utilizing `executor.map` to preserve original ordering and handling exceptions per-PR to fail gracefully.
