## 2024-07-11 - Optimize _filter_to_still_open_prs
**Learning:** Sequential GitHub CLI subprocess calls (`gh pr view`) to check states for multiple PRs are a performance bottleneck (N+1 delays).
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to check PRs concurrently. Use `executor.map` to preserve order, and capture exceptions to be handled sequentially in the main thread to prevent interleaved logs.
