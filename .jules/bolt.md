## 2024-07-10 - Concurrent PR state checking
**Learning:** Checking states sequentially for multiple PRs (`_filter_to_still_open_prs`) via GitHub CLI subprocesses (`_pr_is_still_open`) is an N+1 bottleneck. Using `concurrent.futures.ThreadPoolExecutor` significantly reduces this delay.
**Action:** Use `ThreadPoolExecutor` for concurrent `gh` operations when operating on a list of PRs. Remember to add a guard clause for empty lists and handle exceptions within helper functions to preserve state and logs in the main thread.
