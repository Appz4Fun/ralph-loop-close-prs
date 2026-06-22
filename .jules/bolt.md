## 2026-06-22 - [Refactor `_filter_to_still_open_prs` to avoid N+1 GitHub CLI calls]
**Learning:** Checking GitHub CLI state for multiple PRs iteratively introduces significant latency (N+1 queries).
**Action:** Use concurrent operations, such as `concurrent.futures.ThreadPoolExecutor`, to fetch independent data sources quickly, while avoiding any state mutations within the threads to keep side-effects predictable. Add a guard clause when the input list is empty to prevent an exception with `max_workers=0`.
