## 2024-05-15 - Concurrent GitHub Check Polling
**Learning:** Subprocess calls to the GitHub CLI (`gh`) are a significant bottleneck when checking states for multiple PRs or handling fan-out lists. When checking PR statuses or checks one by one, the delay scales as O(N).
**Action:** Use `concurrent.futures.ThreadPoolExecutor` when polling or interacting with the GitHub API for multiple items simultaneously to preserve throughput and prevent N+1 delays.
