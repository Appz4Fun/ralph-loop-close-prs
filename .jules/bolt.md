## 2026-06-06 - Optimize _filter_to_still_open_prs with Concurrency
**Learning:** Checking state for multiple PRs using sequential GitHub CLI calls (`gh pr view` invoked via subprocess) is a significant performance bottleneck in the supervisor logic due to N+1 delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor.map` with a helper function to evaluate PR states concurrently while preserving the original sequence and handling exceptions robustly.
