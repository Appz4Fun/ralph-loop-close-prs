## 2024-05-24 - Subprocess calls N+1 Performance Optimization
**Learning:** Subprocess calls to the GitHub CLI ('gh') sequentially can be a significant performance bottleneck (N+1 query problem).
**Action:** When checking states for multiple PRs, use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to avoid sequential execution delays while maintaining original order with `executor.map`.
