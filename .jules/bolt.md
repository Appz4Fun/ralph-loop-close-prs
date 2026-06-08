## 2024-06-08 - Parallelize GitHub PR state checking
**Learning:** Sequential subprocess calls to the GitHub CLI (`gh`) are a significant performance bottleneck, especially when filtering multiple PRs in fan-out operations.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to concurrently check PR states, preserving order and handling exceptions gracefully, avoiding N+1 sequential execution delays.
