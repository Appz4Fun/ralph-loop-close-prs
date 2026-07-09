## 2024-07-09 - Parallelize Stale PR Filtering
**Learning:** Checking PR statuses sequentially in `_filter_to_still_open_prs` acts as a severe N+1 bottleneck when a high volume of PRs is managed, primarily because each `_pr_is_still_open` check executes a synchronous subprocess call to `gh`.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to map status checks asynchronously when dealing with arrays of network-bound subprocess tasks, wrapping exceptions to evaluate and log them sequentially in the main thread to preserve stdout formatting without race conditions.
