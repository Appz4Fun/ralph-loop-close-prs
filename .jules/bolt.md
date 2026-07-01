## 2025-02-23 - Concurrency in _filter_to_still_open_prs
**Learning:** Checking PR statuses sequentially using subprocess calls to `gh pr view` in `_filter_to_still_open_prs` can be extremely slow (N+1 queries bottleneck). Using `concurrent.futures.ThreadPoolExecutor.map` significantly speeds up the process while maintaining order.
**Action:** Always check for batching or concurrency opportunities when fetching data from external APIs sequentially.
