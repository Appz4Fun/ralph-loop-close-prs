## 2024-07-04 - Concurrent GitHub CLI Calls
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a performance bottleneck. When checking states for multiple PRs, synchronous iteration causes N+1 delays.
**Action:** Use concurrency (e.g., `ThreadPoolExecutor`) to execute multiple independent CLI calls simultaneously to avoid N+1 delays. Use `executor.map` to preserve order and capture exceptions in a helper wrapper, then handle logging sequentially in the main thread.
