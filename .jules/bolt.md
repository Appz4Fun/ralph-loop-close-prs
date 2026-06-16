## 2024-06-16 - Bolt Performance Opportunity

**Learning:** `gh pr view` subprocess calls executed sequentially in `_filter_to_still_open_prs` and the main respawn loop in `cli.py` cause severe execution delays when iterating over multiple PRs. Specifically, each PR takes around 1-3 seconds to query state, leading to O(N) waiting time.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to perform `gh pr view` checks in parallel, preserving original PR order while drastically lowering total duration of the wait phase.
