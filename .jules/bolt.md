## 2024-05-24 - Parallelize PR State Verification
**Learning:** Subprocess calls to the GitHub CLI ('gh') sequentially in an N+1 manner cause significant performance bottlenecks when checking the state of multiple PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to check PR states concurrently, while preserving the original check order using `executor.map`.
