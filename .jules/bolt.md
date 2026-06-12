## 2024-06-12 - Parallelize PR state checking in _filter_to_still_open_prs
**Learning:** Subprocess calls to the GitHub CLI ('gh') via '_pr_is_still_open' are a significant performance bottleneck when checked sequentially. When checking states for multiple PRs, use concurrency to avoid N+1 sequential execution delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` and capture exceptions to parallelize independent `gh` CLI checks while preserving order and handling transient errors gracefully.
