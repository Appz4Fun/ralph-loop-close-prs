## 2024-06-29 - Bottleneck in PR State Checking
**Learning:** Checking PR state sequentially using `_pr_is_still_open` inside `_filter_to_still_open_prs` blocks the supervisor from spawning PR workers quickly, causing latency that scales with the number of PRs (N+1 bottleneck). Using `concurrent.futures.ThreadPoolExecutor` will avoid sequential execution delays.
**Action:** Use concurrent.futures.ThreadPoolExecutor.map when checking multiple PRs sequentially to prevent the N+1 problem.
