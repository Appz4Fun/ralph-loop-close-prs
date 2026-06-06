## 2026-06-06 - Concurrent GitHub CLI Subprocess Calls
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs sequentially, it creates severe N+1 execution delays.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) and capture exceptions in a helper wrapper so they can be yielded and handled gracefully in order to avoid N+1 delays.
