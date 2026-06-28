## 2024-06-28 - Concurrency in PR State Checking
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs sequentially, it leads to N+1 execution delays.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid sequential execution delays when making multiple CLI calls. Ensure original order is preserved using `executor.map` and add a guard against empty collections to prevent `ValueError: max_workers must be greater than 0`.
