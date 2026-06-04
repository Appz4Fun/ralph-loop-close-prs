## 2024-05-15 - Concurrent PR Status Checking
**Learning:** Subprocess calls to the GitHub CLI (e.g. `gh pr view`) can cause significant N+1 sequential execution delays. Use concurrency (like `concurrent.futures.ThreadPoolExecutor.map`) to avoid these bottlenecks while preserving order.
**Action:** Use `executor.map` and capture exceptions in a wrapper when executing multiple subprocess calls sequentially.
