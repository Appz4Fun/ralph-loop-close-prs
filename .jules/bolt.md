## 2024-05-18 - [Parallelize PR state checks]
**Learning:** Subprocess calls to the GitHub CLI ('gh') for PR state checks are a significant performance bottleneck. When checking states for multiple PRs, they execute sequentially causing N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to check PR states concurrently, capturing exceptions to maintain order and graceful error handling. Ensure a guard clause `if not pr_numbers: return []` is used to prevent `ValueError` for 0 workers.
