## 2026-06-25 - Improve performance of GitHub CLI loops
**Learning:** Checking the states for multiple PRs via separate `gh pr view` processes caused significant performance bottleneck (N+1 queries pattern) due to sequential subprocess execution.
**Action:** Used `concurrent.futures.ThreadPoolExecutor` to speed up fetching `gh pr view` concurrently in `_filter_to_still_open_prs`. Ensure that `executor.map` is used to preserve the original PR list order, and wrap subprocess calls in a try-except to yield exceptions back to the main thread.
