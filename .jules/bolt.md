## 2024-05-24 - Concurrent PR state checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs, N+1 sequential execution delays are significant.
**Action:** When checking states for multiple PRs, use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential execution delays. Ensure that original order is preserved and exceptions are captured so they can be handled gracefully in order.
