## 2024-06-30 - Optimize PR state checks
**Learning:** Checking PR states sequentially via `gh pr view` subprocess calls creates a significant N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to perform state checks concurrently while preserving original ordering and gracefully handling `CommandError` exceptions.
