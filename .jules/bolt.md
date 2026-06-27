## 2025-02-28 - Concurrent GH PR state checks
**Learning:** Subprocess calls to the GitHub CLI (`gh`) are a significant performance bottleneck when checked sequentially.
**Action:** When checking states for multiple PRs, use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential execution delays. Used `executor.map` to preserve original order and safely caught exceptions.
