## 2024-05-14 - Optimize `_filter_to_still_open_prs` N+1 gh calls
**Learning:** `_filter_to_still_open_prs` uses a sequential loop to check PR statuses. `_pr_is_still_open` triggers a `gh` subprocess command. Doing this sequentially for a large list of PRs incurs N+1 sequential overhead, which can be mitigated with concurrency.
**Action:** Use `concurrent.futures.ThreadPoolExecutor.map` to parallelize independent network/subprocess calls while preserving original order and handling exceptions individually.
