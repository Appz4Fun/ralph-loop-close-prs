## 2024-05-30 - Optimize PR state checks with concurrency
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs, sequential execution introduces severe N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with a guarded `max_workers` and `.map` to fetch PR states concurrently while preserving order and capturing exceptions gracefully.
