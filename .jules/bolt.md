## 2024-05-24 - Optimize PR open state checks with concurrency
**Learning:** Sequential subprocess calls to the GitHub CLI ('gh') via `_pr_is_still_open` are a significant performance bottleneck when processing multiple PRs, causing an N+1 scaling issue.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` to perform these network/CLI checks concurrently. Remember to handle empty lists to avoid `max_workers=0` and capture exceptions inside a helper function to yield them gracefully in the original order.
