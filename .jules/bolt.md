## 2026-06-12 - Concurrent gh PR View Checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs (N+1 problem), sequential execution adds substantial latency.
**Action:** Use concurrency (e.g., `concurrent.futures.ThreadPoolExecutor`) to parallelize independent `gh` CLI subprocess calls, being careful to preserve order using `executor.map` and gracefully capture/handle exceptions within the worker functions.
