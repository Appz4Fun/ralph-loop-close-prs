## 2024-07-10 - Concurrent Subprocess GitHub CLI Calls
**Learning:** Checking states sequentially for multiple PRs using subprocess calls to the GitHub CLI ('gh') is a significant performance bottleneck due to the high latency per call.
**Action:** Use concurrent.futures.ThreadPoolExecutor to parallelize independent 'gh' CLI reads. Always capture exceptions in worker threads to prevent crashes, process the responses sequentially in the main thread to avoid interleaved logs, and include a guard clause to handle empty iterables to avoid ValueError when max_workers is dynamically calculated.
