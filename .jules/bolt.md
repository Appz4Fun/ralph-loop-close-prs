## 2024-07-05 - Concurrent Subprocess Calls Bottleneck
**Learning:** Checking states for multiple PRs via sequential subprocess calls to the GitHub CLI ('gh') creates a significant N+1 performance bottleneck.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) for bulk subprocess calls to avoid delays. Use `executor.map` to preserve order, capture exceptions (like `CommandError`) in a helper wrapper to be yielded back to the main thread, and handle all logging sequentially in the main thread to prevent interleaved logs.
