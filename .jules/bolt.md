## 2024-05-24 - Concurrent PR state checks
**Learning:** Checking states sequentially for multiple PRs causes N+1 delays. Subprocess calls to the GitHub CLI are a bottleneck. Using concurrency (ThreadPoolExecutor) drastically improves performance while preserving order.
**Action:** Use concurrent.futures.ThreadPoolExecutor for multiple independent I/O-bound subprocess checks.