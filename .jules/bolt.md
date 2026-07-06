## 2024-07-06 - [Concurrent PR Checks]
**Learning:** N+1 calls to the GitHub CLI (gh) within a loop are a significant performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` when performing multiple state checks (like `gh pr view`) to execute them concurrently, reducing total execution time. Ensure exceptions are yielded back to the main thread and logs are printed sequentially to avoid interleaving.
