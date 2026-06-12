## 2024-06-12 - Concurrent PR Checks
**Learning:** Checking PR state sequentially using `_pr_is_still_open` with external network calls (GitHub CLI) caused significant N+1 delays for large numbers of open PRs.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform network-bound state checks concurrently while preserving order, which substantially reduces overall PR processing time.