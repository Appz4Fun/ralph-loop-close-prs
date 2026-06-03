## 2026-06-03 - Concurrent PR state checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') to fetch PR state sequentially for multiple PRs cause a significant performance bottleneck (N+1 delay).
**Action:** Used `concurrent.futures.ThreadPoolExecutor` with `executor.map` to fetch PR states concurrently, improving execution time while preserving original order and gracefully handling command exceptions.
