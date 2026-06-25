## 2024-05-24 - Concurrent PR check execution
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs sequentially (e.g., using a loop over `gh pr view`), the delays add up and block execution.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform these operations concurrently, preserving the original order via `executor.map`, and capturing exceptions safely to handle them gracefully in order.
