## 2024-03-24 - Parallelize PR status checks during fan-out
**Learning:** Sequential calls to `_pr_is_still_open` via the GitHub CLI ('gh') introduce an N+1 execution delay during fan-out initialization (`_filter_to_still_open_prs`). When checking the status of multiple PRs, this results in significant performance bottlenecks.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to execute targeted `gh pr view` queries in parallel, wrapping calls to capture exceptions (like `CommandError`) in order to gracefully yield results or transient failures in sequence.
