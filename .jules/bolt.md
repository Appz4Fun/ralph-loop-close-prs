## 2025-01-30 - GitHub CLI Concurrent PR Fetching
**Learning:** Subprocess calls to the GitHub CLI ('gh') sequentially (N+1) cause significant performance bottlenecks when checking states for multiple PRs.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) and map the original order while catching `CommandError` in a helper function to avoid N+1 sequential delays.
