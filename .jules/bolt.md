## 2024-03-24 - Parallelize GitHub PR Status Checks
**Learning:** Checking the status of open PRs sequentially using `gh pr view` introduces significant network latency and becomes a major performance bottleneck for a large number of PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to fetch the status of multiple PRs concurrently while preserving the result order.
