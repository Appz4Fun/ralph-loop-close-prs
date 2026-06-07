## 2024-06-07 - Avoid N+1 Sequential Subprocess Calls
**Learning:** Subprocess calls to the GitHub CLI are a significant performance bottleneck. When checking states for multiple PRs, a sequential loop causes N+1 delays.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid N+1 sequential execution delays when calling external CLIs across a list of items. Capture exceptions in a helper wrapper so they can be handled gracefully in order.
