## 2024-06-16 - Concurrent PR state checking
**Learning:** Subprocess calls to the GitHub CLI ('gh') for PR state checking create significant N+1 sequential execution delays when filtering large sets of PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to fetch state concurrently while preserving order and capturing exceptions gracefully.
