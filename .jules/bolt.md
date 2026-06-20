## 2024-06-20 - Concurrent execution for checking PRs
**Learning:** Checking states for multiple PRs sequentially causes N+1 sequential execution delays. Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to execute GitHub CLI calls concurrently and handle exceptions gracefully.
