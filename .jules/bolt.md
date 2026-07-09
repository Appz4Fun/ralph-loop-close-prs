## 2023-10-27 - [Concurrent Open PR Checks]
**Learning:** Checking states for multiple PRs sequentially causes N+1 delays, as subprocess calls to the GitHub CLI are a performance bottleneck.
**Action:** Use concurrency (e.g., `ThreadPoolExecutor`) to evaluate PR states concurrently, capturing exceptions in a helper wrapper to be yielded back to the main thread.
