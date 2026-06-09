## 2024-06-09 - Concurrent PR Status Checking
**Learning:** Checking PR statuses sequentially via subprocess calls to the GitHub CLI ('gh') creates a significant N+1 execution delay bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` and an exception-catching wrapper to check multiple PR statuses concurrently while preserving order, ensuring to include an `if not items: return []` guard to avoid `ValueError` on empty collections.
