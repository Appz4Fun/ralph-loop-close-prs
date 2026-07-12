## 2024-07-12 - Concurrent PR open check filtering
**Learning:** `_filter_to_still_open_prs` checks PR states sequentially, leading to an N+1 performance bottleneck when handling many PRs in fan-out mode because `_pr_is_still_open` triggers a slow subprocess call (`gh pr view`).
**Action:** Use `concurrent.futures.ThreadPoolExecutor` combined with `executor.map` to fetch PR states concurrently while preserving order and catching exceptions without interleaving main thread logs.
