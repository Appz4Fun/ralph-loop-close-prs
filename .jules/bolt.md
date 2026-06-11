## 2026-06-11 - Optimize `_filter_to_still_open_prs` with concurrency
**Learning:** `gh pr view` subprocess calls are executed sequentially for every PR in `_filter_to_still_open_prs`, causing an N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform `gh pr view` concurrently while maintaining the original PR order and properly capturing and logging `CommandError` exceptions. Add an `if not pr_numbers: return []` check to avoid `max_workers` value error when the input array is empty.
