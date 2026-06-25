## 2024-06-25 - Concurrent PR Filtering
**Learning:** Sequential calls to `_pr_is_still_open` using `gh pr view` inside `_filter_to_still_open_prs` create an N+1 performance bottleneck when checking multiple PRs.
**Action:** Used `concurrent.futures.ThreadPoolExecutor` to check the status of multiple PRs in parallel, keeping execution time bounded and improving overall startup time.
