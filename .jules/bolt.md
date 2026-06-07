## 2024-05-18 - Concurrent PR state checks
**Learning:** Checking states sequentially for multiple PRs (e.g., using `gh pr view` for each PR via `_pr_is_still_open`) is a significant performance bottleneck due to the N+1 problem with the `gh` CLI subprocess calls.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` mapped over PR IDs to run `_pr_is_still_open` concurrently. Catch exceptions inside the mapped function to preserve existing logic gracefully.
