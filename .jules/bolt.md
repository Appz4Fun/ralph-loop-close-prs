## 2024-06-06 - Concurrent PR State Checking
**Learning:** Checking PR states sequentially via `_pr_is_still_open` across multiple PRs using `gh` CLI spawns is a performance bottleneck (O(N) latency).
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform the checks in parallel, significantly reducing the fan-out latency while gracefully retaining order and capturing exceptions to preserve stability.
