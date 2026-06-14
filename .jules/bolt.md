## 2025-02-19 - Concurrent PR state checks
**Learning:** Sequential calls to the `gh` CLI (e.g. `gh pr view`) for multiple PRs cause a significant N+1 performance bottleneck.
**Action:** Use `concurrent.futures.ThreadPoolExecutor` with `executor.map` and a helper wrapper to execute independent CLI checks concurrently while preserving result order and handling exceptions properly. Always include a guard clause for empty lists to prevent `max_workers=0` `ValueError`s.
