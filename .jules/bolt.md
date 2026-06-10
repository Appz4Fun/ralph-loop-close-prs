## 2024-05-24 - Optimizing GitHub API calls in fan-out loop
**Learning:** Subprocess calls to the GitHub CLI ('gh') via `_pr_is_still_open` sequentially checking PR states introduce an N+1 execution delay, acting as a significant performance bottleneck in the fan-out supervisor.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform state checks concurrently. Use `executor.map` to preserve order and a helper function to correctly handle `CommandError` exceptions inside the threads.
