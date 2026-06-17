## 2024-05-24 - Initial Bolt Journal

## 2024-05-24 - Concurrent PR Filtering
**Learning:** Subprocess calls to the GitHub CLI are a significant performance bottleneck. When checking states for multiple PRs, N+1 sequential execution delays can be avoided by using concurrency.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to preserve order while capturing exceptions in a helper wrapper.
