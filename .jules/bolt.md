## 2024-05-30 - Parallelize PR state checks
**Learning:** Subprocess calls to the GitHub CLI ('gh') are a significant performance bottleneck. When checking states for multiple PRs, use concurrency to avoid N+1 sequential execution delays.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` to run independent `gh` CLI checks in parallel, preserving original order with `executor.map`, and handling exceptions safely. Add guard clauses to prevent `ValueError` when initializing executors with dynamic `max_workers` based on collection length.
